## Problem
Same as previous level. Git clone the repository given on your own local machine and find the password.   

## Solution
git clone ssh://bandit31-git@bandit.labs.overthewire.org:2220/home/bandit31-git/repo  
cat README.md  
*RESULT:*  
`This time your task is to push a file to the remote repository.`  
  
`Details:`  
    `File name: key.txt`  
    `Content: 'May I come in?'`  
    `Branch: master`  
  
cat .gitignore  
*RESULT:*  
`*.txt`  
  
touch key.txt  
echo 'May I come in?' > key.txt  

git add -f key.txt   
git commit -m "Adding key.txt file"  
*1st RESULT:*  
`Author identity unknown`  
  
`*** Please tell me who you are.`  
  
`Run`  
  
  `git config --global user.email "you@example.com"`  
  `git config --global user.name "Your Name"`  
  
`to set your account's default identity.`  
`Omit --global to set the identity only in this repository.`  
  
`fatal: unable to auto-detect email address (got 'root@ubuntu.(none)')`  

git config --global user.email "musy@gmail.com"  
git config --global user.name "musy"  
git commit -m "Adding key.txt file"  
*2nd RESULT:*  
`[master 3026d22] Adding key.txt file`  
 `1 file changed, 1 insertion(+)`  
 `create mode 100644 key.txt`  
  
git push  

## Explanation
First, we take a look at the README.md file to see that it looks like we must commit and push a text file, key.txt, to a remote repository.  
Before we move onto the next step, when observing all the files in the repo while checking for a README.md file, is a `.gitignore` file, which reading it gives us the result of `*.txt`, which means all text files, which when in this .gitignore file, means the git repository will ignore all and any attempts of pushing specfied information onto the repository, which in this case, is all text files, including the text file we want to push.  
Next, we create the desired text file. Now, we commit this text file by using the `git add -f` option, where anything that is specified after this, will be forcibly commited, disregarding any .gitignore files in the repository.  
Now, what we have to is configure our user email and user name, these can likely be anything (I did not use a my real gmail account). This has to done as, when we try to commit it the first time normally, we get a message saying permission denied and to use the `git config` command to do what we just did.  
So, configuring this will now allow us to commit the file, we also need to add a commit message, otherwise it will prompt us to do so which can also be done but this causes less hassle.  
Finally, using the `git push` command, we push all of our commits onto the remote repository, which then results in the giving of the password.  

## Password
3O9RfhqyAlVBEZpVb6LYStshZoqoSx5K  

## Lesson Learnt
That ".gitignore" files are crucial in github repositories as it keeps from committing possibly log files, temporary files, build artifacts, or personal files onto your repository. These files will induce confusion and unnecessary bloat to the repository.  
The "git add -f" option is for forcing commits that you know are needed for the repository.  
The "git push" command to push all commits made onto the main repository or master branch, if working from a, for example, development branch.  
The "git config" command is for setting your identity so that all work done can be properly attributed to us. It should be used when using any new machine. This command is also used for many other preferences such as making the initial branch for a repository and then naming it (usually "main") or for very niche configurations such as setting up git autocorrect to be enabled for minor spelling auto corrections when using commands in the terminal.  