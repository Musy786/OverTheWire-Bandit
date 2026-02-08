## Problem
Same as previous level. Git clone the repository given on your own local machine and find the password.  

## Solution
git clone ssh://bandit29-git@bandit.labs.overthewire.org:2220/home/bandit29-git/repo  
cd repo  
cat README.md  
*RESULT:*  
`# Bandit Notes`  
`Some notes for bandit30 of bandit.`  
  
`## credentials`  
  
`- username: bandit30`  
`- password: <no passwords in production!>`  
  
git branch -a  
*RESULT:*  
`* master`  
`  remotes/origin/HEAD -> origin/master`  
`  remotes/origin/dev`  
`  remotes/origin/master`  
`  remotes/origin/sploits-dev`  

git switch dev  
cat README.md  

## Explanation
First, we do the same initial steps as the previous level. Then we see that the `README.md` file says that there are no passwords in the production, which implies that there are other branches available. So there is production, which is main, and then usually there is a development branch, which in fact my git repository makes use of.  
Second, we should look at all the branches available using the `branch -a` command, with the "-a" option giving us all the branches. Observing the branches as shown above, there is a "dev" branch, as well as a "sploits-dev" branch.  
We can use the "git switch" command to switch over to another branch, which in this case we go over to the "dev" branch.  
Then we can read the "README.md" file and get the password.  

## Password
qp30ex3VLz5MDG1n91YowTv4Q8l7CDZL  

## Lesson Learnt
Branches are used for developing the code base in a safe environment without having to make changes to the main codebase. Leaving the main codebase usable, and using the additional branches to add features and fix bugs that can be added later on.  
It is extremely useful in lieu of collaboration as multiple people can work on different branches and then merge all their code together seamlessly. There can be merge conflicts however, in which case the better commit should be chosen, which would be decided by the two people's commits or a senior developer who could differentiate between the two.  
To avoid merge conflicts, three strategies can be implemented. 
Atomic commits, this means only making concise commits that make only one meaningful change. This makes it so that bugs that crop up can easily be identified and be fixed.  
Constant commits, this means any bugs that occur, can be fixed relatively easily due to the freshness of the code commited.  
Social cues (social change), this means not accepting commits that deal with a lot of code change, so it could be code that deals with bug x and also bug y, but that would be a risky commit as if some piece of the code results in a problem, it would be difficult to extract the piece of code that works and the code that doesn't. It would better to advise this person to not do so and only accept changes that are clear and meaningful.  