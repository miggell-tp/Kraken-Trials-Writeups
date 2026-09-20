# Budget Report

**Author:** mpm4wi
**Category:** Steganography
**Difficulty:** Beginner
**Points:** 100

## 1. Challenge Overview

We are given a PDF containing a normal-looking PC budget report.

> Hello, could you review our PC budget report?

At first glance, everything appears normal. However, there is hidden text in the document that is not visible because its font color is **white**.

The goal is to find the hidden text and recover the flag.

## 2. What to Look At

The PDF looks like an ordinary budget report, so there is no obvious suspicious image or file attachment.

The important clue is that **text can still exist in a PDF even when it is invisible to the eye**.

In this case, the hidden text is located on the **last page** and uses a white font.

## 3. Approach

There are several easy ways to reveal the hidden text.

### Method 1: Ctrl + F

This is the easiest method.

1. Open `Budget_Report.pdf`.
2. Press:

```text
Ctrl + F
```

4. Search for any text that might be present on the page, or simply use the PDF viewer's text selection/search functionality.
5. The invisible white text becomes visible when it is selected/highlighted.

The hidden text can then be read and used as the flag.

<img width="1243" height="1304" alt="image" src="https://github.com/user-attachments/assets/1c1b1b79-8843-41ad-87f5-46b004be45cd" />

Copy it and paste it to your notepad.

<img width="526" height="82" alt="image" src="https://github.com/user-attachments/assets/ebc3b140-b7e0-49f5-975e-05f21c4d8548" />

## 4. Solution

The intended solution is simply to inspect the **last page** and notice that there is invisible text.

Because the text is white, it blends into the white background:

```text
White text + White background = Invisible
```

Highlighting or selecting the text reveals it.

## 5. Flag

The hidden text on the last page is the flag.

```text
MLUC{invisible_text_not_really_invisible}
```

### Solution Summary

```text
Open PDF
   ↓
Notice nothing suspicious
   ↓
Select / highlight the text
   ↓
White text becomes visible
   ↓
Read the flag
```

**Key takeaway:** In PDF steganography, hidden information does not always require complex tools. Text can be hidden simply by changing its font color to match the background.
