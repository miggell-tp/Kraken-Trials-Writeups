# The Dragon Warrior

*Category:* Forensics  
*Points:* 500  
*Author:* mpm4wi  
*Description:* :>
*Attachments:* [professor-left-tab-open.zip](../materials/The-Dragon-Warrior.zip)


## 1. Challenge Overview

The challenge provides a ZIP file containing two files that appear to be images: `dragon-scroll-x.png` and `dragon-warrior-x.png`.

This challenge combines digital forensics and steganography, with a focus on careful observation. Examine both files to find and retrieve the hidden `flag.txt`.


## 2. What to Look At

- `dragon-warrior-x.png` is actually a JPEG file, despite its `.png` extension. Its unusually large size—26 MB—may indicate that it contains embedded or hidden files.
- `dragon-scroll-x.png` is a genuine PNG image with hidden text encoded in its color channels. The text becomes visible when you inspect the image’s color planes, and `zsteg` can also reveal a clue for it **`I move across different planes and see a wide spectrum of colors`**.

## 3. Approach

First, unzip the archive, obviously. Then do your usual forensic routine: check the metadata, file structure, clues, breadcrumbs, and so on.

You may notice that 26 MB seems too large for a 1980 × 1080 JPEG. That’s your starting point. Eventually, you’ll discover that the JPEG hides a WAV file, the _Kung Fu Panda_ theme song. Since Steghide can embed data in WAV files, you might try to brute-force the password. After many attempts with no luck, shift your investigation to the other image.

Once you’ve exhausted the usual forensic checks, try some steganography techniques. You’ll discover that the image contains low-contrast text that becomes visible when you inspect its color planes. That text might be the password for the WAV file you found earlier.

Use the password to open the WAV file, and you’ll get a ZIP file containing another archive called `the-last-scroll`. It’s password-protected, so put your forensic skills to work again and look for more clues or breadcrumbs. Aha! The generous author left a clue in a subfield marked `1337`, followed by trailing data in hexadecimal. Decode that data from Base64 to get the password.

Unlock the ZIP file, and aha, you’ve got the flag.

## 4. Solution

### Step 1: Extract the archive and inspect the files

Unzip the challenge archive. Check the files’ metadata, types, sizes, and structure for anything unusual.

<img width="1508" height="258" alt="image" src="https://github.com/user-attachments/assets/9b7f6a7a-03ad-4c9e-b67b-37eca14f708f" />

<img width="1330" height="818" alt="image" src="https://github.com/user-attachments/assets/99a0bc07-8e6e-47e5-b049-76f97e59d671" />

<img width="1548" height="128" alt="image" src="https://github.com/user-attachments/assets/5c03b316-7de0-461e-bd68-9b2ebd0eb126" />


<img width="963" height="204" alt="image" src="https://github.com/user-attachments/assets/e12bd4ec-dd13-4f60-b16b-b82a8760678a" />


<img width="1376" height="440" alt="image" src="https://github.com/user-attachments/assets/56bb4b59-e7d9-477a-a2ee-32cb9968203c" />


File signature is not for png

This makes `dragon-warrior-x.png` sus
### Step 2: Investigate the oversized JPEG

Notice that `dragon-warrior-x.png` is actually a JPEG and that its 26 MB size seems unusually large for a 1980 × 1080 image. Investigate it and recover the hidden WAV file.

There are several ways to carve the WAV file. You could try opening the file as raw data in audio editing software such as Audacity, or use a tool like Binwalk to look for embedded files. You could also write a Python script to extract it, or use a hex editor to copy the data after the JPEG end marker, `FF D9`. That last method can be tedious since you have to find the marker yourself and carefully select the remaining data.

This is my favorite Binwalk command. It’s a pretty aggressive way to carve out anything Binwalk recognizes inside the file:

```
binwalk --dd=".*" dragon-warrior-x.png
```

This is we what want 

<img width="2126" height="1208" alt="image" src="https://github.com/user-attachments/assets/a97805ad-7fd4-4051-addb-e92aa3287ad3" />


See how aggressive that command is? It carved out a bunch of unnecessary files too.
### Step 3: Check the WAV file for embedded data

