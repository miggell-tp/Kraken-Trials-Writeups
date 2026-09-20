# Beneath the Surface

**Category:** Forensics\
**Points:** 1000

> The Kraken is known for hiding its treasures beneath the surface.
>
> An old image was recovered from the depths, but something about it
> feels off.
>
> Can you uncover what the Kraken left behind?

**Flag format:** `MLUC{...}`

## 1. Challenge Overview

We are given an image named `kraken.jpg`.

At first glance, it appears to be an ordinary underwater image of the
Kraken. However, the challenge description hints that something is
hidden **beneath the surface**.

The goal is to inspect the image's metadata and file structure, recover
the hidden treasure, identify the encoding used for the final message,
and decode it to obtain the flag.

------------------------------------------------------------------------

## 2. What to Look At

Since this is a **forensics** challenge, we should start by examining
the file itself instead of only looking at the image visually.

Useful things to check:

-   File type
-   Metadata
-   Comments
-   Strings
-   Additional data appended to the image
-   Embedded or hidden files

The intended beginner-friendly workflow is:

``` text
file → exiftool → binwalk → unzip → dCode → CyberChef
```

We can also use **Aperi'Solve** as an alternative automated analysis
tool to verify our findings.

------------------------------------------------------------------------

## 3. Intended Solution

### Step 1: Identify the file

First, check what type of file we are dealing with:

``` bash
file kraken.jpg
```

<img width="854" height="62" alt="Screenshot 2026-09-20 094219" src="https://github.com/user-attachments/assets/3cde85b1-2a95-4c0b-ad3e-e915488b6dfa" />

The result identifies it as a JPEG image.

Since we know it is a JPEG, the next logical step is to inspect its
metadata.

------------------------------------------------------------------------

### Step 2: Inspect the metadata with ExifTool

Run:

``` bash
exiftool kraken.jpg
```

Look through the output for unusual metadata.

We find a comment containing:

``` text
The password to the treasure is: deepsea
```

<img width="578" height="429" alt="Screenshot 2026-09-20 093906" src="https://github.com/user-attachments/assets/d8b05347-7c1f-4bd1-9240-dcfce59bb017" />

This gives us our first important clue.

### Password

``` text
deepsea
```

The challenge description mentions that the Kraken's treasure is hidden
beneath the surface, and the metadata gives us a password that will
likely be useful for the next layer.

------------------------------------------------------------------------

### Step 3: Look for hidden files with Binwalk

Next, check whether additional files are embedded or appended to the
image:

``` bash
binwalk kraken.jpg
```

<img width="855" height="137" alt="Screenshot 2026-09-20 094626" src="https://github.com/user-attachments/assets/29ccbdcf-fb28-464b-abf4-681174304ee9" />

Binwalk reveals that additional data exists inside the image, including
a ZIP archive.

------------------------------------------------------------------------

### Step 4: Extract the hidden archive

We can use Binwalk to extract the discovered files:

``` bash
binwalk -e kraken.jpg
```

After extraction and going to the extracted folder, we find a zip file:

The zip file is password protected.

We already discovered the password using ExifTool:

``` text
deepsea
```

If needed, the archive can be extracted manually with:

``` bash
unzip -P deepsea <extracted_zip>
```

<img width="668" height="47" alt="Screenshot 2026-09-20 095013" src="https://github.com/user-attachments/assets/60f80114-e75e-4fcd-95af-0fca7f72d580" />

------------------------------------------------------------------------

## 4. Read the Hidden Treasure

Open:

``` text
treasure/treasure.txt
```

The file contains:

``` text
The Kraken keeps its treasure deep beneath the surface.

You found the first layer.

But the treasure is not written plainly.

Look deeper.

4d4c55437b7468655f61627973735f72656d656d626572737d
```

<img width="783" height="206" alt="Screenshot 2026-09-20 095406" src="https://github.com/user-attachments/assets/c2a3bac4-9799-4951-bdff-70f430c647c1" />

The last line does not look like normal text.

However, it only contains hexadecimal characters:

``` text
0-9
a-f
```

This suggests that the message may be encoded in hexadecimal.

Instead of immediately assuming the encoding, we can use **dCode's
Cipher Identifier** to check what kind of encoding/cipher we are dealing
with.

<img width="1457" height="630" alt="image" src="https://github.com/user-attachments/assets/5383955f-186c-441e-8768-83ab3466722c" />

------------------------------------------------------------------------

## 5. Identify the Encoding with dCode

Open the **dCode Cipher Identifier**:

https://www.dcode.fr/cipher-identifier

Paste the following into the identifier:

``` text
4d4c55437b7468655f61627973735f72656d656d626572737d
```

