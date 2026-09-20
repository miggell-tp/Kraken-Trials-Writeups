# back2normal

**Category:** Cryptography
**Points:** 100

## 1. Challenge Overview

We are given an encoded message:

```text
`fXk1NDNwX3k1NDN7Q1VMTQ==`
````

The challenge tells us that the machine reversed the message at some point, then did something else to it.

The goal is to undo the transformations in the correct order and recover the flag.

## 2. What to Look At

The ciphertext ends with `==`, which is a strong clue that **Base64** encoding was used.

The challenge also mentions that the message was reversed.

So we need to:

1. Decode the Base64.
2. Reverse the decoded message.

**Key clues:**

* The `==` at the end suggests Base64.
* The message was reversed at some point.

## 3. Approach

We can use **dCode** to decode the Base64 and then reverse the result.

The given ciphertext is:

```text
`fXk1NDNwX3k1NDN7Q1VMTQ==`
```

## 4. Solution

### Step 1: Decode the Base64

Using dCode's **Base64 Decode**, enter:

```text
`fXk1NDNwX3k1NDN7Q1VMTQ==`
```

The decoded result is:

```text
}y543p_y543{CULM
```

<img width="594" height="331" alt="image" src="https://github.com/user-attachments/assets/6d97bec8-d71c-4e5b-8502-e10eb48eeafd" />

### Step 2: Reverse the decoded message

The challenge says the message was reversed, so reverse the decoded text:

```text
MLUC{345y_p345y}
```

### Step 3: Get the Flag

The recovered message already follows the required `MLUC{}` format.

```text
MLUC{345y_p345y}
```
