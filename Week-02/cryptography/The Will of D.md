# The Will of D.

*Category:* Cryptography  
*Points:* 200

*Description:*

> *“My treasure? If you want it, you can have it! Find it! I left everything this world has to offer there!”*

The words of the Pirate King once shook the world and sent countless pirates sailing toward the Grand Line.

Now, a strange Poneglyph has been discovered, along with a treasure that has remained sealed for generations.

The Poneglyph contains a mysterious inscription and a set of numbers. Somewhere within them lies the key to opening the treasure.

The will of those who came before has not disappeared.

It has only been waiting for someone to uncover it.

Follow the inscription. Recover what was left behind. Inherit the will.

**Files:**

- `poneglyph.txt`
- `last_treasure.zip`

**Flag format:**

`MLUC{...}`

> *The treasure awaits at the end of the voyage.*

## 1. Challenge Overview

We are given a Poneglyph containing several numbers and a password-protected ZIP file.

The goal is to figure out what the numbers represent, recover the key needed to open `last_treasure.zip`, and find the flag inside.

## 2. What to Look At

Opening `poneglyph.txt` gives us several large numbers:

```text
p = 1000000007
q = 1000123469

n = 1000123476000864283
e = 65537
````

The values `n` and `e` look like RSA parameters.

Since `n` is a very large number, we can use FactorDB to investigate it and see what it is made of.

*Key clue:* `n`, `e`, `p`, and `q`

## 3. Approach

I first inspected the numbers in the Poneglyph.

The values suggest that we are dealing with RSA. To confirm what `n` is made of, we can look it up in FactorDB.

FactorDB shows that `n` can be factored into the same two numbers given as `p` and `q`.

With `p`, `q`, and `e`, we can calculate the RSA private exponent `d`.

The resulting `d` is then used as the password for the ZIP file.

## 4. Solution

### Step 1: Read the Poneglyph

Open `poneglyph.txt` and take note of the numbers:

```text
p = 1000000007
q = 1000123469

n = 1000123476000864283
e = 65537
```

<img width="534" height="576" alt="image" src="https://github.com/user-attachments/assets/002157ea-564b-4010-aec3-92b2440724e4" />

### Step 2: Check n Using FactorDB

Since `n` is a very large number, we can use **FactorDB** to check its factors.

Enter:

```text
1000123476000864283
```

into FactorDB.

FactorDB shows:

```text
1000000007 × 1000123469
```

These match the `p` and `q` values from the Poneglyph.

<img width="1280" height="689" alt="image" src="https://github.com/user-attachments/assets/ff61b081-563d-45e4-a309-a609fd0e2074" />

This confirms that the numbers are part of an RSA setup.

### Step 3: Calculate φ(n)

For RSA, we first calculate Euler's totient:

```text
φ(n) = (p - 1)(q - 1)
```

Using the given values:

```text
φ(n) = (1000000007 - 1)(1000123469 - 1)
```

This gives:

```text
φ(n) = 1000123474000740808
```

### Step 4: Calculate the Private Key d

The RSA private exponent `d` is the modular inverse of `e` modulo `φ(n)`:

```text
d ≡ e⁻¹ mod φ(n)
```

Using:

```text
e = 65537
φ(n) = 1000123474000740808
```

we get:

```text
d = 502068484895927073
```

This gives us the key:

```text
502068484895927073
```

<img width="734" height="558" alt="image" src="https://github.com/user-attachments/assets/71bd7ccd-6540-4836-9cfe-609b81a49f42" />

### Step 5: Use d as the ZIP Password

Now open:

```text
last_treasure.zip
```

When the ZIP asks for a password, enter:

```text
502068484895927073
```

The ZIP opens successfully and reveals the treasure.

<img width="813" height="599" alt="image" src="https://github.com/user-attachments/assets/d21e7879-7664-4275-9f86-783e0c095f95" />

### Step 6: Read the Flag

Inside the extracted files, we find the flag:

```text
MLUC{D_UNL0CKS_TH3_TR34SUR3}
```

<img width="356" height="396" alt="image" src="https://github.com/user-attachments/assets/a144860b-debf-4f93-966c-067f298122ad" />

## 5. Flag

```text
MLUC{D_UNL0CKS_TH3_TR34SUR3}
```

## 6. Key Takeaway

The Poneglyph gives us the values needed to identify and solve the RSA setup.

The solving process is:

```text
n
↓
FactorDB
↓
p and q
↓
φ(n)
↓
d
↓
ZIP password
↓
MLUC{D_UNL0CKS_TH3_TR34SUR3}
```

The treasure was sealed with the RSA private exponent. Inherit the will, and the treasure opens.

## 7. The Hidden Hint

The letter **D** is mentioned repeatedly throughout the challenge.
This was also a hint toward the RSA private exponent **`d`**.

After solving the RSA parameters, we recover:

```text
d = 502068484895927073
```

That value becomes the password for last_treasure.zip.
