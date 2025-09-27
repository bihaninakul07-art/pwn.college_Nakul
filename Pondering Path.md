# The Root   
## My solve
**Flag:** `pwn.college{YJVxGwF5wpCc6cNzz9xs56QGt7X.QX4cTO0wCM2kzNzEzW}`

## How I solved it
The challenge description mentioned that a binary called `pwn` was placed in the root directory `/`. Since the level was about absolute paths, I realized the way to run it was to type `/pwn`. As soon as I did that, the flag was printed.

## Why this works
Absolute paths always start with `/`, which is the filesystem root. By typing `/pwn`, the shell looks exactly in `/` and runs the binary there, without relying on the current directory or PATH.

## What I learned
I learned the difference between absolute and relative paths. Writing `/pwn`, `./pwn`, or just `pwn` can mean completely different things depending on where I am in the filesystem.

## References
Did not use any references for this challenge.

# Program and absolute paths
## My solve
**Flag:** `pwn.college{Qrt3xpbnb8K3DOoCnqXWzq9j09N.QX1QTN0wCM2kzNzEzW}`

## How I solved it
This challenge reinforced the concept of absolute paths. The description mentioned a program placed somewhere in `/challenge`. I realized that to run it, I just needed to type the full path from root. Once I entered `/challenge/run` at the prompt, the flag appeared instantly. It was straightforward because the level focused on understanding absolute paths.

## Why this works
An absolute path begins with `/` and points directly to a file or directory from the root. Using `/challenge/run` makes sure the shell executes exactly that binary, without depending on the current working directory or PATH.

## What I learned
I learned to distinguish between absolute and relative paths and why absolute paths are useful for running programs reliably. It also showed me that just knowing the program name isn’t enough if you aren’t in the right location or if it isn’t in PATH.

## References
Did not use any references for this challenge.

# Position Thyself
Navigate to the correct directory using cd before executing the /challenge/run program.

## My solve
**Flag:** `pwn.college{85uwAmBgwxsl33MAO9vkxONYSOa.QX2QTN0wCM2kzNzEzW}`

I first tried running /challlenge/run but got "No such file or directory" due to a typo. Correcting it to /challenge/run, the program said I wasn't in the correct directory. Using cd /etc, I navigated to the required directory and re-ran the program. The challenge executed successfully, producing the flag.


```
WSL terminal session:

hacker@paths~position-thy-self:~$ cd/etc
bash: cd/etc: No such file or directory
hacker@paths~position-thy-self:~$ /challenge/run
Incorrect...
You are not currently in the /sys directory.
Please use the cd utility to change directory appropriately.
hacker@paths~position-thy-self:~$ cd /sys
hacker@paths~position-thy-self:/sys$ /challenge/run
Correct!!!
/challenge/run is an absolute path, invoked from the right directory!
Here is your flag:
pwn.college{85uwAmBgwxsl33MAO9vkxONYSOa.QX2QTN0wCM2kzNzEzW}
```


## What I learned
I learned how absolute paths work in Linux and the importance of being in the correct current working directory (cwd) when executing a program. This reinforced the concept that the current directory affects relative and absolute path resolution.

## References
Linux cd command documentation; pwn.college Pondering Paths tutorial.

# Position Elsewhere
Navigate to another specified directory using cd before executing /challenge/run.

## My solve
**Flag:** `pwn.college{URCofR8qt1xdg83Ho1Qyf8edUO0.QX3QTN0wCM2kzNzEzW}`

Initially ran /challenge/run from the home directory and received a message about being in the wrong directory. I used cd /var to move to the correct location, then executed /challenge/run. This successfully returned the flag.
```
WSL terminal session:

Connected!
hacker@paths~position-elsewhere:~$ /challenge/run
Incorrect...
You are not currently in the /etc/apt/sources.list.d directory.
Please use the cd utility to change directory appropriately.
hacker@paths~position-elsewhere:~$ cd /etc/apt/sources.list.d
hacker@paths~position-elsewhere:/etc/apt/sources.list.d$ /challenge/run
Correct!!!
/challenge/run is an absolute path, invoked from the right directory!
Here is your flag:
pwn.college{URCofR8qt1xdg83Ho1Qyf8edUO0.QX3QTN0wCM2kzNzEzW}
```
## What I learned
This reinforced the concept of absolute paths and that /challenge/run must be invoked from the directory the program expects. Different challenges can require navigating to different directories.

## References
Linux cd manual; pwn.college tutorials.

# Position Yet Elsewhere
Navigate to a deeper directory before running /challenge/run.

## My solve
**Flag:** `pwn.college{g2jMZC-a0XeAkGAs4U7CcNCmDZI.QX4QTN0wCM2kzNzEzW}`

