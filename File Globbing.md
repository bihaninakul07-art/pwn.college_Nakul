# Bash Globbing and Tab Completion — Full Module Writeups

# Globbing Basics

## matching-with-asterisk
**Flag:** `pwn.college{AaOl26mwwAM7xpp0PHxPeRX-j_L.QXxIDO0wCM2kzNzEzW}
```

WSL terminal session:
```wsl
hacker@globbing~matching-with-:~$ cd /ch*
hacker@globbing~matching-with-:/challenge$ /challenge/run
You ran me with the working directory of /challenge! Here is your flag:
pwn.college{AaOl26mwwAM7xpp0PHxPeRX-j_L.QXxIDO0wCM2kzNzEzW}
```

### My solve
Used the `*` wildcard to match `/challenge` with `/ch*` for `cd`. Then ran `/challenge/run` to get the flag.

### What I learned
`*` matches any sequence of characters (except leading `.` or `/`). Useful to shorten commands or match multiple files.

---

## matching-with-question-mark
**Flag:** `pwn.college{E6dSyYKng-D6bVfo4nbZ00cgyoL.QXyIDO0wCM2kzNzEzW}`

WSL terminal session:
```wsl
hacker@globbing~matching-with-:~$ cd /?ha??enge
hacker@globbing~matching-with-:/challenge$ /challenge/run
You ran me with the working directory of /challenge! Here is your flag:
pwn.college{E6dSyYKng-D6bVfo4nbZ00cgyoL.QXyIDO0wCM2kzNzEzW}
```

### My solve
Used `?` as a single-character wildcard to match each character in `/challenge`.

### What I learned
`?` matches exactly one character. Useful for precise matching when filenames differ by a few letters.

---

## bracket-globbing
**Flag:** `pwn.college{U_mOh2zZEioAlCrPfnrLiLKfp9C.QXzIDO0wCM2kzNzEzW}`

WSL terminal session:
```wsl
root@LAPTOP-FOONIF69:~# ssh -i ./key hacker@dojo.pwn.college
Connected!
hacker@globbing~matching-with-:~$ cd /challenge/files
hacker@globbing~matching-with-:/challenge/files$ /challenge/run file_[bash]
You got it! Here is your flag!
pwn.college{U_mOh2zZEioAlCrPfnrLiLKfp9C.QXzIDO0wCM2kzNzEzW}
```

### My solve
Used `[bash]` to match one character from the set in file names.

### What I learned
`[]` allows limited wildcarding — matches any one character inside the brackets.

---

## absolute-path-bracket-globbing
**Flag:** `pwn.college{0FmuVTkL7i0lkAfj1soA0Pu9s_u.QX0IDO0wCM2kzNzEzW}`

WSL terminal session:
```wsl
Connected!
hacker@globbing~matching-paths-with-:~$ /challenge/run /challenge/files/file_[absh]
You got it! Here is your flag!
pwn.college{0FmuVTkL7i0lkAfj1soA0Pu9s_u.QX0IDO0wCM2kzNzEzW}
```

### My solve
Used bracket globbing on absolute paths to match `/challenge/files/file_b`, `file_a`, `file_s`, and `file_h`.

### What I learned
Globs can be used with full paths, not just filenames.

---

## multiple-globs
**Flag:** `pwn.college{8Yq3JkluFmjh21VYhF_7ajZxgNn.0lM3kjNxwSN0EzNzEzW}`

WSL terminal session:
```wsl
hacker@globbing~multiple-globs:~$ /challenge/run *p*
You got it! Here is your flag!
pwn.college{8Yq3JkluFmjh21VYhF_7ajZxgNn.0lM3kjNxwSN0EzNzEzW}
```

### My solve
Used a single glob `*p*` to match all files containing `p`.

### What I learned
Multiple globs can be combined in one word to match more complex patterns.

---
## mixing-globs
**Flag:** `pwn.college{UyduQTFuKN6-QyiwSk4G9mwlRPG.QX1IDO0wCM2kzNzEzW}`

