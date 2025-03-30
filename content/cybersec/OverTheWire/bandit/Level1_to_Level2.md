---
title: Level 1 to Level 2
---
Now while being logged in as the user `bandit1`, you need to find the password of user `bandit2` in order to complete this level.

If you haven't completed the previous level, do check out the write-up for Level 1, which is present [[Level0_to_Level1|here]].

#### Follow these steps to proceed:
- Use the `ls` command to list all the files in a directory
- There is a file named `-` in the home directory
- Now, while reading the file, we encounter a problem: the character `-` is a special character in `bash` shell, which is interpreted differently and not how we want it.
- So to read the contents of the file, we need to specify the file name along with its path in the `cat` command like this: `cat ./-`
- This will show you the password of the user `bandit2`. Note that down and proceed forward to the next level.

Password obtained at the time of writing this write-up: `263JGJPfgU6LtdEvgfWU1XP5yac29mFx`

### Note
Passwords on each of the levels are known to change regularly after a specific interval of time. So instead of skimming through the write-up, it is recommended to solve the challenge by hand.

