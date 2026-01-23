## Problem
Read the file that is in the hexdump format and that has been repeatedly compressed using various encrypting methods. 

## Solution 
xxd -r test.txt | gzip -d | bzip2 -d | gzip -d > test2  
mv test2 test2.tar  
tar -xf test2.tar  
mv data5.bin test3.tar  
tar -xf test3.tar  
bzip2 -d data6.bin  
mv data6.bin.out test4.tar  
tar -xf test4.tar  
mv data8.bin test5.gz  
gzip -d test5.gz  
cat test5  

## Explanation 
First, we are instructed to copy the file in the current directory and make a temporary directory in the tmp directory located in the root of the server, pasting our copy there.  
This is important, as to acquire this password, new files must be created and a trial and error method is also encouraged.  
With this, we start with using the `xxd -r` command to decrypt the hexdump file we start off with.  
Everytime we decrypt the file, we must make sure to use the `file` command so that it is clear what method of decryption is needed.  
The first line of the solution does 3 more decryptions by using pipelining and then directing this new file into a new one called test2. This could only be done after the fact as the file command would have needed to be used but for the solution's sake, it is presented as so.  
Now the file is in the tar format. To decrypt this, we need to rename the file using the `mv` command and altering the suffix with .tar so that the tar command can recognise the file as a tar file that needs to be extracted. Next, the `tar -xf` command is used, -x for extracting the tar file, and -f for specifying the file we want to extract.  
This creates a new file called data6.bin which is what happens whenever a decryption or extraction is done.  
Then from here the file is then decrypted using the methods described above leaving us with the password.  

## Password 
FO5dwFsc0cbaIiH0h8J2eUks2vdTDwAn

## Lesson Learnt
Pipelining is useful for when multiple operations can neatly placed into one line. Also, when decrypting a file, the file command is vital in knowing what decrypting method needs to used, along with the mv command to ensure the decrypting method being used recognises the file so it can be decrypted appropriately.