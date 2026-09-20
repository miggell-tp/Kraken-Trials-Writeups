# Chris Brown

*Category:* Cryptography

*Points:* 100

## 1. Challenge Overview

We are given a ZIP file named `chrisbrown.zip`.

The clue says:

> Ate at mcdonalds and picked this up

After extracting the ZIP file, we are given two files:

```text
hashbrown.png
flag.zip
````

The goal is to figure out the password for `flag.zip` and extract the flag.

## 2. What to Look At

Start by extracting the provided ZIP file.

Inside, we find:

* `hashbrown.png`
* A password-protected `flag.zip`

Opening `hashbrown.png` reveals an image containing the text:

```text
hashbrown
the pass
```

This is the important clue.

*Key clue:* `hashbrown`

## 3. Approach

I first extracted `chrisbrown.zip` and checked the files inside.

The image `hashbrown.png` tells us that **hashbrown** is the password clue.

Since the challenge is categorized as cryptography and specifically tells us about a password, we should try hashing `hashbrown`.

The most common hash to check for a beginner crypto challenge like this is **MD5**.

We can calculate the MD5 hash of:

```text
hashbrown
```

The resulting MD5 hash can then be used as the password for `flag.zip`.

## 4. Solution

### Step 1: Extract the challenge files

Extract:

```text
chrisbrown.zip
```

We get:

```text
hashbrown.png
flag.zip
```

The file `flag.zip` is password protected.

### Step 2: Inspect `hashbrown.png`

Open the image.

It contains:

<img width="2560" height="1440" alt="hashbrown" src="https://github.com/user-attachments/assets/fe978e8c-b12d-4348-b988-e22472c9cc61" />

This tells us that `hashbrown` is the value we need to work with.

### Step 3: Calculate the MD5 hash

Use an MD5 hashing tool or command.

For example:

```bash
echo -n "hashbrown" | md5sum
```

<img width="467" height="61" alt="image" src="https://github.com/user-attachments/assets/0911703b-7784-47aa-b151-2175defe92e8" />

This gives:

```text
afc85ee276f33abe7d041853c634fc36
```

The resulting MD5 hash is the password for `flag.zip`.

### Step 4: Open `flag.zip`

Use the MD5 hash as the password.

<img width="497" height="553" alt="image" src="https://github.com/user-attachments/assets/b3e20777-e486-44c4-b532-714849e2f37f" />

The archive extracts the flag.

### Step 5: Get the flag

The extracted flag is:

```text
MLUC{1_l0v3_h45hbr0wn}
```

## 5. Final Flag

```text
MLUC{1_l0v3_h45hbr0wn}
```

## 6. Solution Summary

```text
chrisbrown.zip
      ↓
Extract files
      ↓
hashbrown.png + password-protected flag.zip
      ↓
Read the clue: "hashbrown"
      ↓
MD5("hashbrown")
      ↓
Use MD5 hash as ZIP password
      ↓
Extract flag.zip
      ↓
MLUC{1_l0v3_h45hbr0wn}
```

```
```
