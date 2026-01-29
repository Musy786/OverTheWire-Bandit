## Problem
Find the line that differs between the files password.new and password.old. The password is in password.new.

## Solution
diff passwords.new passwords.old

## Explanation
The `diff` command searches for the differences in between two files.  
The results shows two lines indicated with a greater than sign (`<`) first, and then with a lesser than sign (`>`) next, the first line shows what line is different in the **first** file provided (so passwords.new) and the second line is visa versa (passwords.old).  

## Password
x2gLTTjFwMOhQ8oWNbMN362QKxfRqGlO

## Lesson Learnt
The diff command is useful for finding differences between two files easily and the results need to be interpreted in terms of which file is provided in order of physically first to last.