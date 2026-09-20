# Pinoy Almusal

**Category:** Crypto
**Points:** 100

## 1. Challenge Overview

We are given a series of musical notes and the following clue:

> I remember the melody and it goes like this but I'm unable to find the title of the song.

The goal is to decode the musical notes and recover the hidden message.

<img width="713" height="129" alt="song" src="https://github.com/user-attachments/assets/69c6365d-cb64-4603-9f38-b96ccfb43195" />

## 2. What to Look At

The image contains a sequence of notes written on a musical staff.

Instead of trying to identify the song itself, we can treat the notes as a **cipher**. dCode has a **Music Sheet Cipher** tool that can decode musical notes by mapping them to letters. :contentReference[oaicite:0]{index=0}

**Key clue:** The image contains individual musical notes that can represent letters.

## 3. Approach

We can use **dCode's Music Sheet Cipher** to decode the notes.

The tool allows musical notes to be associated with letters or numbers, making it suitable for this type of challenge. 

## 4. Solution

### Step 1: Open the Music Sheet Cipher

Go to dCode and open the **Music Sheet Cipher** tool.

Select the option for decoding a music sheet.

### Step 2: Enter the notes

Read the notes from the image and enter them into the dCode decoder in the same order.

The notes should be entered from **left to right**, following the musical staff.

### Step 3: Decode the message

After entering the notes and using the appropriate note-to-letter mapping, dCode gives:

```text
M4LUNGG4YP4ND3SAL
````

<img width="1176" height="1196" alt="image" src="https://github.com/user-attachments/assets/36fbf15f-b971-48c2-9cb3-1e5f39b9d1fd" />

### Step 4: Get the Flag

The challenge specifies the flag format `MLUC{FLAG}`.

Enclose the decoded message in `MLUC{}`:

```text
MLUC{M4LUNGG4YP4ND3SAL}
```

**Flag:**

```text
MLUC{M4LUNGG4YP4ND3SAL}
```