Try your usual steganography checks on the WAV file. Mention that brute-forcing its Steghide passphrase did not work, which led you to inspect the other image.

Here is our wav file listening to it does nothing its just really the theme song of kungfu fighting yah! exciting something idk the lyrics

<img width="2070" height="1306" alt="image" src="https://github.com/user-attachments/assets/344918c3-eb3c-4f8b-8221-0a252eb1602d" />


<img width="1234" height="144" alt="image" src="https://github.com/user-attachments/assets/f56ff2df-6639-4afb-83d1-250e432fae92" />


You will also try stegseek the best version of steghide

<img width="1204" height="204" alt="image" src="https://github.com/user-attachments/assets/470c2b97-114a-40e1-a5ad-a1901444008c" />


It even went through the entire 133 MB RockYou wordlist also if your password is there you are cooked really cooked so change password now

Now we will shift to the other image `dragon-scroll-x.png`
### Step 4: Inspect the PNG’s color planes

Examine `dragon-scroll-x.png` through different color planes. Reveal the low-contrast text and recognize it as a possible passphrase.

Personally ill just use online tools for this steganography tools something like that for example this website 
https://www.boxentriq.com/steganography/invisible-ink-detector

<img width="531" height="698" alt="image" src="https://github.com/user-attachments/assets/825cc90d-6c96-4560-8b69-8d17206edf3c" />


Notice the text? It might be the password for the WAV file we carved out of the other image.

It may not be easy to read at first, so try inspecting different color planes. You could write a script to cycle through them, or just keep clicking the **Randomize Colors** button. That’s way easier, and eventually you’ll spot the password: `p455#w0rdxd`.
### Step 5: Use the passphrase to extract the archive

Use the recovered text as the Steghide passphrase for the WAV file. Extract the ZIP archive and note that it contains a password-protected archive called `the-last-scroll`.

<img width="990" height="88" alt="image" src="https://github.com/user-attachments/assets/1b0ffcf8-e968-4a6f-9651-366d2681395d" />


Charan! But wait, there’s more. The author really isn’t that generous after all.

<img width="1536" height="150" alt="image" src="https://github.com/user-attachments/assets/e09d766c-09f3-4a8a-8d11-19257a6a5cc6" />


You can’t unzip it! It says “Unsupported compression method 99.” What a bum.

<img width="602" height="362" alt="image" src="https://github.com/user-attachments/assets/eab238a9-e27f-4d58-b856-bed8425ec58d" />


And now its asking for password
### Step 6: Recover the archive password

Inspect the archive for clues. Find the subfield marked `1377` and its trailing hexadecimal data. Convert the data to bytes, then decode it from Base64 to reveal the password.

Inspecting the `last-scroll.zip` 

```
zipinfo -v last-scroll.zip
```

<img width="1652" height="382" alt="image" src="https://github.com/user-attachments/assets/a7b92457-e4e2-4dab-8f23-1328eb9709fa" />


iIt reveals a subfield with ID `0x1337`, followed by 24 bytes of trailing data:

```
55 00 32 00 74 00 68 00 5a 00 44 00 41 00 77 00 63 00 32 00 67 00 3d 00
```

The data is in hexadecimal, so let’s use CyberChef to decode it. Apply **From Hex**, then decode the result as **UTF-16LE**. That gives us a Base64 string:

```
U2thZDAwc2g=
```

Decode that from Base64, and we get:

```
Skad00sh
```


### Step 7: Retrieve the flag

Use the recovered password to unlock `the-last-scroll` and retrieve `flag.txt`.

<img width="616" height="406" alt="image" src="https://github.com/user-attachments/assets/b1b65217-acd2-469c-9472-d039cf247b88" />


Or using terminal with 7z to make it cooler gui is lame

<img width="1406" height="790" alt="image" src="https://github.com/user-attachments/assets/0ebfbd5c-3611-40ea-a1bc-7c595fd0436e" />

Wolah! you get the flag!
`MLUC{Y0u_4r3_7h3_dr4g0n_w4rr10r_098f6bcd4621d373c4d343832627b4f6}`
