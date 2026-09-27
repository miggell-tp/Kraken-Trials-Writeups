# The Evidence Board

*Category:* Forensics  
*Description:* Something happened inside the CIT Building after school hours.

A restricted room containing confidential student records was accessed after everyone had supposedly left.

Someone had a reason to get inside.

Your task is to investigate the evidence, connect the events, and identify who was responsible.

*Attachments:* Messenger conversation, system login log, CCTV footage, student grade record

## 1. Challenge Overview

We are given several pieces of evidence related to an unauthorized access inside the CIT Building:

- A Messenger conversation
- A system login log
- CCTV footage
- A student grade record

The goal is to connect the evidence, identify who was responsible, and recover the information needed for the flag.

The flag format is:

```text
MLUC{Culprit_Password_UpdatedGrade_LoginTime}
````

## 2. What to Look At

Start by examining each piece of evidence and looking for connections between them.

* The Messenger conversation gives us a possible motive.
* The CCTV footage helps identify who entered the restricted room.
* The system login log shows the account used to access the system.
* The student grade record shows the grade that was changed.

## 3. Approach

I first checked the evidence individually and then connected the information together.

The CCTV footage helps identify the person who entered the restricted room. The Messenger conversation gives us context about why they would want access.

Next, the system login log provides the password and exact login time. Finally, the student grade record confirms that a grade was changed.

By putting these pieces together, we can identify the culprit and construct the flag.

## 4. Solution

### Step 1: Examine the Messenger Conversation

Start by reading the Messenger conversation carefully.

Look for anything that could explain why someone would want to access the student records.

<img width="420" height="631" alt="image" src="https://github.com/user-attachments/assets/3b8afff8-a593-4876-9fc2-9e37afb7742f" />

The password was revealed in the message:

```text
Password: KRAKEN2026
```

### Step 2: Check the CCTV Footage

Next, examine the CCTV footage and identify the person who entered the restricted room.

The person identified is:

```text
Marvel Abuan
```

<img width="768" height="543" alt="image" src="https://github.com/user-attachments/assets/6052c2b2-4175-4733-81c5-a267851e08f3" />

### Step 3: Check the System Login Log

The description tells us that the incident happened **after school hours**. This gives us an important clue when checking the system login log.

We should look for a login that happened after school hours. Among the login entries, the relevant activity happened at:

```text
Login Time: 18:34:02
```

<img width="369" height="296" alt="image" src="https://github.com/user-attachments/assets/f22378d5-7d94-4d5e-a534-2a2fc3d85b55" />

### Step 4: Check the Student Grade Record

Finally, check the student grade record.

The relevant record shows that the grade was updated to:

```text
75
```

<img width="417" height="471" alt="image" src="https://github.com/user-attachments/assets/c1734d8e-0e08-4472-86a7-3125477800b3" />

### Step 5: Construct the Flag

The flag format is:

```text
MLUC{Culprit_Password_UpdatedGrade_LoginTime}
```

Using the information we found:

```text
Culprit: MarvelAbuan
Password: KRAKEN2026
Updated Grade: 75
Login Time: 18:34:02
```

The completed flag is:

```text
MLUC{MarvelAbuan_KRAKEN2026_75_18:34:02}
```

## 5. Flag

```text
MLUC{MarvelAbuan_KRAKEN2026_75_18:34:02}
```
