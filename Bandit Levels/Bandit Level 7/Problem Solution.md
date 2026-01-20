## Problem
Read the file that has three properties: owned by the user bandit7, owned by group bandit6, 
and 33 bytes in size. This file can be anywhere on the server

## Solution 
find / -user bandit7 -group bandit6 -size 33c 2>/dev/null
cat ./var/lib/dpkg/info/bandit7.password

## Explanation 
A single line was able to be used as we are going through all files from the route of the server using the 
slash command after the find command. Then the user owner is specified, along with the group and size.
As we are going through a lot of files, most of the files will come up with a file permission denied error,
therefore the command "2>/dev/null" is used. The "2" means standard errors, these results will then be sent to (">") 
a specific file that discards everything that is sent to it ("/dev/null"), leaving us with the desired file.

## Password 
morbNTDkSW6jIlUc0ymOdMaLnOlFVAaj

## Lesson Learnt
Using the "/" command allows us to go through all the files starting from the route, especially useful when using the 
"find" command. Also, the "2>/dev/null" is a standard method of removing error messages from the output so as to not
clutter the results so the desired files are shown clearly.