# Cat

**Category:** Forensics
**Points:** 100

## 1. Challenge Overview

We are given an image called `cat.png` with the description:

> The krazy car ate the flag!

<img width="1120" height="904" alt="cat" src="https://github.com/user-attachments/assets/14782e50-f9ed-4b36-bd29-4b3e665bec89" />

The image itself does not show the flag. The clue suggests that the flag was hidden inside the file.

## 2. What to Look At

The important clue is:

> The krazy car ate the flag!

Instead of looking at the image normally, we can inspect the contents of the file using the Linux `cat` command.

## 3. Approach

The `cat` command displays the contents of a file in the terminal.

Run:

```bash
cat cat.png
````

Since `cat.png` is a binary image, most of the output will appear as unreadable characters. However, the hidden flag was placed at the **end of the file**, so it will appear after the image data.

Scroll to the bottom of the output to find the flag.

## 4. Solution

### Step 1: Open the terminal

Navigate to the directory containing `cat.png`.

### Step 2: Display the file contents

Run:

```bash
cat cat.png
```

The terminal will display a large amount of unreadable binary data.

Scroll to the **end of the output**.

The hidden flag will be visible at the end of the file:

<img width="1518" height="860" alt="image" src="https://github.com/user-attachments/assets/5295d335-69a1-43a4-bf36-8ca97d35d160" />

### Step 3: Get the Flag

The flag is located after the image data at the end of `cat.png`.

```text
MLUC{cat_pussycat_meow}
```

The main idea is that the flag was appended to the image file, and `cat` allows us to see the extra data at the end.
