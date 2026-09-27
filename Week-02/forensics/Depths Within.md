# Depths Within

*Category:* Steganography  
*Attachments:* `kr4k3n_hidden.jpg`

## 1. Challenge Overview

We are given an ordinary-looking JPEG image of a Kraken.

The description tells us that there is more hidden beneath the surface, so instead of only looking at the image, we need to inspect the file itself and figure out if it contains something else.

## 2. What to Look At

- The image looks normal when opened.
- The description repeatedly tells us to look deeper and inspect the file.
- The file is named `kr4k3n_hidden.jpg`.
- The `.jpg` extension may not necessarily tell us what the file actually contains.

*Key clue:* `What appears to be an ordinary file may contain more than meets the eye.`

## 3. Approach

I first opened the image normally, but there was nothing obvious to find.

Since the challenge tells us to **inspect what we are given**, I started looking at the file itself.

The `.jpg` extension caught my attention. If the file contains something other than an image, changing its extension could reveal what is actually inside.

After trying `.zip`, the file could be extracted successfully. This revealed another file with a `.jpg` extension, so I followed the same idea again.

## 4. Solution

### Step 1: Try Changing the File Extension

The original file is:

```text
kr4k3n_hidden.jpg
````

Rename it to:

```text
kr4k3n_hidden.zip
```

Then extract the ZIP file.

<img width="1284" height="910" alt="image" src="https://github.com/user-attachments/assets/8ad638ed-7c3c-485b-9f97-a5426270c4fe" />
<img width="1288" height="909" alt="image" src="https://github.com/user-attachments/assets/1cd068d6-8fd1-483d-b368-e01d3ac002ef" />

The extracted files are:

```text
part1.txt
part2.jpg
```

### Step 2: Read part1.txt

Open `part1.txt`.

It contains:

```text
MLUC{D0N7_7RU57_
```

<img width="1090" height="801" alt="image" src="https://github.com/user-attachments/assets/8f39fbd7-7829-4414-b91b-22dbc05fc876" />

This looks like the beginning of a flag, but it is incomplete.

There is still another file to investigate:

```text
part2.jpg
```

### Step 3: Inspect part2.jpg

Since the original `.jpg` file turned out to actually be a ZIP archive, we can try the same thing with `part2.jpg`.

Rename:

```text
part2.jpg
```

to:

```text
part2.zip
```

Then extract it.

<img width="1285" height="912" alt="image" src="https://github.com/user-attachments/assets/cd84e53f-dee4-42af-b842-6e04c8882fdd" />

This gives us:

```text
final.txt
```

### Step 4: Read final.txt

Open `final.txt`.

It contains:

```text
7H3_F1L3_3X73N51ON}
```

<img width="1095" height="802" alt="image" src="https://github.com/user-attachments/assets/7afddc5f-9870-471f-b79b-dc1a28c06da0" />

Now we have both parts of the flag:

```text
MLUC{D0N7_7RU57_
7H3_F1L3_3X73N51ON}
```

Combining them gives:

```text
MLUC{D0N7_7RU57_7H3_F1L3_3X73N51ON}
```

## 5. Flag

```text
MLUC{D0N7_7RU57_7H3_F1L3_3X73N51ON}
```

## 6. Key Takeaway

Don't always trust the file extension.

In this challenge, both `.jpg` files were actually ZIP archives containing another layer of the flag.

The solution was:

```text
kr4k3n_hidden.jpg
        ↓
   rename to .zip
        ↓
part1.txt + part2.jpg
                    ↓
             rename to .zip
                    ↓
                final.txt
                    ↓
                 FLAG
```

**Only 4 screenshots are needed**, marked directly in the writeup as `<!-- SCREENSHOT X: ... -->`.
```
