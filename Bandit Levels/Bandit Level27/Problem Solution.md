## Problem
Grab the next password!    

## Solution
cat ./bandit27-do cat /etc/bandit`\`_pass/bandit27  

## Explanation
This is explained in bandit 20, where using this setuid binary file, we can act as user bandit27 and just grab the password.  

## Password
upsNCc7vzaRDx6oZC6GiR6ERwe1MowGB  

## Lesson Learnt
Once in the vim, you are required to use the forward slash (`\`) to access directories and files with a symbol within them, similar to what is taught at the beginning of bandit.  