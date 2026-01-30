## Problem
Use the setuid binary in the homedirectory to gain access to the place where the password is usually located (/etc/bandit_pass).

## Solution
stat -c "%a %U:%G %n" bandit20-do  
./bandit20-do cat /etc/bandit_pass/bandit20  

## Explanation
The `stat` command displays the file or file system status, with the `-c` option that is just for format purposes to make the results readable.  
The `%a` is to display the permission bits, `%U:%G` to display the user and the group of the file, `%n` to display the file name. This gives us a clear display of the permissions and the name of the user and group of the file that we want to know about.  
Then we can execute the binary setuid file.  
A suid makes a program run as the owner, in this case bandit20, so we can utilise the file by executing it, accessing the file where the password is stored for this level as we are now recognised as the owner of the file.  

## Password
0qXahG8ZjOVMN9Ghs7iOWsCfZyXOUbYO  

## Lesson Learnt
A suid is a special permission that allows a program to run with the privileges of its owner rather than current user executing. It replaces the "x" is in the user permissions with a "s" as a visual that the suid is working.  