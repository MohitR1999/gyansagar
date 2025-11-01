---
title: Level 11 to Level 12
---
Now while being logged in as the user `bandit11`, you need to find the password of user `bandit12` in order to complete this level.

If you haven't completed the previous level, do check out the write-up for Level 10 to Level 11, which is present [[Level10_to_Level11|here]].
### Follow these steps to proceed:
- Password for this level is stored in a file called ```data.txt``` which has been encrypted with [ROT13](https://en.wikipedia.org/wiki/ROT13) algorithm
- It is a very simple substitution cipher that replaces a letter with the 13th letter after it in the Latin Alphabet
- In other words, `A` becomes `N`, `B` becomes `O`, and so on.
- In order to crack this, we can use [CyberChef](https://gchq.github.io/CyberChef), a simple but powerful tool developed by [GCHQ](https://www.gchq.gov.uk/)
- Just visit [CyberChef](https://gchq.github.io/CyberChef), search for `ROT13`, add it to the `Recipe` section, and paste the text present in `data.txt` in the input section
- You'll get the following output:
```text
The password is <password>
```

Password obtained at the time of writing this write-up: `7x16WNeHIi5YkIhWsfFIqoognUTyj9Q4`
### Note
Passwords on each of the levels are known to change regularly after a specific interval of time. So instead of skimming through the write-up, it is recommended to solve the challenge by hand.