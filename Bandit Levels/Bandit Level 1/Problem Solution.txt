## Problem /
The password for the next level is stored in a file called **readme** located in the home directory. /
Use this password to log into bandit1 using SSH. Whenever you find a password for a level, use SSH (on port 2220) to log into that level and continue the game./
We need to first log onto the game and then proceed to read the file called readme located in the home directory.
/
## Solution /
ssh bandit[levelNo]@bandit.labs.overthewire.org -p 2220 /
ls /
cat readme /
/
## Explanation /
To log into the game, we need to use the command ssh which allows us to remotely access the bandit server./
First use "ls" to look at the files in the current directory./
Then use the "cat" command and type in the file name to access the password./
/
## Password /
ZjLjTmM6FvvyRnrb2rfNWOZOTa6ip5If
/
## Lesson Learnt
The use of ssh command and how to access files.