## Problem
Access the next level. However, the next level's shell does not use /bin/bash, figure out what it is and how to break out of it.  

## Solution
cat /etc/passwd | grep bandit26  
*RESULT:*  
`bandit26:x:11026:11026:bandit level 26:/home/bandit26:/usr/bin/showtext`  
  
cat /usr/bin/showtext
*RESULT:*
`#!/bin/sh`  
  
`export TERM=linux`  
  
`more ~/text.txt`  
  
scp -P 2220 bandit25@bandit.labs.overthewire.org:bandit26.sshkey .    
chmod 700 bandit26.sshkey  
ssh -i bandit26.sshkey bandit26@bandit.labs.overthewire.org  
  
*ONLINE SOLUTION:*  
Before logging into bandit 26, make the physical terminal on your screen very small, then log in.  
There should be a piece of text saying "More", where, if you follow that instruction, can now access vim by pressing the "v" on your keyboard.  
Now we can re-maximise the terminal.   
  
:set shell=/bin/bash  
:shell  
cat /etc/bandit`\`_pass/bandit26  

## Explanation
First, as the shell for the next level is different, we can just check the `passwd` file and grep the bandit26 shell. We get `/usr/bin/showtext`.  
We can access this by using the cat command. Observing this, we can see that the more command is used which will just display the text from the text.txt file.  
Looking the home directory, we can see that there is a sshkey, so if we take this out of the server and copy it over, we can then change the permissions and use this key to log into the next level (explained in bandit 14).  
However, as the problem states, the shell is different so we are instantly kicked out of the server. This is puzzling.  
  
This is where the online solution comes in, which highlights the "more" command we saw in that bash file initially.  
  
Now, that we are in vim, we can set the shell using the `:set` command, to our desired /bin/bash. Using the `:shell` command, we can now access the level normally.  
With the bandit26 permissions, we can just access the password file.  

## Password
s0773xxkk0MXfdqOfPRVr9L3jJBUOgCZ    

## Lesson Learnt
The shell is crucial for accessing servers, as if configured differently, can wildly alter the server.  
  
Credit for online solution: https://mayadevbe.me/posts/overthewire/bandit/level26/