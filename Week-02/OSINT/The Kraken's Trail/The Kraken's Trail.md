# The Kraken's Trail

*Category:* OSINT  
*Author:* 0xj4n

*Description:*

Someone using the name `0xKrakenzzz` has been leaving digital footprints across the internet. What starts as an ordinary question may lead you much further than expected. Follow the trail, connect the identities, and pay attention to everything you find along the way. Some things are meant to be found. Others are meant to fool you.

The flag is case-insensitive, so you do not need to worry about capitalization.

*Attachments:* The challenge has no separate download package. The trail uses social-media posts, a Telegram bot, and a YouTube video. Screenshots are included in the local `Evidence Screenshots` folder.

## 1. Challenge Overview

We are given the username `0xKrakenzzz` and need to follow a chain of public online clues. The trail starts with a Reddit post, points to an Instagram post, then moves to an X account and a Telegram bot. The bot eventually provides a YouTube video whose audio must be reversed to hear the flag.

One of the clues is deliberately misleading: the puzzle on the X account's photos spells a fake flag. The challenge description also says that the flag is case-insensitive.

## 2. What to Look At

- Search results for `0xKrakenzzz` lead to a Reddit post about a first CTF.
- A comment on that post gives the ID `DdUKDuDj0SK`.
- That ID is an Instagram post shortcode, not an encoded string.
- The Instagram account is `packetbykraken`, and its caption says to look on another platform.
- The X account's photo puzzle is a decoy; a reply points to another challenge account.
- That account mentions a bot on another platform and includes `@MLUCKrakenBot` in its bio.
- The Telegram bot's answer leads to a YouTube video with reversed audio.

*Key clue:* “Same identity. Different platform.”

## 3. Approach

I started by searching for the supplied username and then checked the social account that matched it. Rather than trying to decode every unusual string, I treated each clue in context: the Reddit post ID had the shape of an Instagram shortcode, and the Instagram post explicitly hinted at looking for the same identity elsewhere.

The next important step was not trusting the apparent flag from the X photo puzzle. Its reply contains “jabaited,” and the commenter has a profile that continues the trail. Following that account's bot hint leads to Telegram, and the video returned by the bot reveals that its audio is reversed.

## 4. Solution

### Step 1: Find the Reddit account

Search Google for `0xKrakenzzz`, or use a username-search tool such as [Instant Username Search](https://instantusername.com/) or Sherlock to find platforms where the name appears to be used. These tools are useful leads, but verify a result by opening the profile or post.

The search leads to a Reddit post titled **“What's something you still remember from your first CTF?”**

![Search result for 0xKrakenzzz](<Evidence Screenshots/01-google-search.png>)

The username-search result also indicates that the Reddit username is taken.

![Username-search results for 0xKrakenzzz](<Evidence Screenshots/02-username-search-0xkrakenzzz.png>)

### Step 2: Read the Reddit comment

Open the post and inspect its comment. The user `0xKrakenzzz` says:

> As for me, you can check the post with the ID `DdUKDuDj0SK`.

![Reddit post and the comment containing the ID](<Evidence Screenshots/03-reddit-post-and-comment.png>)

At first, the ID may look like ciphertext. It is actually an Instagram post shortcode, so use it directly in this URL:

[https://instagram.com/p/DdUKDuDj0SK](https://instagram.com/p/DdUKDuDj0SK)

### Step 3: Follow the Instagram clue

The Instagram post is not the flag. Its caption says that the real flag may be on another social-media platform and gives the hint **“Same identity. Different platform.”** The account name is `packetbykraken`.

![Instagram post hinting at another platform](<Evidence Screenshots/04-instagram-clue.png>)

Search for `packetbykraken` again with a username-search tool. The results point to an X account with the same username, displayed as **MLUC Kraken**.

![X profile result for MLUC Kraken](<Evidence Screenshots/05-x-profile-search.png>)

![The MLUC Kraken X profile using packetbykraken](<Evidence Screenshots/06-x-profile.png>)

### Step 4: Inspect the X account's photos

Open the account's **Photos** tab. The images form a puzzle that appears to spell:

```text
MLUC{F4K3_FL4G_XD}
```

This is a decoy, not the final flag.

![Puzzle assembled from the X account's photos](<Evidence Screenshots/07-x-photos-puzzle.png>)

![The apparent fake flag from the photo puzzle](<Evidence Screenshots/08-decoy-flag.png>)

One of the puzzle posts has a reply from **Another MLUC Kraken** saying, “I got jabaited. You so goofy dawg.” The word “jabaited” is a strong hint that the apparent flag was intended to fool solvers. Follow the commenter instead of submitting the fake flag.

![Puzzle post with the jabaited comment](<Evidence Screenshots/09-puzzle-post-comment.png>)

### Step 5: Find the bot's platform

The commenter uses the handle `@packetbykraken1`. Their profile contains two useful clues:

- A post says, “I think my bot is already working on another platform. Can you test it?”
- The profile bio names the bot as `@MLUCKrakenBot`.

![Another MLUC Kraken profile with the bot hint](<Evidence Screenshots/10-bot-hint-profile.png>)

Search for `MLUCKrakenBot` with a username-search tool. The result identifies Telegram; then search for that exact handle in Telegram and open the bot.

![Username-search result pointing to Telegram](<Evidence Screenshots/11-telegram-username-search.png>)

### Step 6: Ask the Telegram bot

Start the bot with `/start`. It asks:

> Who was the first coach of the MLUC Trojans? Please use the format: John A. Doe.

The answer is **Alvin R. Malicdem**. Enter the name in the requested format. The bot confirms the answer and returns this YouTube video:

[https://www.youtube.com/watch?v=LlseF6BAYKo](https://www.youtube.com/watch?v=LlseF6BAYKo)

![Telegram bot accepting the answer and sharing the video](<Evidence Screenshots/12-telegram-bot-link.png>)

The video's title in the Telegram preview is itself reversed: `nekarK snotialutargnoC - egatS laniF ehT`. Reversing it reads **“The Final Stage - Congratulations Kraken,”** which hints at the transformation needed next.

### Step 7: Reverse the video's audio

The flag is spoken in the video, but the audio plays backward. Reverse the audio track and listen to it. For example, if you have the video saved locally, FFmpeg can reverse its audio into a WAV file:

```sh
ffmpeg -i challenge.mp4 -vn -af areverse reversed.wav
```

You can then play `reversed.wav`. Alternatively, import the audio track into Audacity, select the full track, and choose **Effect → Special → Reverse**.

The reversed audio reveals the flag:

```text
MLUC{c3rt1f13d_0s1nt_m4st3r}
```

![The linked YouTube video](<Evidence Screenshots/13-youtube-video.png>)
