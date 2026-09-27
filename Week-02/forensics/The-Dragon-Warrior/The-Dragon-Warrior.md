# Professor Left His Tab Open

*Category:* Forensics  
*Points:* 500  
*Author:* mpm4wi  
*Description:* :>
*Attachments:* [Download the evidence ZIP from the challenge link](http://161.118.223.219:5006/downloads/professor-left-tab-open.zip)


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

![[Pasted image 20260927233135.png]]

![[Pasted image 20260927233209.png]]

![[Pasted image 20260927233254.png]]

![[Pasted image 20260927233459.png]]

![[Pasted image 20260927233530.png]]

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

![[Pasted image 20260927234232.png]]

See how aggressive that command is? It carved out a bunch of unnecessary files too.
### Step 3: Check the WAV file for embedded data

Try your usual steganography checks on the WAV file. Mention that brute-forcing its Steghide passphrase did not work, which led you to inspect the other image.

Here is our wav file listening to it does nothing its just really the theme song of kungfu fighting yah! exciting something idk the lyrics

![[Pasted image 20260927234431.png]]


![[Pasted image 20260927234634.png]]

You will also try stegseek the best version of steghide

![[Pasted image 20260927234708.png]]

It even went through the entire 133 MB RockYou wordlist also if your password is there you are cooked really cooked so change password now

Now we will shift to the other image `dragon-scroll-x.png`
### Step 4: Inspect the PNG’s color planes

Examine `dragon-scroll-x.png` through different color planes. Reveal the low-contrast text and recognize it as a possible passphrase.

Personally ill just use online tools for this steganography tools something like that for example this website 
https://www.boxentriq.com/steganography/invisible-ink-detector

![[Pasted image 20260927235127.png]]

Notice the text? It might be the password for the WAV file we carved out of the other image.

It may not be easy to read at first, so try inspecting different color planes. You could write a script to cycle through them, or just keep clicking the **Randomize Colors** button. That’s way easier, and eventually you’ll spot the password: `p455#w0rdxd`.
### Step 5: Use the passphrase to extract the archive

Use the recovered text as the Steghide passphrase for the WAV file. Extract the ZIP archive and note that it contains a password-protected archive called `the-last-scroll`.

![[Pasted image 20260928000358.png]]

Charan! But wait, there’s more. The author really isn’t that generous after all.

![[Pasted image 20260928000439.png]]

You can’t unzip it! It says “Unsupported compression method 99.” What a bum.

![[Pasted image 20260928000607.png]]

And now its asking for password
### Step 6: Recover the archive password

Inspect the archive for clues. Find the subfield marked `1377` and its trailing hexadecimal data. Convert the data to bytes, then decode it from Base64 to reveal the password.

Inspecting the `last-scroll.zip` 

```
zipinfo -v last-scroll.zip
```

![[Pasted image 20260928000810.png]]

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

![[Pasted image 20260928001202.png]]

Or using terminal with 7z to make it cooler gui is lame

![[Pasted image 20260928001302.png]]

`MLUC{Y0u_4r3_7h3_dr4g0n_w4rr10r_098f6bcd4621d373c4d343832627b4f6}`
