## Problem
Read a file that has three properties: human-readable, 1033 bytes in size, and not executable. This file is in 
the inhere directory along with numerous other files.

## Solution 
cd inhere  
find . -type f -size 1033c ! -executable  
cat maybehere07/.file2  

## Explanation 
Using the "find" command allows us to filter out the files using the set properties of the target file.
Starting with finding all (".") regular files ("-type f") with a byte size of 1033 ("-size 1033c") that is 
a non executable file ("! -executable"). 

## Password 
HWasnPhtq9AVKe0dmk45nxy20cvUa6EG

## Lesson Learnt
The "find" command has a ton of filters that can be utilised to pinpoint the location of certain files.