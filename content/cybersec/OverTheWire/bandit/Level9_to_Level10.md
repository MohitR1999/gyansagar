---
title: Level 9 to Level 10
---
Now while being logged in as the user `bandit9`, you need to find the password of user `bandit10` in order to complete this level.

If you haven't completed the previous level, do check out the write-up for Level 8 to Level 9, which is present [[Level8_to_Level9|here]].
### Follow these steps to proceed:
- Password for this level is stored in a file called ```data.txt``` in one of the few human readable strings, preceded by several ```=``` characters
- Now since there are only a few strings that are human readable, we can use the `strings` command to get those, and then `grep` the `=` character to find the string
- Use the following bash one liner for this:
```bash
strings data.txt | grep '=========='
```
- This will give you the following output:
```text
========== the
========== password{k
=========== is
========== <password>
```
Password obtained at the time of writing this write-up: `FGUW5ilLVJrxX9kMYMmlN4MgbpfMiqey`
### Note
Passwords on each of the levels are known to change regularly after a specific interval of time. So instead of skimming through the write-up, it is recommended to solve the challenge by hand.