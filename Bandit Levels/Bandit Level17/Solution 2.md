## Solution
nmap -sV -T4 localhost -p 31000-32000  
openssl s_client -connect localhost:31790 **(-quiet)**  
(Same next steps as initial solution)  

## Explanation
The `nmap` command is used to listen to ports, the `-sV` option gives us the service of the port as well so differentiating between the ports will be viable due to the extra information of the service which directly shows if the port can speak SSL/TLS.  
Also, the `-T4` just makes it so that the operation is done quicker, as said in the nmap man page.  
Then with that, the same next steps can be used as in the initial solution.  

## Lesson Learnt
The nmap command can be used to specify the service of each port, such as if a port can speak SSL/TLS.  