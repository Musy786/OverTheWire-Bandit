## Problem
Same as previous level. Git clone the repository given on your own local machine and find the password.   

## Solution
git clone ssh://bandit30-git@bandit.labs.overthewire.org:2220/home/bandit30-git/repo  
git tag  
git show secret  

## Explanation
This level gave us no clues, with the README.md file saying that this is an empty file...  
There is one command we can try, which is the `git tag` command. This command marks specific points in the version history of the repository that are important.  
With this, we can see a tag called "secret", and now using the git show command we can observe the secret, which gives us the password.   

## Password
fb5S2xb7bRyFmAvQYQGEqsbhVyJqhnDy  

## Lesson Learnt
Git tag is yet another command that can be used to mark specific points of the version history of a repository that are deemed important.  
This is used for saving builds of the codebase as problems may arise during development which could lead to having to rollback changes to the most recent usable build so that users are not affected too much. For example, a version number (i.e V1.0).  