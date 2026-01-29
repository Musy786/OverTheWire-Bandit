## Problem
Read the readme file in the homedirectory of the level. However, the .bashrc file does not allow for you to ssh into the level and will immediately log you out with a "byebye" message.  

## Solution
ssh bandit18@bandit.labs.overthewire.org -p 2220 cat readme  

## Explanation
The `ssh` command can also be used as a command line so instead of using the `cat` command **after** entering the level, we can just place in the command prior.  
This solves the problem of not being able to enter the level and then perform the command.  

## Password
cGWpMaKXVwDUNgPAVJbWYuGHVn9zl3j8  

## Lesson Learnt
SSH can be used as a command line also.  