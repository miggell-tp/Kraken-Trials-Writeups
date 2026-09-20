# XORdinary

**Category:** Cryptography
**Points:** 100

## 1. Challenge Overview

We are given an encrypted message and a clue telling us that the encryption machine keeps using the **same key repeatedly**.

The machine says the key is:

```text
MLUC
```

The goal is to recover the original message and wrap it in `MLUC{}`.

## 2. What to Look At

The important clues are:

* The machine uses the **same characters over and over again**.
* The given key is `MLUC`.
* This suggests a **repeating-key XOR** encryption.
* The ciphertext contains non-printable characters, so we need to handle the data as raw bytes.

**Key clue:**

```text
The machine keeps saying the key is:

MLUC
```

## 3. Approach

We can use **CyberChef** to perform the XOR operation.

Since the ciphertext contains byte values that are not normal readable characters, we need to make sure CyberChef interprets the input correctly.

For the XOR operation:

* **Operation:** XOR
* **Key:** `MLUC`
* **Key format:** UTF-8

### Why UTF-8?

The key `MLUC` is a normal text string. Selecting **UTF-8** tells CyberChef to convert each character of the key into its corresponding byte value before performing XOR.

This lets CyberChef repeatedly apply the bytes for `MLUC` against the ciphertext.

## 4. Solution

### Step 1: Open CyberChef

Open CyberChef and add the **XOR** operation.

### Step 2: Enter the ciphertext

Paste the encrypted message into the input:

```text
4|y>f5|''|"a14
```

### Step 3: Configure XOR

Set the XOR operation to:

```text
Key: MLUC
Key type: UTF-8
```

<img width="2559" height="1212" alt="image" src="https://github.com/user-attachments/assets/9bb2af72-2e47-4a1b-b71c-e896c9ca6cb0" />

### Step 4: Decode the message

CyberChef produces:

```text
y0u_4r3_x0rd1n4ry
```

### Step 5: Wrap the message

The challenge tells us to wrap the recovered message in `MLUC{}`.

Therefore, the flag is:

```text
MLUC{y0u_4r3_x0rd1n4ry}
```
