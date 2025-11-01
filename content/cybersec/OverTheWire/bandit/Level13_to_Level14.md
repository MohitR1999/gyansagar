---
title: Level 13 to Level 14
---
Now while being logged in as the user `bandit13`, you need to find the password of user `bandit14` in order to complete this level.

If you haven't completed the previous level, do check out the write-up for Level 12 to Level 13, which is present [[Level12_to_Level13|here]].
### Follow these steps to proceed:
- In this level, there is no file that contains password.
- However, we do have a private key, contents of which are as follows:
```text
-----BEGIN RSA PRIVATE KEY-----
MIIEpAIBAAKCAQEAxkkOE83W2cOT7IWhFc9aPaaQmQDdgzuXCv+ppZHa++buSkN+
gg0tcr7Fw8NLGa5+Uzec2rEg0WmeevB13AIoYp0MZyETq46t+jk9puNwZwIt9XgB
ZufGtZEwWbFWw/vVLNwOXBe4UWStGRWzgPpEeSv5Tb1VjLZIBdGphTIK22Amz6Zb
...
```
- We can use this key to authenticate and log-in to the server as `bandit14`
- Copy this key at your end, I named it as `bandit14.key` on my machine
- Don't forget to set the correct permissions on the key as follows:
```bash
chmod 600 bandit14.key
```
- Use this key to log-in, as follows:
```bash
ssh -l bandit14 bandit.labs.overthewire.org -p 2220 -i bandit14.key
```
- Now, you can also view the password for `bandit14`, which is present at `/etc/bandit_pass/bandit14` (You'll need it)
- Password obtained at the time of writing this write-up: `MU4VWeTyJk8ROof1qqmcBPaLh7lDCPvS`
### Note
Passwords on each of the levels are known to change regularly after a specific interval of time. So instead of skimming through the write-up, it is recommended to solve the challenge by hand.