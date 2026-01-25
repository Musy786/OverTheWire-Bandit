## Solution 
scp -P 2220 bandit13@bandit.labs.overthewire.org:sshkey.private .  
bandit13@bandit.labs.overthewire.org's password:  
sshkey.private                                      100% 1679    18.2KB/s   00:00  
chmod 600 sshkey.private  
ssh -i sshkey.private bandit14@bandit.labs.overthewire.org -p 2220  

## Explanation 
The `scp -P` command is an openSSH secure file copy with the -P allowing to connect to the required port accessing the bandit level. At the end of the command, we colon the file name that we want to copy on to the terminal ending it with a "." to specify we want the file to be copied into the current directory at the terminal.  
This gives us access to the private key, leaving us with just altering the permissions (explained in the initial solution) and proceeding to use said key to access the next level.  

## Lesson Learnt
The scp command can be used to file copy when using an openSSH connection if a file is needed to be accessed outside of the game and into the terminal.