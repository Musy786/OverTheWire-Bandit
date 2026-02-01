## Problem
Look in /etc/cron.d/ for the configuration and see what command is being executed. This program is running automatically at regular intervals from **cron**, the time-based scheduler.  

## Solution
cat /etc/cron.d/cronjob_bandit22  
*RESULT:*  
`@reboot bandit22 /usr/bin/cronjob_bandit22.sh &> /dev/null`  
``* * * * *` bandit22 /usr/bin/cronjob_bandit22.sh &> /dev/null``  
  
cat /usr/bin/cronjob_bandit22.sh  
*RESULT:*  
`#!/bin/bash`  
`chmod 644 /tmp/t7O6lds9S0RqQh9aMcz6ShpAoZKF7fgv`  
`cat /etc/bandit_pass/bandit22 > /tmp/t7O6lds9S0RqQh9aMcz6ShpAoZKF7fgv`  
  
cat /tmp/t7O6lds9S0RqQh9aMcz6ShpAoZKF7fgv  

## Explanation
First, we need to look at the cron configuration that is being executed.  
So we cat into it and get those results above. It means every time the system reboots and every minute, the bash script is run as the user bandit22, the standard output and standard error created from the "cronjob_bandit22.sh" bash script, is then sent to a void location (/dev/null), discard all output so no messages are displayed or logged.  
So from here, we cat into the bash script to see what exactly is being executed. The results show that the permissions for a certain temp file are altered (chmod) and allows for the owner to read and write the file created, the group to be able to read it, and the user to be able to read it.  
The password for the next level is then sent to the temp file that we are able to read.  
Finally, we proceed to just read the temp file.  

## Password
tRae0UfB9v0UzbCdn9cY0gQnds9GF58Q  

## Lesson Learnt
Cron is used for doing jobs at regular intervals. For example, sending the results of a certain file to a void location every single minute.  