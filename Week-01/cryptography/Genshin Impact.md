# Genshin Impact

**Category:** Crypto
**Points:** 100

## 1. Challenge Overview

We are given a message written using the **Teyvat Language**, the fictional writing system used in *Genshin Impact*.

The goal is to identify the language, translate the characters into English, and recover the flag.

The encrypted message is:

<img width="978" height="68" alt="genshinimpact" src="https://github.com/user-attachments/assets/56ec34ae-0c66-4114-83ce-f38422b82527" />

## 2. What to Look At

The characters do not look like a normal cipher. Instead, they resemble the alphabet used in **Genshin Impact's Teyvat Language**.

Since this is a fictional writing system, we need to find a translator that supports it.

## 3. Approach

We can use **dCode** to find a translator for the Genshin Impact languages.

dCode has a section for **Genshin Impact** with different languages used in the game. Among the available options is **Teyvat Language**, which matches the characters in the challenge.

Once the Teyvat translator is selected, we can translate the characters one by one using the corresponding alphabet.
## 4. Solution

### Step 1: Find the Genshin Impact translator

Open dCode and search for the **Genshin Impact** language translator.

The translator provides several Genshin Impact languages.

Look for:

```text
Teyvat Language
```

<img width="1457" height="1257" alt="image" src="https://github.com/user-attachments/assets/59adb78f-62e5-4740-aa03-40fcec30d918" />

### Step 2: Select Teyvat Language

Choose **Teyvat Language** because its characters match the symbols given in the challenge.

The Teyvat alphabet provides the corresponding English letters for each symbol.

### Step 3: Translate the characters

Using the Teyvat alphabet, translate the symbols from the challenge **one by one**.

The message:

```text
[ Teyvat characters ]
```

translates to:

```text
PAIMONISTHEREALARCHON
```

<img width="1180" height="766" alt="image" src="https://github.com/user-attachments/assets/25db25c6-525c-40c7-928f-ce36f65cc0c0" />


### Step 4: Get the Flag

The challenge requires the recovered message to be enclosed in `MLUC{}`.

Therefore, the final flag is:

```text
MLUC{PAIMONISTHEREALARCHON}
```
