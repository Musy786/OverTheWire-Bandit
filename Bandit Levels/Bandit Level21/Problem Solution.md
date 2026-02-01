## Problem
In home directory, there is a setuid binary that will connect to localhost on a port you specify as a commandline arguement. From that connection, it reads the line of text within it and compares it to the previous level's password, sending you the password for the next level if it is correct.  

## Solution
echo -n "0qXahG8ZjOVMN9Ghs7iOWsCfZyXOUbYO" | nc -l -p 1234 &  
./suconnect 1234  

## Explanation
First, we need to create a temporary server and then insert the previous level's password into it. To do so, we can echo the password into a netcat server with a specifid port.  
The echo `-n` is just to ensure that the password is read on its own in a new line. The nc `-l` to listen to a specified port `-p`, which we have as port 1234. Ending off with the `&` option to allow the server to keep running in the background so that we can then connect to the server using the setuid binary instead of it just disconnecting as soon as we are done putting in the password, leaving the setuid binary to read nothing.  
Then execute the setuid binary file and specifiy the port we have already set up just now, in this case port 1234.  

## Password
EeoULMCra2q0dSkYj561DX7s1CpBuOBt  

## Lesson Learnt
Using the nc command, we can just make a temporary server with our own specified port by using the -l, -p, and & options to keep it running in the background. We can also pipeline anything into this server such as the echo we have done in this case.  
TIP: We can use the `jobs` command after running the first command line for this solution and you would see that this "job" is running in the background.  