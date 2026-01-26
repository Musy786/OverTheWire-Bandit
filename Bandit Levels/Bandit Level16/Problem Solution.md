## Problem
Submit the current level's password in to localhost in port 30001 using a simple SSL/TLS encryption.

## Solution
openssl s_client localhost:30001
(Paste in current level password)

## Explanation
The `openssl` command is used as a command line program for various crptography functions such as SSL/TLS.  
The `s_client` command allows for the use of a simple secure SSL/TLS connection to the service.  
Then we paste in the current password for the level and the host responds with the password for the next level.  

## Password
kSkvUpMQ7lBYyCM4GBPvCvT1BfWRy0Dx

## Lesson Learnt
The openssl command is useful for when a cryptography method is required.