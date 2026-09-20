# Flip

**Category:** Forensics

**Points:** 100

## 1. Challenge Overview

We are given a file called `flip.png`, but the image cannot be opened normally.

The description says:

> Hi duds nagpaedit ako sa tropa ko sabi ko "baliktarin ung pic" pero nung bubuksan ko na may problema may idea ka ba dito?!

The clue **"baliktarin ung pic"** suggests that the file needs to be reversed.

The goal is to recover the image and find the hidden flag.

## 2. What to Look At

The file has a `.png` extension, but it cannot be opened as a normal image.

The description specifically tells us to **reverse the picture**.

Instead of flipping the image visually, we can try reversing the **bytes of the file**.

**Key clue:**

> "baliktarin ung pic"

## 3. Approach

We can use **CyberChef** to reverse the file without using the command line.

Open CyberChef and upload `flip.png`.

Then search for the **Reverse** operation and add it to the recipe.

The idea is:

```text
flip.png
   ↓
Reverse the bytes
   ↓
Recovered image
````

## 4. Solution

### Step 1: Open CyberChef

Open:

```text
https://gchq.github.io/CyberChef/
```

Upload `flip.png` into the input area.

### Step 2: Reverse the file

Search for:

```text
Reverse
```

Add the **Reverse** operation to the recipe.

Make sure the file is being reversed at the byte level.

Then the wand icon beside the Output will light up. Click it to render the image.

<img width="2559" height="1214" alt="image" src="https://github.com/user-attachments/assets/99c9700c-f533-4b9e-9100-3162d375266e" />

### Step 3: Recover the image

After reversing the file, save the output and open it as an image.

<img width="1200" height="600" alt="recovered" src="https://github.com/user-attachments/assets/e2eb5dee-48ea-4564-8b3c-f1b42b7cb6bb" />

The recovered image contains the flag:

```text
MLUC{fl1p_th3_1mage_not_the_byt3z}
```

### Step 4: Get the Flag

```text
MLUC{fl1p_th3_1mage_not_the_byt3z}
```
