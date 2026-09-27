# Professor Left His Tab Open

*Category:* Forensics  
*Points:* 100  
*Author:* 0xj4n  
*Description:* Professor K. left an exported Chromium profile behind after a lecture. Most of it is ordinary university browsing, but something feels deliberately out of place. A recovered browser fragment may reveal what they tried to remove.  
*Attachments:* [Download the evidence ZIP from the challenge link](http://161.118.223.219:5006/downloads/professor-left-tab-open.zip)

If the link is down already, you can get the copy here: [professor-left-tab-open.zip](professor-left-tab-open.zip).
## 1. Challenge Overview

The challenge provides a link to download a ZIP file containing an exported Chromium profile. Use the challenge link or local copy listed under **Attachments** above.

The goal is to examine the browser artifacts, recover a link the professor removed, and decode the flag found there.

## 2. What to Look At

- `Default/History` is a SQLite database containing visited page titles and URLs.
- `Default/Bookmarks` contains the current bookmarks.
- `Default/Bookmarks.bak` is a backup that still contains a removed bookmark.
- `Default/Network/Cookies` is present, but its cookie is not needed to solve the challenge.
- The search for “how to hide CTF flag from students” is a humorous hint to inspect the profile carefully.

*Key clue:* The backup bookmark file has one entry that is missing from the current bookmarks.

## 3. Approach

First, use the browsing history to identify the relevant site among the professor's ordinary school browsing. Then compare the current bookmarks with the backup to find the deleted entry. The recovered URL leads to a short encoded payload. The payload uses ROT13, which shifts each letter by 13 places in the alphabet; digits and punctuation remain unchanged.

## 4. Solution

### Step 1: Download and extract the evidence

Download `professor-left-tab-open.zip` from the challenge link under **Attachments** (or use the local copy there). In Windows File Explorer, right-click the ZIP and choose **Extract All**. Open the extracted `professor-left-tab-open` folder, then its `Default` folder.

You do not need to import this data into Chrome. We can inspect the files directly.

### Step 2: Find the relevant site in History

The file named `History` is a SQLite database. If you do not already have a SQLite viewer, **DB Browser for SQLite** provides a beginner-friendly graphical interface.

1. Open DB Browser for SQLite.
2. Choose **Open Database** and select the `Default/History` file. It may not have a file extension; that is expected.
3. Open the **Browse Data** tab.
4. Select the `urls` table from the table dropdown.
5. Review the `title` and `url` columns.

Most rows are ordinary browsing. One row is titled **MLUC Research Archive** and points to `http://161.118.223.219:5006/`. The unusual search “how to hide CTF flag from students” is another nudge that the profile contains something relevant.

### Step 3: Recover the deleted bookmark

In the same `Default` folder, open `Bookmarks` and `Bookmarks.bak` in a text editor such as Notepad. These are JSON files, so they can be read as ordinary text.

The current `Bookmarks` file has only the University Library and Course planning entries. In `Bookmarks.bak`, look for **Read after the colloquium — do not share**. Its `url` field points to the payload:

[Download from the challenge link](http://161.118.223.219:5006/files/professor-k-archive-7f2a.enc)

If the link is down already, you can get the copy here: [professor-k-archive-7f2a.enc](professor-k-archive-7f2a.enc).

The `.bak` file is a leftover backup of the bookmarks. It preserved an entry that is no longer in the current bookmark list.

### Step 4: Open the recovered link

Visit the URL from the deleted bookmark. The file contains this text:

```text
ZYHP{l0he'3_4_q3g3pg1i3}
```

This looks like the flag format, but its letters—including the apparent `ZYHP` wrapper—have been changed with ROT13.

### Step 5: Decode the payload with ROT13

ROT13 replaces each letter with the letter 13 positions away in the alphabet. For example, `Z` becomes `M`, `Y` becomes `L`, `H` becomes `U`, and `P` becomes `C`. Numbers, underscores, and the apostrophe do not change. You can also use the [dCode ROT13 Cipher tool](https://www.dcode.fr/rot-13-cipher) to decode it.

Apply ROT13 to the entire payload:

```text
ZYHP{l0he'3_4_q3g3pg1i3}
MLUC{y0ur'3_4_d3t3ct1v3}
```

The recovered flag is:

```text
MLUC{y0ur'3_4_d3t3ct1v3}
```