Running /challenge/run initially produced an error about being in the wrong directory. Using the hint, I navigated to /usr/share/zoneinfo/posix/Asia and executed the program successfully to get the flag.
```
WSL terminal session:

Connected!
hacker@paths~position-yet-elsewhere:~$ /challenge/run
Incorrect...
You are not currently in the /usr/share/doc directory.
Please use the cd utility to change directory appropriately.
hacker@paths~position-yet-elsewhere:~$ cd /usr/share/doc directory
bash: cd: too many arguments
hacker@paths~position-yet-elsewhere:~$ cd/usr/share/do
bash: cd/usr/share/do: No such file or directory
hacker@paths~position-yet-elsewhere:~$ cd /usr/share/doc
hacker@paths~position-yet-elsewhere:/usr/share/doc$ /challenge/run
Correct!!!
/challenge/run is an absolute path, invoked from the right directory!
Here is your flag:
pwn.college{g2jMZC-a0XeAkGAs4U7CcNCmDZI.QX4QTN0wCM2kzNzEzW}
```
## What I learned
Practiced navigating through nested directories and understood how absolute paths are crucial when programs expect to be run from specific locations.

## References
Linux filesystem hierarchy documentation; pwn.college.

# Implicit Relative Paths From /
Run /challenge/run using a relative path instead of an absolute path.

## My solve
**Flag:** `pwn.college{wZMUNp4CfghLEIg-tSzn16hyTV7.QX5QTN0wCM2kzNzEzW}`

Started in / and used the relative path challenge/run instead of the absolute /challenge/run. Executing the command produced the flag.
```
WSL terminal session:

hacker@paths~implicit-relative-paths-from-:~$ cd /
hacker@paths~implicit-relative-paths-from-:/$ challenge/run
Correct!!!
challenge/run is a relative path, invoked from the right directory!
Here is your flag:
pwn.college{wZMUNp4CfghLEIg-tSzn16hyTV7.QX5QTN0wCM2kzNzEzW}
```
## What I learned
Understood relative paths and how they are resolved from the current working directory. Learned that relative paths don’t need to start with /.

## References
Linux path resolution documentation; pwn.college tutorials.

# Explicit Relative Paths From /
Run /challenge/run with a relative path that explicitly starts with .

## My solve
**Flag:** `pwn.college{4H17qPblTppslN49P8yuFB_aXst.QXwUTN0wCM2kzNzEzW}`

Executed ./challenge/run from / to explicitly indicate the current directory. This satisfied the challenge's requirement to use . for relative paths.
```
WSL terminal session:

Connected!
hacker@paths~explicit-relative-paths-from-:~$ cd /
hacker@paths~explicit-relative-paths-from-:/$ ./challenge/run
Correct!!!
./challenge/run is a relative path, invoked from the right directory!
Here is your flag:
pwn.college{4H17qPblTppslN49P8yuFB_aXst.QXwUTN0wCM2kzNzEzW}
```
## What I learned
Learned the significance of . in Linux paths, explicitly referencing the current directory. Also learned Linux safety measures prevent executing “naked” programs in the current directory by default.

## References
Linux file path documentation; pwn.college.

# Implicit Relative Paths
Run /challenge/run from the /challenge directory using relative path.

## My solve
**Flag:** `pwn.college{cjkYmFP9bNx7tqXxevV2g6e9vBD.QXxUTN0wCM2kzNzEzW}`

Navigated to /challenge and ran ./run to invoke the program correctly from the current directory. Flag returned successfully.
```
WSL terminal session:

Connected!
hacker@paths~implicit-relative-path:~$ cd /challenge
hacker@paths~implicit-relative-path:/challenge$ ./run
Correct!!!
./run is a relative path, invoked from the right directory!
Here is your flag:
pwn.college{cjkYmFP9bNx7tqXxevV2g6e9vBD.QXxUTN0wCM2kzNzEzW}
```
## What I learned
Practiced running programs using relative paths from within the target directory. Reinforced why Linux does not allow running programs from the current directory automatically without ./.

## References
Linux relative path documentation; pwn.college tutorials.

# Home Sweet Home
Use /challenge/run to write a flag to a file in your home directory using a short absolute path.

## My solve
**Flag:** `pwn.college{MCWFZimJ19gy3mh2AfZzchncdXX.QXzMDO0wCM2kzNzEzW}`

Ran /challenge/run ~/a to write the flag to the file /home/hacker/a using an absolute path inside my home directory. The program output the flag successfully.
```
WSL terminal session:

Connected!
hacker@paths~home-sweet-home:~$ /challenge/run ~/n
Writing the file to /home/hacker/n!
... and reading it back to you:
pwn.college{MCWFZimJ19gy3mh2AfZzchncdXX.QXzMDO0wCM2kzNzEzW}
```
## What I learned
Learned about the ~ shorthand for home directories, writing files using absolute paths, and the constraints of short paths for challenge programs.

## References
Bash home directory shorthand documentation; pwn.college.
