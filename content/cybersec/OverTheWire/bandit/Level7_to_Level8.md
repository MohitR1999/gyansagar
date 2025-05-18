---
title: Level 7 to Level 8
---
Now while being logged in as the user `bandit7`, you need to find the password of user `bandit8` in order to complete this level.

If you haven't completed the previous level, do check out the write-up for Level 6 to Level 7, which is present [[Level6_to_Level7|here]].
### Follow these steps to proceed:
- Password for this level is stored in the file ```data.txt``` next to the word ```millionth```
- We can use the `grep` command to search the word `millionth` and it will show the corresponding matched line.
- Use the following command to search through the file:
```bash
grep 'millionth' data.txt
```
- It will return the output with the matching word and the password as:
```text
millionth       <password>
```
Password obtained at the time of writing this write-up: `dfwvzFQi4mU0wfNbFOe9RoWskMLg7eEc`
### Note
Passwords on each of the levels are known to change regularly after a specific interval of time. So instead of skimming through the write-up, it is recommended to solve the challenge by hand.