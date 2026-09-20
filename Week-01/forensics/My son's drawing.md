# My Son's Drawing

**Author:** mpm4wi
**Category:** Forensics
**Difficulty:** Limit Testing
**Points:** 100

## 1. Challenge Overview

We are given a PNG file that cannot be opened normally.

> I am in the prison right now and my son sent me a drawing but i dont know how to open it....

The goal is to figure out what is wrong with the PNG and recover the drawing hidden inside it.

## 2. What to Look At

First, check the file:

```bash
file my-drawing.png
```

The output shows:

```text
PNG image data, 1702326119 x 1229146672, 101-bit
```

Those values are clearly unusual for a normal PNG.

Let's check the PNG structure:

```bash
pngcheck -v my-drawing.png
```

It reports that the PNG has invalid image information.

This suggests that the file may not actually contain a normal image.

## 3. Approach

Let's inspect the data after the PNG header:

```bash
xxd -s 16 -l 100 my-drawing.png
```

We see:

```text
6577 6f67 4943 4a30 6558 426c 496a 6f67
```

Interpreting these bytes as text gives:

```text
ewogICJ0eXBlIjog...
```

This looks like **Base64**.

So instead of trying to repair the PNG, we can extract and decode the hidden data.

## 4. Solution

### Step 1: Decode the Base64

Copy the Base64 data and open **CyberChef**.

Use the operation:

```text
From Base64
```

The decoded result is JSON.

It starts with something similar to:

```json
{
  "type": "657863616c6964726177",
  "version": 2,
  "source": "...",
  "elements": [...]
}
```

The value:

```text
657863616c6964726177
```

is hexadecimal for:

```text
excalidraw
```

This tells us that the hidden data is an **Excalidraw drawing**.

<img width="2559" height="1213" alt="image" src="https://github.com/user-attachments/assets/4be4f630-2a08-48bb-8382-f498199ae5dd" />

### Step 2: Render the JSON

Copy the complete decoded JSON from the first { to the last }.

Open **MassiveDiag Playground** and paste the JSON into the JSON renderer.

The JSON contains the drawing's elements and freehand strokes, so the playground can render the hidden drawing.

<img width="2538" height="1156" alt="Screenshot 2026-09-20 121829" src="https://github.com/user-attachments/assets/5e59d7cc-b828-42c8-85a0-8a711fbbb543" />

### Step 3: Inspect the drawing

After rendering the JSON, the son's drawing appears.

The flag is contained in the rendered drawing.

<img width="3514" height="1874" alt="svg markmap-svg markmap" src="https://github.com/user-attachments/assets/caf7ad62-1425-490f-a1b9-1d7235a4b998" />

## 5. Solution Summary

```text
my-drawing.png
      ↓
Check PNG
      ↓
xxd
      ↓
Find Base64
      ↓
CyberChef
From Base64
      ↓
Excalidraw JSON
      ↓
MassiveDiag Playground
      ↓
Render the JSON
      ↓
Read the flag
```

**Key takeaway:** The PNG was not a normal image. Its contents contained a Base64-encoded Excalidraw drawing, which could be decoded and rendered to recover the flag.
