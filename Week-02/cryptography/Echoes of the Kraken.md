# Echoes of the Kraken

*Category:* Crypto  
*Points:* 100

## 1. Challenge Overview

We are given an encrypted message and a clue telling us that the beast beneath the waves knows the way.

The description says:

> The beast beneath the waves knows the way.  
> Its name is the key.

The encrypted text is:

```text
WCUM{XUO_BRKORX_IEGEENJ_TRSFO_NHY_OAYN_TRI_XOP}
````

The clue tells us that the name of the beast is the key.

## 2. What to Look At

* The ciphertext looks like it uses a substitution-based cipher.
* The clue specifically tells us that the beast's name is the key.
* The beast in the challenge is the **Kraken**.
* Therefore, the key is:

```text
KRAKEN
```

*Key clue:* `KRAKEN`

## 3. Approach

I first looked at the clue instead of trying random ciphers.

The description says **"Its name is the key."** Since the challenge is based around the Kraken, we can use `KRAKEN` as the key.

We can then use a Vigenère Cipher decoder with the key `KRAKEN`.

## 4. Solution

### Step 1: Identify the Key

From the description:

> Its name is the key.

The beast's name is **KRAKEN**, so we use:

```text
KRAKEN
```

### Step 2: Decode the Ciphertext

Use a Vigenère Cipher decoder and enter:

```text
WCUM{XUO_BRKORX_IEGEENJ_TRSFO_NHY_OAYN_TRI_XOP}
```

Use `KRAKEN` as the key.

<img width="883" height="629" alt="image" src="https://github.com/user-attachments/assets/30cb19e7-e151-4e45-b21c-2f7c467caa2e" />

The decoded message is:

```text
MLUC{THE_KRAKEN_REWARDS_THOSE_WHO_KNOW_THE_KEY}
```

### Step 3: Get the Flag

The decoded message already follows the flag format:

```text
MLUC{THE_KRAKEN_REWARDS_THOSE_WHO_KNOW_THE_KEY}
```

## 5. Flag

```text
MLUC{THE_KRAKEN_REWARDS_THOSE_WHO_KNOW_THE_KEY}
```