WSL terminal session:
```wsl
Connected!
hacker@globbing~mixing-globs:~$ cd /challenge/files
hacker@globbing~mixing-globs:/challenge/files$ ls
amazing      delightful   great       jovial    magical     pwning   splendid   victorious  youthful
beautiful    educational  happy       kind      nice        queenly  thrilling  wonderful   zesty
challenging  fantastic    incredible  laughing  optimistic  radiant  uplifting  xenial
hacker@globbing~mixing-globs:/challenge/files$ /challenge/run [cep]*
You got it! Here is your flag!
pwn.college{UyduQTFuKN6-QyiwSk4G9mwlRPG.QX1IDO0wCM2kzNzEzW}
```

### My solve
I combined a bracket glob `[cep]` with `*` to match all files that start with `c`, `e`, or `p`. This satisfied the challenge requirement to cover multiple files in a short globbed argument (≤3 characters for the challenge).

### What I learned
- You can mix `[]` with `*` to create flexible patterns that match a subset of files.  
- Keep globbed arguments short to satisfy constraints in scripts.  
- Mixing globs is powerful for selecting multiple files while excluding others.

## exclusionary-globbing
**Flag:** `pwn.college{IWXzeak4myS9bym3VZ-bgiRt4co.QX2IDO0wCM2kzNzEzW}`

WSL terminal session:
```wsl
Connected!
hacker@globbing~exclusionary-globbing:~$ cd /challenge/files
hacker@globbing~exclusionary-globbing:/challenge/files$ /challenge/run [^pwn]*
You got it! Here is your flag!
pwn.college{IWXzeak4myS9bym3VZ-bgiRt4co.QX2IDO0wCM2kzNzEzW}
```

### My solve
Used `[^pwn]*` to exclude characters `p`, `w`, or `n` in the match.

### What I learned
`[^...]` allows negation of characters within brackets.

---

# Tab Completion

## tab-completion-for-files
**Flag:** `pwn.college{0VgpwBaEwFagPFF2eGKLwIqiJuQ.0FN0EzNxwCM2kzNzEzW}`

WSL terminal session:
```wsl
Connected!
hacker@globbing~tab-completion:~$ ccat /challenge/pwncollege​
pwn.college{0VgpwBaEwFagPFF2eGKLwIqiJuQ.0FN0EzNxwCM2kzNzEzW}
```

### My solve
Used tab-completion to auto-complete the tricky filename in `/challenge`.

### What I learned
Tab-completion prevents errors and saves typing. It is essential for tricky filenames that are hard to type.

---

## multiple-options-tab-completion
**Flag:** `pwn.college{4cWR6VmwafelXcRA8nNrXptvruG.0lN0EzNxwCM2kzNzEzW}`

WSL terminal session:
```wsl
Connected!
hacker@globbing~multiple-options-for-tab-completion:~$ cd /challenge/files
hacker@globbing~multiple-options-for-tab-completion:/challenge/files$ cat ./pwncollege-flag
pwn.college{4cWR6VmwafelXcRA8nNrXptvruG.0lN0EzNxwCM2kzNzEzW}
```

### My solve
Navigated `/challenge/files` with tab-completion to locate `pwncollege-flag` and cat the file.

### What I learned
When multiple files match the prefix, hitting tab twice lists all options. Helps discover files with similar names.

---

## tab-completion-on-commands
**Flag:** `pwn.college{YFWkGsT9EhMXopewU6nm2JwNNK2.0VN0EzNxwCM2kzNzEzW}`

WSL terminal session:
```wsl
root@LAPTOP-FOONIF69:~# ssh -i ./key hacker@dojo.pwn.college
Connected!
hacker@globbing~tab-completion-on-commands:~$ pwncollege-25771
Correct! Here is your flag:
pwn.college{YFWkGsT9EhMXopewU6nm2JwNNK2.0VN0EzNxwCM2kzNzEzW}
```

### My solve
Used tab-completion for commands to auto-complete a `pwncollege` binary that gives the flag.

### What I learned
Tab completion works for both filenames and commands. It prevents mistakes and speeds up navigation.

---
