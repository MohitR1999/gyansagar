---
title: Level 15 to Level 16
---
Now while being logged in as the user `bandit15`, you need to find the password of user `bandit16` in order to complete this level.

If you haven't completed the previous level, do check out the write-up for Level 14 to Level 15, which is present [[Level14_to_Level15|here]].
### Follow these steps to proceed:
- In this level, you'll have to use the password you have for the current level, and pass it to the service running on port `30001` via an encrypted channel (over SSL)
- We cannot use `netcat` in the same way as before, because it won't be encrypted. Instead, we can use `openssl` to do the same
- In order to connect to that service, we can run the following command:
```bash
openssl s_client -connect localhost:30001
```
- After running this, put the password and press enter. You'll be greeted with the following message:
```text
Correct!
<password>
```
- This is the required password
- Password obtained at the time of writing this write-up: `kSkvUpMQ7lBYyCM4GBPvCvT1BfWRy0Dx`
### Note
Passwords on each of the levels are known to change regularly after a specific interval of time. So instead of skimming through the write-up, it is recommended to solve the challenge by hand.