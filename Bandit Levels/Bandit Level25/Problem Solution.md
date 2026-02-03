## Problem
Submit the current level password and a secret 4 digit pincode to a daemon that is listening in on port 30002. The only way to retrieve the 4 digit pincode is through a bruteforce method.  
New connections each submission are not required.  

## Solution
mktemp -d    (/tmp/tmp.eKk0FLNcYU)  
touch script.sh  
nano script.sh  
*INSERTED INTO SCRIPT:*  
`#!/bin/bash`  
  
`pass=gb8KRRCsshuZXI0tUuR6ypOFjiZbf3G8`  
  
`for i in {0000..9999}`  
`do`  
`echo $pass $i >> results.txt`  
`done`  
  
`cat results.txt | nc localhost 30002 > answer.txt`  

chmod 777 script.sh   
./script.sh  
sort answer.txt | uniq -u  

## Explanation
Observing the problem, it looks like we will need to use the nc command to connect to the daemon in port 30002 and submit the current level password. However, a 4 digit code is also needed and that can only be retrieved through bruteforce.  
The bruteforce method consists of inputting in all 10000 combinations and then retrieving the password from the 4 digit code that worked.  
First, we need to make a bash script that can automate the process for us, so we make a temporary directory.  
Then we create the script. We use the for loop and echo the password along with `i`, which corresponds to the for loop going through all values from 0000 through to 9999, of which is then neatly placed into a text file, in this case "results.txt". This is done 10000 times.  
Then we read this file and connect to the designated port 30002, inputting line by line what we have just created in the answer.txt file, then putting all that feedback into another text file, in this case "answer.txt".  
We then make this script executable using the chmod command and then run the script. We can double check if this worked by using the ls command to see if the text files have been created.  
Finally, we use the sort command on the final text file, answer.txt, and then the uniq -u command (explained in bandit 9) to retrieve the one result which gave us the correct response, thus retrieving the password.  

## Password
iCi86ttT4KSNe1armKiwbQNmB3YJP3q4

## Lesson Learnt
TIP: From a lot of work debugging, the ">" and ">>" commands are different. The ">" will overwrite when redirecting output but the ">>" command will append to whatever is in the file. So on the 7th line, a ">" would not work because everytime we sent output of the password along with a new 4 digit code, it would then overwrite what was just already written leaving us with just the password and the code "9999" as the only line in the resulting text file.  