In this room, I utilized nmap and hydra to discover open ports, vulnerabilities and exploit them. Here is the step by step
on how I was able to finish it.

1. First thing when trying to exploit a machine is by performing reconnaisance. I will be using active reconnaisance by using
   nmap. I issused this command nmap -sS -sV -O -sC -oN scan.nmap -p- 10.66.138.185. This scans all ports on the target
   machine also giving me their version and the operating system. The output will be stored on a file called snan.nmap for me
   to filter out results in the further steps. The scan will take a while 

Problem: What is the highest port number that is open and less than 10,000?
Solution: grep "open" scan.nmap
Problem: On port 80, what is the service version value?
Solution: grep "80" scan.nmap

2. Usernames eddie and quinn was given so the task is to discover their password. I used hydra to bruteforce their password
   on an ftp server. 
   command: hydra -l eddie -P /usr/share/wordlists/rockyou.txt ftp://10.66.138.185:10121 -V, since ftp is listening on a non
   default port, we have to specify which port its listening to which is 10121.

3. Log in ftp using cracked credentials, username=eddie password=softball. ftp 10.66.138.185 10121 and capture the flag



