---
title: Level 4 to Level 5
---
Now while being logged in as the user `bandit4`, you need to find the password of user `bandit5` in order to complete this level.

If you haven't completed the previous level, do check out the write-up for Level 3 to Level 4, which is present [[Level3_to_Level4|here]].
### Follow these steps to proceed:
- Password for this level is stored in the only human readable file inside the `inhere` directory
- Navigate to the `inhere` directory using the command `cd inhere`
- To check which file is human readable, we can use the `file` command. Now we can check each file by hand, but let's write a bash one liner for it
- This is the bash one liner that you need to run: 
```bash
for f in *; do file "./$f"; done
```
- This will show you the list of all file types in the directory, the output will look like this:
```text
./-file00: PGP Secret Sub-key -
./-file01: data
./-file02: data
./-file03: data
./-file04: data
./-file05: data
./-file06: data
./-file07: ASCII text
./-file08: data
./-file09: data
```
- You can see, only one file is of the type `ASCII text`, so we simply read its contents using the command `cat ./-file07`. Please use the technique of reading file with special characters, as mentioned in the writeup for Level 1 to Level 2 [[Level1_to_Level2|here]].

Password obtained at the time of writing this write-up: `4oQYVPkxZOOEOO5pTW81FB8j8lxXGUQw`
### Note
Passwords on each of the levels are known to change regularly after a specific interval of time. So instead of skimming through the write-up, it is recommended to solve the challenge by hand.