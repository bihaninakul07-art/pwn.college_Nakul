# PERCEIVING PERMISSIONS
This module tells us about the permissions in linux and how to acdess the files across different users
# CHANGING FILE OWNERSHIP
This challenge teaches us about ownership of flag and changing original file name into hacker

**FLAG**:```pwn.college{wv05vRctrKtzE0M8xc8DL8U56P6.QXxEjN0wCM2kzNzEzW}```
CODE:
```wsl
Connected!
hacker@permissions~changing-file-ownership:~$ chown hacker /flag
hacker@permissions~changing-file-ownership:~$ ls -1 /flag
/flag
hacker@permissions~changing-file-ownership:~$ ls -l /flag
-r-------- 1 hacker root 60 Oct 10 17:39 /flag
hacker@permissions~changing-file-ownership:~$ cat /flag
pwn.college{wv05vRctrKtzE0M8xc8DL8U56P6.QXxEjN0wCM2kzNzEzW}
```
# What I Learned
How to take ownership of the flag and retrieve it 

# Reference
pwn.college
# GROUPS AND FILES
This challenge teaches us how to own and group files them
**FLAG**:```pwn.college{g2sUadz8BwLzLKd9qEybBlrTxgX.QXxcjM1wCM2kzNzEzW}```
CODE:
```wsl
Connected!
hacker@permissions~groups-and-files:~$ chgrp hacker /flag
hacker@permissions~groups-and-files:~$ ls -l /flag
-r--r----- 1 root hacker 60 Oct 10 17:42 /flag
hacker@permissions~groups-and-files:~$ cat /flag
pwn.college{g2sUadz8BwLzLKd9qEybBlrTxgX.QXxcjM1wCM2kzNzEzW}
```
# What I Learned
How to own and group files them 

# Reference
pwn.college
# FUN WITH GROUPS
This challenge teaches us to use id command and have fun with the names
**FLAG**:```pwn.college{EtI4uNXgCHqnQ9Qr8SE6v4LG5_H.QXycjM1wCM2kzNzEzW}```
CODE:
```wsl
Connected!
hacker@permissions~fun-with-groups-names:~$ id -gn
grp11507
hacker@permissions~fun-with-groups-names:~$  chgrp "$(id -gn)" /flag
hacker@permissions~fun-with-groups-names:~$ ls -l /flag
-r--r----- 1 root grp11507 60 Oct 10 17:46 /flag
hacker@permissions~fun-with-groups-names:~$ cat /flag
pwn.college{EtI4uNXgCHqnQ9Qr8SE6v4LG5_H.QXycjM1wCM2kzNzEzW}
```
# What I Learned
How to use id command and have fun with names and usage of cgrp command

# Reference
pwn.college

# CHANGING PERMISSIONS
**FLAG**:```pwn.college{oT-u1XBnt3NomVD_GshNvpbnJDi.QXzcjM1wCM2kzNzEzW}```
CODE:
```wsl
Connected!
hacker@permissions~changing-permissions:~$ chmod o+r /flag
hacker@permissions~changing-permissions:~$ ls -l /flag
-r-----r-- 1 root root 60 Oct 10 17:48 /flag
hacker@permissions~changing-permissions:~$ cat /flag
pwn.college{oT-u1XBnt3NomVD_GshNvpbnJDi.QXzcjM1wCM2kzNzEzW}
```
# What I Learned
How to use chmod command and changing permissions

# Reference
pwn.college

# EXECUTABLE FILES
**FLAG**:```pwn.college{sDgw-f_sDN3Ft1sMLed-UbUz8YA.QXyEjN0wCM2kzNzEzW}```
CODE:
```wsl
Connected!
hacker@permissions~executable-files:~$  ls -l /challenge/run
-r--r--r-- 1 hacker hacker 32 Jan 14  2025 /challenge/run
hacker@permissions~executable-files:~$ chmod +x /challenge/run
hacker@permissions~executable-files:~$ ls -l /challenge/run
-r-xr-xr-x 1 hacker hacker 32 Jan 14  2025 /challenge/run
hacker@permissions~executable-files:~$ /challenge/run
Successful execution! Here is your flag:
pwn.college{sDgw-f_sDN3Ft1sMLed-UbUz8YA.QXyEjN0wCM2kzNzEzW}
```
# What I Learned
How to use execute files using chmod

# Reference
pwn.college
# THE-SUID-BIT
**FLAG**:```pwn.college{sJ-A0wfQlaZMEWoIFt6GW1YVSrC.QXzEjN0wCM2kzNzEzW}```
CODE:
```wsl
Connected!
hacker@permissions~the-suid-bit:~$ chmod u+s /challenge/getroot
hacker@permissions~the-suid-bit:~$ ls -l /challenge/getroot
-rwsr-xr-x 1 root root 155 Jan 14  2025 /challenge/getroot
hacker@permissions~the-suid-bit:~$ /challenge/getroot
SUCCESS! You have set the suid bit on this program, and it is running as root!
Here is your shell...
root@permissions~the-suid-bit:~# id
uid=0(root) gid=1000(hacker) groups=1000(hacker)
root@permissions~the-suid-bit:~# whoami
root
root@permissions~the-suid-bit:~# cat /root/flag 2>/dev/null || cat /flag 2>/dev/null
pwn.college{sJ-A0wfQlaZMEWoIFt6GW1YVSrC.QXzEjN0wCM2kzNzEzW}
# What I Learned
Just like previous challenge we learn how to play the game and understand the clues, etc

# Reference
pwn.college
