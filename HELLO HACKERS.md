# Intro to Command
*Module:* Hello Hackers (pwn.college)
**Date:** 2025-09-22

## My solve
**Flag:** 'pwn.college{wkh85SGn5dETq3x8q0ydcrhZfup.QX3YjM1wCM2kzNzEzW}`

## Steps
1. Logged in to the dojo using SSH.
2. Typed `hello` at the prompt.
3. Got the flag from the output.

## Explanation
This challenge was about running a simple command in the shell. Typing `hello` printed the flag. It helped me get comfortable with running commands remotely.

## What I learned
- How to connect to pwn.college via SSH.
- How basic commands work in Linux.
- How flags are displayed after running a program.

## References
Did not use any references for this challenge. 


# Intro to Arguments
*Module:* Hello Hackers (pwn.college)
**Date:** 2025-09-22

## My solve
**Flag:** `pwn.college{MzOcALZ1cBAUEyOrynRWBIMNF4P.QX4YjM1wCM2kzNzEzW}`

## Steps
1. Logged in via SSH.
2. Typed `hello hackers` at the prompt.
3. Copied the flag from the output.

## Explanation
This challenge showed how commands can take arguments. Here, `hackers` was an argument to `hello`. The shell splits what you type into the command and arguments, and the program returned the flag based on that.

## What I learned
- How to pass arguments to commands.
- How Linux parses command + arguments.
- That small differences (like case) can matter.

## References
Did not use any references for this challenge.


# Command History
*Module:* Hello Hackers (pwn.college)
**Date:** 2025-09-22

## My solve
**Flag:** `pwn.college{M18u5dM99G90fFh6ytkJKk6nCLP.0lNzEzNxwCM2kzNzEzW}`

## Steps
1. Logged in via SSH.
2. Pressed the up arrow key in the terminal to scroll through previous commands.
3. Found the flag in the history and copied it.

## Explanation
This challenge taught how the shell saves command history. Instead of retyping, we can scroll through past commands. The flag was stored as one of the previous commands, so using the arrow keys made it easy to retrieve.

## What I learned
- How to use command history in Linux.
- That you can reuse previous commands instead of typing everything again.
- Flags can sometimes be hidden in history.

## References
Did not use any references for this challenge.
