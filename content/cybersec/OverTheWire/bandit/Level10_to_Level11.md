---
title: Level 10 to Level 11
---
Now while being logged in as the user `bandit10`, you need to find the password of user `bandit11` in order to complete this level.

If you haven't completed the previous level, do check out the write-up for Level 9 to Level 10, which is present [[Level9_to_Level10|here]].
### Follow these steps to proceed:
- Password for this level is stored in a file called ```data.txt``` which has been [base64](https://en.wikipedia.org/wiki/Base64) encoded
- We already have a built-in tool called `base64` that does this encoding and decoding for us
- Use the following bash one liner for this:
```bash
base64 data.txt --decode
```
- This will give you the following output:
```text
The password is <password>
```
Password obtained at the time of writing this write-up: `dtR173fZKb0RRsDFSGsg2RWnpNVj3qRr`
### Note
Passwords on each of the levels are known to change regularly after a specific interval of time. So instead of skimming through the write-up, it is recommended to solve the challenge by hand.