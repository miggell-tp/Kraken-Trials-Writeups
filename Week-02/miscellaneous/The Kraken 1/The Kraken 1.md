# The Kraken 1

*Category:* Forensics  
*Points:* 500  
*Author:* mpm4wi  
*Description:* :>
*Attachments:* [Download the ZIP from the challenge link](http://161.118.223.219:5006/downloads/the-dragon-warrior.zip)


## 1. Challenge Overview

The challenge features an interactive Kraken guarding chest #7. It may seem like you’re talking to an AI, but the Kraken follows scripted `if/else` logic. Although it’s listed under Misc to keep the Kraken challenges together, solving it is mainly a web challenge.

Check the website’s scripts for clues about how the conversation works, or talk to the Kraken and follow the hints it gives you. Either way, you’ll need to make the three offerings in the correct order to retrieve the flag.

## 2. What to Look At

Check the website’s scripts. You might find out how this whole Kraken thing works. The beast talks a big game, but its JavaScript might snitch.

## 3. Approach

The Kraken talks like an AI, but don’t let the tentacles fool you. Start by checking the website’s scripts and look for the conversation logic, clues, and the order of the offerings. If reading code feels like swimming through seaweed, you can also talk to the Kraken and follow its hints.

Keep an eye on the status pills to confirm each offering was accepted. The Kraken loves dramatic narration, but the pills keep the receipts. Once all three are lit, speak the tide-word again to bring up chest #7 and claim the flag.

## 4. Solution

## 4. Solution

The script lays out the order of the conversation. You can also follow the Kraken’s hints, but the scripted flow is the real map. Tentacles are dramatic. JavaScript is specific.

![Screenshot 1](./Pasted%20image%2020260928004720.png)

Just scroll down
### Step 1: Ask for a shanty

Start by asking the Kraken to sing, for example:

```
Sing me a song.
```

![Screenshot 2](./Pasted%20image%2020260928004813.png)

This begins the first stage.

### Step 2: Ask about the wreck

Once the Kraken has sung, ask about the wreck or the **Wailing Dowager**:

```
Tell me of the wreck.
```

![Screenshot 3](./Pasted%20image%2020260928010133.png)
### Step 3: Earn the tide-word

Ask what word the crew screamed, and show that you listened by mentioning the crew or the shanty. The tide-word is:

```
UNDERTOW
```
![Screenshot 4](./Pasted%20image%2020260928010207.png)

You have to earn it first. Just guessing the word at the start won’t count. The Kraken has standards. Apparently.

### Step 4: Say the tide-word

After the Kraken gives you the word, say:

```
UNDERTOW
```

![Screenshot 5](./Pasted%20image%2020260928010219.png)

This moves the conversation to the next stage.

### Step 5: Ask what the deep demands

Ask the Kraken what it wants in exchange:

```
What is the price deep?
```

![Screenshot 6](./Pasted%20image%2020260928010236.png)

### Step 6: Find the captain’s name

Ask who commanded the ship. The captain’s name is:

```
Elias Vane
```

![Screenshot 7](./Pasted%20image%2020260928010239.png)
### Step 7: Offer the captain’s name

Give the Kraken the name as payment:

```
Elias Vane
```

![Screenshot 8](./Pasted%20image%2020260928010312.png)

Check that the offerings have been accepted in the status pills beneath the conversation. The Kraken may have plenty to say, but the pills keep the receipts.

### Step 8: Open chest #7

Once all three offerings are accepted, say the tide-word one more time:

```
UNDERTOW
```
![Screenshot 9](./Pasted%20image%2020260928010336.png)

The chest opens, and the flag is yours. A little karaoke, some maritime lore, one captain’s name, and suddenly the Kraken is doing customer service.

```
MLUC{the_kraken_from_the_depths}
```

