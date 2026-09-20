# Maintenance Room

**Category:** Cryptography

**Points:** 100

## 1. Challenge Overview

A suspicious transmission was recovered inside the College of Information Technology. Along with it, a damaged note was found near the transmission.

We are given two files:

* `transmission.txt` contains the suspicious transmission.
* `note.txt` contains a clue that helps us identify the key.

The objective is to recover the hidden flag.

> **Flag format:** `MLUC{...}`

## 2. What to Look At

Start by examining the files provided with the challenge.

* `transmission.txt` contains a string made up of hexadecimal characters.
* `note.txt` points toward the **CIT Maintenance Room**.
* The note tells us to find the number associated with the Maintenance Room.
* That number is used as part of the decryption process.

**Key clues:**

```text
transmission.txt → Hexadecimal
note.txt → Maintenance Room
Maintenance Room → Room 113
113 → XOR key
```

## 3. Approach

The challenge has two main layers:

1. Decode the transmission from Hexadecimal.
2. XOR the decoded data using `113` as the key.

We can use **CyberChef** to perform and verify both steps.

## 4. Solution

### Step 1: Open `transmission.txt`

The transmission contains:

```text
3c3d24320a402e1d4107422e4440032e45031f411d150c
```

Notice that it contains only hexadecimal characters (`0-9` and `a-f`).

This suggests that the first layer is **Hexadecimal encoding**.

### Step 2: Decode the Hex using CyberChef

Open **CyberChef** and paste the contents of `transmission.txt` into the **Input** section.

Search for the operation:

```text
From Hex
```

Drag **From Hex** into the **Recipe** section.

Your recipe should now look like:

```text
From Hex
```

The decoded output is:

```text
<=$2
@.
A
B.D@
.E
A
```

Some characters are not printable, so CyberChef may display them differently.

The important thing is that **we still do not have readable text**.

This tells us that the Hex encoding was only the first layer.

<img width="2559" height="1214" alt="image" src="https://github.com/user-attachments/assets/e414b669-f9cf-421e-bead-cc82afffc84f" />

### Step 3: Read `note.txt`

Open `note.txt`.

The note gives us the following clues:

> Every room has its place.
> Every place has its number.

It then specifically points toward the **Maintenance Room**.

The note tells us to:

> "Find what comes after its name."

This points us toward the number associated with the Maintenance Room.

### Step 4: Identify the key

The CIT Maintenance Room is:

```text
Room 113
```

Therefore, our key is:

```text
113
```

The note also says:

> "That number might be more than just a number."

This hints that `113` should be used in a cryptographic operation.

### Step 5: Add XOR in CyberChef

Go back to CyberChef.

Keep the existing:

```text
From Hex
```

operation.

Then search for:

```text
XOR
```

and add the **XOR** operation underneath `From Hex`.

Your recipe should now look like:

```text
From Hex
XOR
```

### Step 6: Configure XOR

In the **XOR** operation, set the key to:

```text
113
```

Make sure the key is interpreted as the numeric/byte value intended by the challenge.

The recipe is now:

```text
From Hex
XOR (Key: 113)
```

CyberChef will apply the operations from top to bottom:

```text
Hexadecimal
    ↓
From Hex
    ↓
Decoded bytes
    ↓
XOR with 113
    ↓
Plaintext
```

<img width="2559" height="1213" alt="image" src="https://github.com/user-attachments/assets/e769c74e-9496-4f35-a106-aabaed37654a" />

### Step 7: Recover the flag

After applying the XOR operation with key `113`, CyberChef produces:

```text
MLUC{1_l0v3_51r_4rn0ld}
```

Therefore, the flag is:

```text
MLUC{1_l0v3_51r_4rn0ld}
```

## 5. Complete CyberChef Recipe

The final CyberChef recipe is simply:

```text
From Hex
XOR
```

With the XOR key set to:

```text
113
```

So the complete process is:

```text
3c3d24320a402e1d4107422e4440032e45031f411d150c
                         ↓
                      From Hex
                         ↓
                    Decoded bytes
                         ↓
                    XOR with 113
                         ↓
             MLUC{1_l0v3_51r_4rn0ld}
```

## 6. Why It Works

The challenge uses two layers of encoding/encryption.

**Layer 1: Hexadecimal**

The original transmission is represented using hexadecimal characters. `From Hex` converts those characters back into their original byte values.

**Layer 2: XOR**

The resulting bytes are still encrypted. The note gives us the key by pointing toward the CIT Maintenance Room, which is **Room 113**.

Using `113` as the XOR key reveals the plaintext flag.

## 7. CTF Takeaway

**What to remember:**

* A string containing only `0-9` and `a-f` should make you think of **Hexadecimal**.
* CyberChef can quickly test common encoding and encryption techniques.
* If one decoding step produces unreadable data, don't immediately assume it failed. There may be another layer.
* Read challenge files carefully. Clues can contain the key.
* **XOR** is a common technique in CTF cryptography.
* Learn the recipe, not just the answer:

```text
Recognize → Decode → Investigate → Identify key → XOR → Flag
```
