---
title: Level 14 to Level 15
---
Now while being logged in as the user `bandit14`, you need to find the password of user `bandit15` in order to complete this level.

If you haven't completed the previous level, do check out the write-up for Level 13 to Level 14, which is present [[Level13_to_Level14|here]].
### Follow these steps to proceed:
- In this level, you'll have to use the password found in the [[Level13_to_Level14|previous level]]
- We need to enter that password to a service running on the port `30000` on the server
- In order to connect to that service, we can use `netcat`, which can be run as follows:
```bash
nc localhost 30000
```
- After running this, put the password and press enter. You'll be greeted with the following message:
```text
Correct!
<password>
```
- This is the required password
- Password obtained at the time of writing this write-up: `8xCjnmgoKbGLhHFAZlGE5Tmu4M2tKJQo`
### Note
Passwords on each of the levels are known to change regularly after a specific interval of time. So instead of skimming through the write-up, it is recommended to solve the challenge by hand.