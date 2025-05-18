---
title: Level 6 to Level 7
---
Now while being logged in as the user `bandit6`, you need to find the password of user `bandit7` in order to complete this level.

If you haven't completed the previous level, do check out the write-up for Level 5 to Level 6, which is present [[Level5_to_Level6|here]].
### Follow these steps to proceed:
- Password for this level is stored somewhere on the server in a file with the following properties:
	- owned by user ```bandit7```
	- owned by group ```bandit6```
	- exactly 33 bytes in size
- For finding this file, the ```find``` command had to be run with additional parameters specifying user, group and file size.
- Run the following bash one liner to find the file: 
```
 find / -type f -size 33c -user bandit7 -group bandit6 2>/dev/null
```
- This will give you one single file as follows:
```text
/var/lib/dpkg/info/bandit7.password
```
- Run the `cat` command on the file to reveal the password as: `cat /var/lib/dpkg/info/bandit7.password`
- **Important thing to notice about the `find` command:** since we are searching from the filesystem root `/`, there might be some files which we can't read or some directories which we might list due to permissions, hence we are suppressing the errors by redirecting the error console to `/dev/null` by appending `2>/dev/null` to the end of our command

Password obtained at the time of writing this write-up: `morbNTDkSW6jIlUc0ymOdMaLnOlFVAaj`
### Note
Passwords on each of the levels are known to change regularly after a specific interval of time. So instead of skimming through the write-up, it is recommended to solve the challenge by hand.