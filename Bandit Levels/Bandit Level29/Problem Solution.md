## Problem
Same as previous level. Git clone the repository given on your own local machine and find the password.  

## Solution
mktemp -d  
git clone ssh://bandit28-git@bandit.labs.overthewire.org:2220/home/bandit28-git/repo  
cd repo  
cat README.md  
*RESULT:*  
`# Bandit Notes`  
`Some notes for level29 of bandit.`  
  
`## credentials`  
  
`- username: bandit29`  
`- password: xxxxxxxxxx`  
  
git log  
*RESULT:*  
`...`  
`commit d0cf2ab7dd7ebc6075b59102a980155268f0fe8f`  
`Author: Morla Porla <morla@overthewire.org>`  
`Date:   Tue Oct 14 09:26:19 2025 +0000`  
  
`    add missing data`  
`...`  
  
git show d0cf2ab7dd7ebc6075b59102a980155268f0fe8f  

## Explanation
First we do the same initial steps as the previous level. Then we can read the README.md file to see how to get the password.  
The password is not shown, instead it is shown as several asterisks characters.  
Thus, we should use the `git log` command to see the commits that have been made to the repository in hopes that we can observe if an initial password was indeed entered into the file.  
There have been 3 commits made to the repository. As shown above, we can observe that there is a commit called "add missing data", which we can infer where the inital password was entered in plain text.  
To read into this, we can use the `git show` command, followed by the hash of the commit, so at the top of the commit, there will be a line with "commit" then followed by is the hash. Giving us the psasword.  

## Password
4pT1t5DENaYuqnqvadYs1oE4QLCdjmJ7  

## Lesson Learnt
The "git log" command can be used to see the history of commits on a file, and the "git show" command can be used to show the contents of that commit, only needing the hash that will be shown at the top of the commit information from the git log results.  