dCode recognizes the structure as **ASCII Code**.

This means that ASCII text is represented using hexadecimal encoding.

dCode's Cipher Identifier is designed to recognize possible encryption
or encoding methods and can direct you toward the appropriate decoding
tool.

------------------------------------------------------------------------

## 6. Decode the Hexadecimal with CyberChef

Now that we have identified the encoding, we can use **CyberChef** for
the actual decoding.

Open:

https://gchq.github.io/CyberChef/

Search for the operation:

``` text
From Hex
```

Paste:

``` text
4d4c55437b7468655f61627973735f72656d656d626572737d
```

CyberChef produces:

``` text
MLUC{the_abyss_remembers}
```

<img width="1280" height="607" alt="image" src="https://github.com/user-attachments/assets/d8a46493-c469-4c65-b9b7-26dfb93557ed" />

Or we can also click the ASCII Code that dcode.fr identified and paste the string there.

<img width="727" height="469" alt="image" src="https://github.com/user-attachments/assets/d9c42b62-4e3f-4479-ba87-0b6f3ca78517" />

------------------------------------------------------------------------

## 7. Final Flag

``` text
MLUC{the_abyss_remembers}
```

------------------------------------------------------------------------

# 8. Alternative Method: Aperi'Solve

The same challenge can also be investigated using **Aperi'Solve**, an
online image analysis platform.

Open:

https://www.aperisolve.com/

Upload:

``` text
kraken.jpg
```

<img width="2559" height="1253" alt="image" src="https://github.com/user-attachments/assets/557f1ca6-9b5f-496c-880e-948571c1af7d" />

Aperi'Solve automatically runs several common image and steganography
analysis tools, including metadata and embedded-file checks.

### Check the ExifTool results

In the ExifTool output, look for:

``` text
The password to the treasure is: deepsea
```

So we have:

``` text
Password = deepsea
```

<img width="755" height="411" alt="image" src="https://github.com/user-attachments/assets/3b477e82-8866-4602-a416-60f98b57d1ee" />

### Check the Binwalk results

The Binwalk results reveal the appended/embedded ZIP archive.

<img width="749" height="226" alt="image" src="https://github.com/user-attachments/assets/beb6039a-6b29-488d-b71e-913e7db65c08" />

Extract the archive and use:

``` text
deepsea
```

as the password.

This gives us:

``` text
treasure/treasure.txt
```

<img width="511" height="564" alt="image" src="https://github.com/user-attachments/assets/4fdd2ca5-b65e-4499-b4ff-8873ef18623f" />

The file contains the hexadecimal string:

``` text
4d4c55437b7468655f61627973735f72656d656d626572737d
```

We can then use the earlier steps to get the flag:

``` text
MLUC{the_abyss_remembers}
```

------------------------------------------------------------------------

# 9. Complete Attack Chain

``` text
kraken.jpg
    ↓
file
    ↓
Identify JPEG
    ↓
exiftool
    ↓
Find password: deepsea
    ↓
binwalk
    ↓
Find hidden ZIP archive
    ↓
Extract archive
    ↓
treasure/treasure.txt
    ↓
Find hexadecimal string
    ↓
dCode Cipher Identifier
    ↓
Identify Hexadecimal encoding
    ↓
CyberChef → From Hex
    ↓
MLUC{the_abyss_remembers}
```

## 10. Tools Used

  -----------------------------------------------------------------------
  Tool                                Purpose
  ----------------------------------- -----------------------------------
  `file`                              Identify the file type

  `exiftool`                          Inspect metadata and find the
                                      password

  `binwalk`                           Detect and extract the hidden ZIP
                                      archive

  `unzip`                             Extract the password-protected
                                      archive

  dCode Cipher Identifier             Identify the encoding used by the
                                      final string

  CyberChef / dcode                   Decode the hexadecimal data

  Aperi'Solve                         Alternative automated image
                                      analysis
  -----------------------------------------------------------------------

## 11. Beginner Takeaway

When you encounter a suspicious image in a forensics challenge, don't
immediately assume that the secret is hidden in the pixels.

Start with the file itself:

``` text
1. Identify the file
2. Check the metadata
3. Look for embedded or appended files
4. Extract anything suspicious
5. Inspect the extracted content
6. Identify unknown encodings
7. Decode the final message
```

For this challenge, the important progression is:

``` text
Metadata
   ↓
Password
   ↓
Hidden Archive
   ↓
Hidden Text
   ↓
Hexadecimal
   ↓
Flag
```

The Kraken's treasure was hidden in multiple layers, which is why the
clue **"Beneath the Surface"** is important: each step takes us deeper
into the file.
