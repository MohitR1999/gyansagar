---
title: Level 5 to Level 6
---
Now while being logged in as the user `bandit5`, you need to find the password of user `bandit6` in order to complete this level.

If you haven't completed the previous level, do check out the write-up for Level 4 to Level 5, which is present [[Level4_to_Level5|here]].
### Follow these steps to proceed:
- Password for this level is stored in a file that has the following properties:
    - human-readable
	- 1033 bytes in size
	- not executable
- However, running the ```find``` command with only the size parameter leaves us with a single file, telling that it is the only possible file that can match these properties.
- To check which file it is, run the following bash one liner: 
```bash
find . -type f -size 1033c
```
- This will give a single result as follows:
```text
./inhere/maybehere07/.file2
```
- We simply read its contents using the command `cat ./inhere/maybehere07/.file2`. Please use the technique of reading hidden files as mentioned in the writeup for Level 3 to Level 4 [[Level3_to_Level4|here]].

Password obtained at the time of writing this write-up: `HWasnPhtq9AVKe0dmk45nxy20cvUa6EG`
### Note
Passwords on each of the levels are known to change regularly after a specific interval of time. So instead of skimming through the write-up, it is recommended to solve the challenge by hand.