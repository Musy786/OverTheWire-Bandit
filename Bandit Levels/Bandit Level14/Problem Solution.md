## Problem
Use the sshkey.private to access the next level.

## Solution 
cat sshkey.private  
touch test.txt  
echo "(Insert Contents of the sshkey.private here)" > test.txt  
ls -la  
chmod 600 test.txt  
ssh -i test.txt bandit13@bandit.labs.overthewire.org -p 2220  

## Explanation 
First, we need to copy the sshkey.private and then exit out of the level. Now from here, we create a new file and echo in the key we just copied.  
When using the `ls -la` command, we need to confirm what permissions our new file has, which currently is -rw-r--r--. This means users from our group and any user can read this private key which is not good as it is supposed to be a private key which can only be read by the user.  
Hence, the `chmod 600` command is used, chmod is a command that can change the permissions of a file and the 600 specifies what permissions need to be changed, which in this case the 600 means readable and writable for only the creator, and 0 permissions for the other two, ensuring that this in fact is a private key.  
With this, we can use an extended command of the ssh command, `ssh -i` which means to identify a file, which in this case will have the effect of using the private key we copied initially to finally let us into the next level.

## Password 
The sshkey.private was the password for the level which is directly used to progress to next level.

## Lesson Learnt
The chmod command is used to change permissions and this also uses octal numbers.  
Tip: Using your fingers from one hand, you can effectively understand how to use the octal numbers. Exclude your thumb and ring finger, starting from pinky is read, write, then execute with the index finger. Starting from index finger, it holds the value of 1, 2, then 4 with the pinky. So for a file to have read and write permissions you do 2 + 4, which is the pinky and middle finger.