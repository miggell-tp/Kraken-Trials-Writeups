# Dust

**Category:** Steganography
**Points:** 100

## 1. Challenge Overview

We are given a very large image. The goal is simply to inspect the image closely and find the hidden flag.

<img width="5000" height="5000" alt="dust" src="https://github.com/user-attachments/assets/b605f26d-0959-430b-aa2d-aa1bffab8cb8" />

## 2. What to Look At

The description says:

> **Big image what to do**

This hints that the flag may be hidden somewhere in the image and can be found by **zooming in**.

## 3. Solution

### Step 1: Open the image

Open `dust.png` normally.

### Step 2: Zoom in

Zoom into different areas of the image and look carefully for anything unusual.

The flag is visible when you **zoom in closely** on the image.

It is easy to overlook since it looks like a *DUST*

<img width="1900" height="1039" alt="image" src="https://github.com/user-attachments/assets/c1c8d2a8-c119-4321-a130-e07d94c94e0f" />

### Step 3: Find the Flag

Once you locate the hidden text, read the flag.

**Flag:** `MLUC{thought_it_was_dust}`
