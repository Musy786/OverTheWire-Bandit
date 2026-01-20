## Problem
Read the data.txt file and find the password which is preceed by several "=" characters.

## Solution 
strings data.txt | grep ===

## Explanation 
The "strings" command allows us to go through every string in the text file, which then allows us to grep
the key character "=". 

## Password 
FGUW5ilLVJrxX9kMYMmlN4MgbpfMiqey

## Lesson Learnt
The strings command allows us to see every string in a file. Grep is used in tandem with other commands
to find specific keywords that come from the results of the other command used.