## Problem
There is a git repository at ssh://bandit27-git@bandit.labs.overthewire.org/home/bandit27-git/repo via the port 2220. The password to enter is the same for the current level.  
From your **local machine** (not the overthewire machine), clone the repository and find the password. Git needs to be installed locally on your machine.  

## Solution
mktemp -d  
git clone ssh://bandit27-git@bandit.labs.overthewire.org:2220/home/bandit27-git/repo  
cd repo  
cat README  

## Explanation
First, we must understand that we need to do this on our own local machine instead of in a temp file in the overthewire machine, because this gives us an error with us not being in the correct port, when we clearly are.  
Thus, we in our own local machine (I used killercoda ubuntu terminal), make a temporary directory and git clone the repository given to us, with a slight change where right after we input the server name, we end with a `..:2220` to specify the port given to us.  
Then we cd into the only directory made in the current directory, leading us into the `README` text file, which we can then proceed to use the cat command to retrieve the password inside of it.  

## Password
Yz9IpL0sBcCeuG7m9uQFt8ZNpS4HZRcN

## Lesson Learnt
Adding the :2220 to specify the port at the end of the server name. I used git clone to actually make this repository in the first place so I was already informed on this method so it did not take long.  