## Problem
Submit the current level password into one of the ports in the range 31000-32000. The port must be listening and be able to speak SSL/TLS. 

## Solution
nc -zv localhost 31000-32000 2>&1 | grep "succeeded"  
openssl s_client -connect localhost:31790 **(-quiet)**  
(Paste current level password) (And then copy resulting RSA Private Key)  
touch sshkey17.private  
echo "(Insert RSA Private Key)" > sshkey17.private  
chmod 600 sshkey17.private  
ssh -i sshkey.private bandit17@bandit.labs.overthewire.org -p 2220  

## Explanation
I used the nc command to listen to desired port range, using the `-z` option which lists all ports which are listening, with `-v` option providing us with a more verbose result to see if there is any information that can be used to differentiate between the ports such as if they can speak SSL/TLS. No such information was uncovered unfortunately.  
With an extra use of the `2>&1` command, this command, again (explained in bandit level 7), will ensure the results given are then sent to where standard output messages ("&1") (A.K.A. stdout) are sent, instead of where the standard error messages (stderr) are normally sent. In other words, the stderr message will turn into stdout message so that we can utilise the `grep` command and only filter the results for the ports that we succeeded in listening to.  
Next, albeit inefficient, we use the `openssl s_client` command to speak to each port with SSL/TLS, then, the `-connect` command is used because an extra command was needed, the `-quiet` command. This command is needed ONLY if the current level password starts with a CONNECTED COMMAND character, which the password for my level, starts with the character "k", so "KEYUPDATE" was the response we would get everytime the password would be entered.  
Then inserting the current level password will prompt the server to respond with a RSA Private key, which the next steps for, are explained in previously completed bandit level 14.  

## Password
The next level can be accessed through the RSA Private key which was given.  
EReVavePLFHtFlFsjn3hyzMlvSuSAcRD (accessed after proceeding into the next level and going into /etc/bandit_pass/bandit17)  

## Lesson Learnt
The -connect command can be used to further customise the results we recieve such as the -quiet option.  
TIP: The use of turning the stderr messages into stdout form with the 2>&1 command so that the grep command can be used.