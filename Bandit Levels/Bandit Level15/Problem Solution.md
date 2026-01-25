## Problem
Use the password for this level and submit that into localhost 30000.

## Solution 
cat /etc/bandit_pass/bandit14  
nc localhost 30000  
(Paste the password retrieved from reading the file from the first command)  

## Explanation 
The password location for this level was stated in the previous level but was not accessible due to the restricted permissions, but now we can retrieve it.  
With this password, we are instructed to use the local host 30000 and then use the password we just retrieved and paste that in.  
It then responds with the password.  

## Password 
8xCjnmgoKbGLhHFAZlGE5Tmu4M2tKJQo

## Lesson Learnt
The nc command is useful for accessing different connections when needed.