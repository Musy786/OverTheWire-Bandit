## Problem
Read the data.txt file and perform a rotation of 13 positions for each character in the text file.

## Solution 
cat data.txt  
tr 'A-Za-z' 'N-ZA-Mn-za-m' <<< "Gur cnffjbeq vf 7k16JArUVv5LxVuJfsSVdbbtaHGlw9D4"  

## Explanation 
The tr command is used to translate or delete characters, in this case we want to translate each character by 13.
The A-Z and a-z is the desired range of characters that we want to rotate by 13 characters, both uppercase and lowercase.
The next part is what we want as the result of our rotation so as to show an example of what is desired, so the A will translate
to the letter N and the letter Z will translate to the letter M. Notice the N-Z instead of N-M, this is due to the fact that 
these two letters will have to had to loop around the alphabet to get to each other so the letter N needs to end off at the
letter Z and then loop around starting from the letter A all the way to the letter M so that letters such as Z can be rotated
appropriately.  
Then using the "<<<" followed by what was given from the text file, we can direct this translation to the desired target 
and translate this text into the desired password.

## Password 
7x16WNeHIi5YkIhWsfFIqoognUTyj9Q4

## Lesson Learnt
The tr command is useful for the translation and deletion of characters.