````md
# git git git aw

**Category:** Misc  
**Points:** 100

## 1. Challenge Overview

We are given a ZIP file containing a Git repository.

> **Description:** Come git that flag

The goal is to inspect the Git history and find the hidden flag.

<img width="1278" height="1044" alt="image" src="https://github.com/user-attachments/assets/44df9666-d698-4747-9ce9-f2ae3cdb6e7b" />

## 2. What to Look At

After extracting the ZIP file, we open the folder in PowerShell and check the Git history.

## 3. Solution

### Step 1: Check the Git History

First, we run:

```powershell
git log
````

This shows that the repository has two commits:

```text
89af2a77a153aaa13e8a443e0a3d8faf7c3bcbbd (HEAD -> master)
git git git aw

69d4e9828e7768b66afc5200e6ea99be8a9828ba
git git git aw
```

<img width="488" height="174" alt="image" src="https://github.com/user-attachments/assets/a64c96ca-eb2d-47b2-9c35-b3c5ad972a62" />

We can also use the shorter version:

```powershell
git log --oneline
```

Output:

```text
89af2a7 (HEAD -> master) git git git aw
69d4e98 git git git aw
```

<img width="548" height="46" alt="image" src="https://github.com/user-attachments/assets/94d7cc39-d231-4a35-81c9-adc546d9620b" />

### Step 2: Check What Changed

Since there are two commits, we can check what changed between them using:

```powershell
git log -p
```

This shows that `flag.txt` was deleted in the latest commit:

```text
diff --git a/flag.txt b/flag.txt
deleted file mode 100644
...
-MLUC{git_git_git_that_flag}
```

<img width="496" height="397" alt="image" src="https://github.com/user-attachments/assets/8be4b2ad-8919-4dde-9243-55b799b0aad1" />

### Step 3: Check the Previous Commit

Looking at the previous commit, we can see that `flag.txt` was originally created with the flag:

```text
diff --git a/flag.txt b/flag.txt
new file mode 100644
...
+MLUC{git_git_git_that_flag}
```

The flag is:

```text
MLUC{git_git_git_that_flag}
```

## 4. Flag

```text
MLUC{git_git_git_that_flag}
```

## 5. Key Takeaway

When solving a Git-based CTF challenge, always check the repository's history.

Even if a file has been deleted, Git may still keep its contents in an older commit.

Useful commands:

```powershell
git log
git log --oneline
git log -p
```

```
```
