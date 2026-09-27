# The False Positives

*Category:* OSINT  
*Points:* 500 

## 1. Challenge Overview

We are given a list of 100 URLs and need to find the correct one.

The goal is to investigate the URLs and find the information needed to obtain the flag.

## 2. What to Look At

- There are many URLs to check.
- Manually checking all 100 URLs can take a while.
- VirusTotal can be used to investigate domains and retrieve useful information.
- The domain we are looking for is `theoldnet[.]com`.

*Clue for 50 points:* `Use VirusTotal`

## 3. Approach

Since there are 100 URLs, checking each one manually would be tedious.

The more efficient approach is to use **VirusTotal's API**. We can create a VirusTotal account, get an API key, and write a small Python script that checks each URL/domain automatically.

This allows us to go through all the URLs from the terminal instead of manually checking all 100 of them.

If you don't want to use the API, you can also manually check the URLs on VirusTotal. Good luck checking all 100 lol.

Or, if you're good at distinguishing phishing links from legitimate ones, we respect the skills.

## 4. Solution

### Step 1: Get a VirusTotal API Key

Create an account on VirusTotal and obtain an API key.

We can then use the API to query the URLs from a Python script.

### Step 2: Check the URLs

Create a Python script that sends each URL to the VirusTotal API and checks the results.

The script can be used to go through the entire list automatically and identify the relevant domain.

<img width="855" height="431" alt="image" src="https://github.com/user-attachments/assets/0e00ee3e-a872-45f0-b490-24fc98fe3161" />

### Step 3: Find the Relevant Domain

After checking the URLs, we find:

```text
theoldnet[.]com
````

We can then check this domain on VirusTotal to view its information.

<img width="1269" height="630" alt="image" src="https://github.com/user-attachments/assets/be190c82-c3b6-4287-b353-7ed86c30f20a" />

### Step 4: Get the IPv4 Address

Looking at the domain information, we find its IPv4 address:

```text
138.197.157.224
```

### Step 5: Get the Flag

The IPv4 address is used directly as the flag:

```text
MLUC{138.197.157.224}
```

## 5. Flag

```text
MLUC{138.197.157.224}
```
