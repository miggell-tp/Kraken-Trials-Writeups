# Caesar the Great

*Category:* Crypto  
*Points:* 100

## 1. Challenge Overview

We are given a ciphertext along with a clue mentioning **Rome**.

The goal is to identify the cipher being used, decode the ciphertext, and obtain the flag.

```text
POXF{1_i0xqg_U0p3_4_f17b_0i_eu1fn5_4qg_o3i7_17_4_f17b_0i_p4ueo3}
````

## 2. What to Look At

Start with the clue and the ciphertext.

* The challenge mentions **Rome**.
* The ciphertext contains letters, numbers, and underscores.
* The flag format starts with `POXF` instead of the expected `MLUC`.
* The reference to Rome can point us toward **Julius Caesar**.

*Key clue:* `Rome`

## 3. Approach

I first looked at the clue because the mention of **Rome** seemed intentional.

Rome is associated with **Julius Caesar**, which suggests that the ciphertext may use a **Caesar Cipher**.

Instead of manually trying different shifts, we can use **dCode's Cipher Identifier** to determine the cipher.

## 4. Solution

### Step 1: Identify the cipher with dCode

Go to:

[https://www.dcode.fr/cipher-identifier](https://www.dcode.fr/cipher-identifier)

Paste the ciphertext:

```text
POXF{1_i0xqg_U0p3_4_f17b_0i_eu1fn5_4qg_o3i7_17_4_f17b_0i_p4ueo3}
```

dCode identifies the ciphertext as a **Caesar Cipher**.

Click the **Caesar Cipher** result to open the decoder.

### Step 2: Decode the ciphertext

Enter the ciphertext into the Caesar Cipher tool.

The correct shift is **3**.

After applying the shift, we get:

```text
MLUC{1_f0und_R0m3_4_c17y_0f_br1ck5_4nd_l3f7_17_4_c17y_0f_m4rbl3}
```

The numbers are intentional leetspeak and should be kept exactly as they appear.

### Step 3: Get the flag

The decoded message is:

```text
MLUC{1_f0und_R0m3_4_c17y_0f_br1ck5_4nd_l3f7_17_4_c17y_0f_m4rbl3}
```

## 5. Final Flag

```text
MLUC{1_f0und_R0m3_4_c17y_0f_br1ck5_4nd_l3f7_17_4_c17y_0f_m4rbl3}
```

## 6. Solution Summary

```text
Rome
  ↓
Julius Caesar
  ↓
dCode Cipher Identifier
  ↓
Caesar Cipher
  ↓
Shift 3
  ↓
MLUC{1_f0und_R0m3_4_c17y_0f_br1ck5_4nd_l3f7_17_4_c17y_0f_m4rbl3}
```

```
```
