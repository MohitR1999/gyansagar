---
title: Level 8 to Level 9
---
Now while being logged in as the user `bandit8`, you need to find the password of user `bandit9` in order to complete this level.

If you haven't completed the previous level, do check out the write-up for Level 7 to Level 8, which is present [[Level7_to_Level8|here]].
### Follow these steps to proceed:
- Password for this level is stored in a file ```data.txt``` and is the only line of text that occurs once
- For this we will first sort the file in lexicographical order, and then find the only unique line using the ```uniq``` command
- Run the following command in order to sort the file and return the only unique line:
```bash
sort data.txt | uniq -u
```
- This will directly print the password string

Password obtained at the time of writing this write-up: `4CKMh1JI91bUIZZPXDqGanal4xvAg0JM`
### Note
Passwords on each of the levels are known to change regularly after a specific interval of time. So instead of skimming through the write-up, it is recommended to solve the challenge by hand.