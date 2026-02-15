## Problem
Another escape problem! Figure it out.  

## Solution
ls
*RESULT:*  
`sh: 1: LS: Permission denied`  

$0  
cat /etc/bandit_pass/bandit33  

## Explanation
When we enter into this level, we observe the welcoming message, 'WELCOME TO THE UPPERCASE SHELL'. So this is a new shell that we have to figure out.  
Now when we enter a command, which the first command is likely always going to be `ls` (but of course it can be anything), and we get an error message saying that the shell has responded with a standard output message of our command but in the uppercase format, so permission is denied.  
This implies that anything is typed into the shell will be converted into all uppercase letters, this could be the work of some sort of script running in the shell. This evidently means that no commands that we execute will work due to linux being extremely case sensitive.  
To bypass this, what we can do is make use of an environment variable `$0`, using this command allows us to launch a new fresh shell as it expands the shell to the path of the current shell, which in this case, could have been `/bin/bash`. Of course, this command works because it cannot be made into uppercase due to the sole use of symbols in this command, but also due to the fact, that environment variables are run before the execution of the uppercase commands on this shell.  
Finally, we can just read and access the password for the next level.  

## Password
tQdtbs5D5i2vJwkO8mEyYEyTL8izoeJ0  

## Lesson Learnt
That enviroment variables are run before commands from the shell, and that the "$0" initiates the shell to launch a new fresh one.  