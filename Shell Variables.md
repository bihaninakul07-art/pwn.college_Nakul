# Variables — Full Module Writeups

## Printing Variables
What the challenge asks: Print the value stored in the variable FLAG.

**Flag:** `pwn.college{kMgOeQOnQ1F1LgsYASJM_8rtAUW.QX3UTN0wCM2kzNzEzW}`
```
Connected!
hacker@variables~printing-variables:~$ echo $FLAG
pwn.college{kMgOeQOnQ1F1LgsYASJM_8rtAUW.QX3UTN0wCM2kzNzEzW}
```
### My solve
Used echo $FLAG to print the variable.

### What I learned
$VAR expands to the value stored in the variable VAR.

### References
Bash variable expansion docs.

---

## Setting Variables
What the challenge asks: Set PWN to COLLEGE and print it to get the flag.

**Flag:** `pwn.college{wU0EuHILn5fK_1NodJolu7lsOZl.QX5UTN0wCM2kzNzEzW}`
```
Connected!
hacker@variables~setting-variables:~$ PWN=COLLEGE
hacker@variables~setting-variables:~$ echo "$PWN"
COLLEGE
You've set the PWN variable properly! As promised, here is the flag:
pwn.college{wU0EuHILn5fK_1NodJolu7lsOZl.QX5UTN0wCM2kzNzEzW}
```
### My solve
Assigned PWN=COLLEGE and echoed it.

### What I learned
Variable assignment uses = with no spaces; $VAR is used to access it.

### References
Bash variable assignment docs.

---

## Multi-word Variables
What the challenge asks: Set PWN to "COLLEGE YEAH" including spaces.

**Flag:** `pwn.college{Ac5Ueay45J20FkewbVNyCfK0bTW.QXwYTN0wCM2kzNzEzW}`
```
Connected!
hacker@variables~multi-word-variables:~$ PWN="COLLEGE YEAH"
hacker@variables~multi-word-variables:~$ echo "$PWN"
COLLEGE YEAH
You've set the PWN variable properly! As promised, here is the flag:
pwn.college{Ac5Ueay45J20FkewbVNyCfK0bTW.QXwYTN0wCM2kzNzEzW}
```
### My solve
Used quotes to store multi-word values.

### What I learned
Quotes allow spaces in variable values.

### References
Bash quoting docs.

---

## Exporting Variables
What the challenge asks: Export PWN so child processes can access it; set COLLEGE locally.

**Flag:** `pwn.college{8uyoBQqnSTzQ_eR6QBpkOLL8F8W.QXyYTN0wCM2kzNzEzW}`
```
Connected!
hacker@variables~exporting-variables:~$ export PWN=COLLEGE
You've set the PWN variable to the proper value!
hacker@variables~exporting-variables:~$ COLLEGE=PWN
You've set the PWN variable to the proper value!
You've set the COLLEGE variable to the proper value!
hacker@variables~exporting-variables:~$ /challenge/run
CORRECT!
You have exported PWN=COLLEGE and set, but not exported, COLLEGE=PWN. Great
job! Here is your flag:
pwn.college{8uyoBQqnSTzQ_eR6QBpkOLL8F8W.QXyYTN0wCM2kzNzEzW}
```
### My solve
Exported PWN and ran /challenge/run with the proper local variable COLLEGE.

### What I learned
export VAR makes the variable available to child processes.

### References
Bash export docs.

---

## Printing Exported Variables
What the challenge asks: Print all exported variables to find FLAG.

**Flag:** `pwn.college{4fH-tiAVORWQ7afuPxXrvP8842L.QX4UTN0wCM2kzNzEzW}`
```
hacker@variables~printing-exported-variables:~$ printenv FLAG
pwn.college{4fH-tiAVORWQ7afuPxXrvP8842L.QX4UTN0wCM2kzNzEzW}
```
### My solve
Used printenv FLAG to access exported variables.

### What I learned
printenv lists exported environment variables.

### References
Bash printenv docs.

---

## Storing Command Output in Variables
What the challenge asks: Store the output of /challenge/run into PWN.

**Flag:** `pwn.college{A-70V7nOXV7TJWt6i6EaqAa4INT.QX1cDN1wCM2kzNzEzW}`
```
Connected!
hacker@variables~storing-command-output:~$ PWN=$(/challenge/run)
Congratulations! You have read the flag into the PWN variable. Now print it out
and submit it!
hacker@variables~storing-command-output:~$ export PWN
hacker@variables~storing-command-output:~$ printenv PWN
pwn.college{A-70V7nOXV7TJWt6i6EaqAa4INT.QX1cDN1wCM2kzNzEzW}
```
### My solve
Used $(command) to capture stdout into a variable.

### What I learned
Command substitution VAR=$(command) stores program output in a variable.

### References
Bash command substitution docs.

---

## Reading Input into Variables
What the challenge asks: Use read to set PWN to COLLEGE.

**Flag:** `pwn.college{cEOn-FjfRWq-F0_Dn5_1Vy4sFVX.QX4cTN0wCM2kzNzEzW}`
```
Connected!
hacker@variables~reading-input:~$ read -p "Enter value: " PWN
Enter value: COLLEGE
You've set the PWN variable properly! As promised, here is the flag:
pwn.college{cEOn-FjfRWq-F0_Dn5_1Vy4sFVX.QX4cTN0wCM2kzNzEzW}
```
### My solve
Used read -p to take input into a variable.

### What I learned
read VAR reads standard input into a variable; -p adds a prompt.

### References
Bash read docs.
# Reading Files

## My solve
**Flag:** `pwn.college{4rbLd6hR9wuv0aOXLjUZNuSVHzo.QXwIDO0wCM2kzNzEzW}`

```
Connected!
hacker@variables~reading-files:~$ read PWN < /challenge/read_me
You've set the PWN variable properly! As promised, here is the flag:
pwn.college{4rbLd6hR9wuv0aOXLjUZNuSVHzo.QXwIDO0wCM2kzNzEzW}
```
## Incorrect tangents I went on
None

## What I learned
Learned how to read a file by redirecting the output to input

## References 
No outside reference used
