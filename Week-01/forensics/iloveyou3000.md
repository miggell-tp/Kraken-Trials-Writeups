# iloveyou3000

**Category:** Forensics
**Points:** 100

## 1. Challenge Overview

We are given a ZIP file containing folders named `iloveyou1` to `iloveyou3000`.

> I love you 3000.

The folders appear to have no useful contents, so we need to look at something else to find the flag.

## 2. What to Look At

After extracting `flag.zip`, we get 3,000 folders:

```text
iloveyou1
iloveyou2
iloveyou3
...
iloveyou3000
```

Most of them are empty.

Since there is nothing useful inside the folders, we can check their **Date modified**.

## 3. Approach

Instead of opening all 3,000 folders, simply sort them by their modification date.

## 4. Solution

### Step 1: Extract the ZIP

Extract `flag.zip`.

### Step 2: Sort by Date Modified

In File Explorer, click the **Date modified** column at the top to sort the folders.

The most recently modified folder will appear at the top.

It is:

```text
iloveyou2989
```

<img width="528" height="450" alt="image" src="https://github.com/user-attachments/assets/caa5c345-8314-42fb-88f4-ca1d2253df88" />

### Step 3: Open the Folder

Open `iloveyou2989` to find the flag.

<img width="1074" height="278" alt="image" src="https://github.com/user-attachments/assets/b32ef3c8-4b5f-4f5a-97ac-cd7b2b33b94f" />

## 5. Flag

```text
MLUC{1_l0v3_y0u_3000}
```

## Solution Summary

```text
flag.zip
   ↓
Extract
   ↓
3,000 folders
   ↓
Click Date modified
   ↓
iloveyou2989
   ↓
MLUC{1_l0v3_y0u_3000}
```
