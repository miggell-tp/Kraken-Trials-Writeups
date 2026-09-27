# Puede Nang Mangarap

*Category:* Forensics  
*Points:* 300  
*Author:* 0xj4n  
*Description:*

Hanapin mo ang pangarap mo dawg.

Good luck with the LSS😂😂😂

*Attachments:* [Watch or download Puede Nang Mangarap.mp4](<Puede Nang Mangarap/Puede Nang Mangarap.mp4>)

## 1. Challenge Overview

We are given a video. The flag is split into short text fragments that appear in different places in the video frame. Find each fragment and join them in the order they appear.

“LSS” means “Last Song Syndrome,” a hint that the attached video is central to the challenge.

## 2. What to Look At

- Small text flashes at different positions in the video, sometimes against a busy background.
- Pause or slow down playback when a fragment appears.
- The red marks in the annotated frames below point to the text to read.
- Keep the underscores and letter case when joining the fragments.

*Key clue:* Each red-marked snippet is part of one continuous `MLUC{...}` flag.

## 3. Approach

I watched the video carefully and paused on frames where faint text appeared. The fragments were scattered around the scene, so I read them in the order they appeared rather than trying to find the whole flag in one frame. Joining the pieces, including their underscores, formed the flag.

## 4. Solution

### Step 1: Open the video

Open the attached [video](<Puede Nang Mangarap.mp4>). Watch for brief, small text overlays. If a fragment is hard to read, pause the video or step through it frame by frame.

The screenshots below are copies of the frames you marked in red. The red underline shows where each fragment can be seen.

### Step 2: Read the fragments in order

1. The first fragment, beside the rainbow, is `MLUC{m4yr0n`.
   ![Red-marked frame showing fragment 1: MLUC{m4yr0n](<Writeup Frames/fragment-01.png>)

2. The next fragment, beside the mushroom on the left, is `_d1n_`.
   ![Red-marked frame showing fragment 2: _d1n](<Writeup Frames/fragment-02.png>)

3. The fragment near the cloud at the upper right is `n4m4n_`.
   ![Red-marked frame showing fragment 3: _n4m4n_](<Writeup Frames/fragment-03.png>)

4. The fragment near the tree at the upper left is `p4l4ng_g4nd4_`.
   ![Red-marked frame showing fragment 4: p4l4ng_g4nd4__](<Writeup Frames/fragment-04.png>)

5. The next fragment, near the top of the tree, is `_4ng_b0h41`.
   ![Red-marked frame showing fragment 5: 4ng_b0h41](<Writeup Frames/fragment-05.png>)

6. The last fragment, near the raised hand, is `_Xd`.

   ![Red-marked frame showing fragment 6: _Xd](<Writeup Frames/fragment-06.png>)

### Step 3: Join the pieces

Join the fragments in order. The red-marked piece appears to show two underscores between `g4nd4` and `4ng`; the author made a mistake in the flag at this point. The platform accepted one underscore, as noted below.

```text
MLUC{m4yr0n
_d1n
_n4m4n_
p4l4ng_g4nd4_
_4ng_b0h41
_Xd
```

The flag assembled from the video fragments is:

```text
MLUC{m4yr0n_d1n_n4m4n_p4l4ng_g4nd4__4ng_b0h41_Xd}
```

The platform-accepted flag is:

```text
MLUC{m4yr0n_d1n_n4m4n_p4l4ng_g4nd4_4ng_b0h41_Xd}
```

### Correction and apology

The author accidentally included an extra underscore between `g4nd4` and `4ng` in the flag. The platform accepted the version with only one underscore. Sorry for the mistake and any confusion. All players who attempted the challenge were able to get the accepted flag despite the typo.
