## Problem
Look into cron script that is being run and look at what needs to be done to get to the next level.  

## Solution
cat /etc/cron.d/cronjob_bandit23  
cat /usr/bin/cronjob_bandit23.sh  
*RESULT:*  
`#!/bin/bash`  
`myname=$(whoami)`  
`mytarget=$(echo I am user $myname | md5sum | cut -d ' ' -f 1)`  
`echo "Copying passwordfile /etc/bandit_pass/$myname to /tmp/$mytarget"`  
  
echo I am user bandit23 | md5sum | cut -d ' ' -f 1  
*RESULT:*  
`8ca319486bfbbc3663ea0fbe81326349`  
  
cat /tmp/8ca319486bfbbc3663ea0fbe81326349  
*RESULT:*  
`0Zf11ioIjMVN551jX3CmStKLYqjk54Ga`  

## Explanation
First, we need to access the cron job that be is being run, which in similar familiar fashion, directed us to the bash file "cronjob_bandit23.sh".  
Interpreting the bash file, we can see that the `mytarget` variable is the key to accessing the file for the next level's password.  
So we just copy the echo command that the mytarget variable is using so as shown in the next command used, I place in the name "bandit23" (because that is the name for the next level).  
The result as shown, we can use to know what the name of the tmp file we need to access is, which again is shown in the next command, finally giving us the password.  

## Password
0Zf11ioIjMVN551jX3CmStKLYqjk54Ga  

## Lesson Learnt
Simple level.  