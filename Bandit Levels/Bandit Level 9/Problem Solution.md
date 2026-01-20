## Problem
Read the data.txt file and find the line of text that only occurs once.

## Solution 
sort data.txt | uniq -u

## Explanation 
First the text needs to sorted in order for the "uniq" command to work as intended due to the limitation
of the detection of repeated lines having to be adjacent to one another. Then pipelining the "-u" from the uniq command
gives us the only unique line in the text file which means it only occurs once.

## Password 
4CKMh1JI91bUIZZPXDqGanal4xvAg0JM

## Lesson Learnt
The uniq command works in tandem with the sort command and pipelining can be done using the "|" so as to be able to 
do 2 commands on the same line.