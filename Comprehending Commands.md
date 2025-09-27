# Commands / Filesystem — Full Module Writeups

# cat-not-the-pet-but-the-command
Read the flag file in your home directory using `cat`.

## My solve
**Flag:** `pwn.college{MvX8kqS_uC7FFVENIS4v7gzc8oF.QXxcTN0wCM2kzNzEzW}`

I opened the flag file in my home directory using `cat flag` to display its contents.

WSL terminal session:
```
root@LAPTOP-FOONIF69:~# ssh -i ./key hacker@dojo.pwn.college
Connected!
hacker@commands~cat-not-the-pet-but-the-command:~$
hacker@commands~cat-not-the-pet-but-the-command:~$ cat flag
pwn.college{MvX8kqS_uC7FFVENIS4v7gzc8oF.QXxcTN0wCM2kzNzEzW}
```

## What I learned
Simple use of `cat` to read files in the current directory; confirm file permissions before attempting more advanced reads.

## References
`man cat`; pwn.college challenge description.

---

# catting-absolute-paths
Read the flag at absolute path `/flag`.

## My solve
**Flag:** `pwn.college{EBvjG7Q3CoVO15HyX6ul8EGI8Mc.QX5ETO0wCM2kzNzEzW}`

I used `cat /flag` to read the file placed at an absolute path.

WSL terminal session:
```wsl
Connected!
hacker@commands~catting-absolute-paths:~$ cat /flag
pwn.college{EBvjG7Q3CoVO15HyX6ul8EGI8Mc.QX5ETO0wCM2kzNzEzW}
```

## What I learned
Absolute paths let you read files regardless of current working directory (if permissions allow).

## References
Didn't use any reference.

---

# more-catting-practice
Read the flag at `/lib/maxima-sage/flag` by absolute path (no `cd` allowed).

## My solve
**Flag:** `pwn.college{cJiqorbdh5Q8cCPypwfBsPm8eOv.QXwITO0wCM2kzNzEzW}`

I used `cat /lib/maxima-sage/flag` to print the flag from that absolute path without changing directories.

WSL terminal session:
```wsl
root@LAPTOP-FOONIF69:~# ssh -i ./key hacker@dojo.pwn.college
Connected!
You cannot use the 'cd' command in this level, and must retrieve the flag by
absolute path. Plus, I hid the flag in a different directory! You can find it
in the file /lib/x86_64-linux-gnu/perl5/flag. Go cat it out *without* cding
into that directory!
hacker@commands~more-catting-practice:~$ cat /lib/x86_64-linux-gnu/perl5/flag
pwn.college{cJiqorbdh5Q8cCPypwfBsPm8eOv.QXwITO0wCM2kzNzEzW}
```

## What I learned
You can access files anywhere by absolute path; `cd` is not required and may be disallowed by challenge constraints.

## References
`man cat`; pwn.college challenge description.

---

# grepping-for-a-needle-in-a-haystack
Search a large file for the flag using `grep`.

## My solve
**Flag:** `pwn.college{QaPXVLOH2h3KEUf3tc6b_Q06I1O.QX3EDO0wCM2kzNzEzW}`

I searched `/challenge/data.txt` for the known prefix `pwn.college` with `grep`.

WSL terminal session:
```wsl
Connected!
hacker@commands~grepping-for-a-needle-in-a-haystack:~$ grep pwn.college /challenge/data.txt
pwn.college{QaPXVLOH2h3KEUf3tc6b_Q06I1O.QX3EDO0wCM2kzNzEzW}
```

## What I learned
`grep` is the right tool for extracting matching lines from very large files; use anchored or unique prefixes to narrow results.

## References
Didn't use any reference.

---

# comparing-files
Use `diff` to compare two files and reveal an added flag line.

## My solve
**Flag:** `pwn.college{YFWAr8CNea7O3fxnhyIzQMyAsBH.01MwMDOxwCM2kzNzEzW}`

I ran `diff /challenge/decoys_only.txt /challenge/decoys_and_real.txt` and inspected the added line.

WSL terminal session:
```wsl
hacker@commands~comparing-files:~$ diff /challenge/decoys_only.txt /challenge/decoys_and_real.txt
23a24
> pwn.college{YFWAr8CNea7O3fxnhyIzQMyAsBH.01MwMDOxwCM2kzNzEzW}
```

## What I learned
`diff` is useful to spot differences between files; added lines are typically marked with `a` and `>`.

## References
Didn't use any reference.

---

# listing-files:/challenge
List `/challenge` to find the renamed binary and run it.

## My solve
**Flag:** `pwn.college{Ysr657_5EjHMd6HOjmTAI3tQuv1.QX4IDO0wCM2kzNzEzW}`

I used `ls /challenge` to find the randomized filename and executed it by full path.

WSL terminal session:
```wsl
Connected!
hacker@commands~listing-files:~$ ls /challenge
4735-renamed-run-419  DESCRIPTION.md
hacker@commands~listing-files:~$ /challenge/4735-renamed-run-419  DESCRIPTION.md
Yahaha, you found me! Here is your flag:
pwn.college{Ysr657_5EjHMd6HOjmTAI3tQuv1.QX4IDO0wCM2kzNzEzW}
```

## What I learned
`ls` reveals file names; execute discovered binaries with absolute paths to avoid PATH issues.

## References
Didn't use any reference

---

# touching-files:/tmp
Create `/tmp/pwn` and `/tmp/college` with `touch`, then run the checker.

## My solve
**Flag:** `pwn.college{oobN3N5EA5vu4ZvxrTbqhCdXhRC.QXwMDO0wCM2kzNzEzW}`

I created the required files in `/tmp` using `touch` and ran `/challenge/run` to confirm.

WSL terminal session:
```wsl
Connected!
hacker@commands~touching-files:~$ touch pwn
hacker@commands~touching-files:~$ touch college
hacker@commands~touching-files:~$ ls
college  home-backup.tar.gz  n  pwn
hacker@commands~touching-files:~$ /challenge/run
Success! Here is your flag:
pwn.college{oobN3N5EA5vu4ZvxrTbqhCdXhRC.QXwMDO0wCM2kzNzEzW}
```

## What I learned
`touch` creates empty files; verify creates with `ls` before invoking checkers.

## References
Didn't use any reference

---

# removing-files
Delete the provided `delete_me` file and run the checker.

## My solve
**Flag:** `pwn.college{ETRoM3r1CtNnDobkhDtx2sS01c2.QX2kDM1wCM2kzNzEzW}`

I removed `delete_me` with `rm` and ran `/challenge/check` to receive the flag.

WSL terminal session:
```wsl
Connected!
hacker@commands~removing-files:~$ ls
college  delete_me  home-backup.tar.gz  n  not-the-flag  pwn
hacker@commands~removing-files:~$ rm delete_me
hacker@commands~removing-files:~$ ls
college  home-backup.tar.gz  n  not-the-flag  pwn
hacker@commands~removing-files:~$ /challenge/check
Excellent removal. Here is your reward:
pwn.college{ETRoM3r1CtNnDobkhDtx2sS01c2.QX2kDM1wCM2kzNzEzW}
```

## What I learned
`rm` deletes files — double-check names before running; use `ls` to confirm deletion.

## References
Didn't use any reference

---

# moving-files
Move `/flag` into `/tmp/hack-the-planet` and run the checker.

## My solve
**Flag:** `pwn.college{kIB_oUBmfTZ8NBerZxh_2va09r8.0VOxEzNxwCM2kzNzEzW}`

I moved the global `/flag` to `/tmp/hack-the-planet` with `mv` and ran the checker to verify.

WSL terminal session:
```wsl
Connected!
hacker@commands~moving-files:~$ mv /flag /tmp/hack-the-planet
Correct! Performing 'mv /flag /tmp/hack-the-planet'.
hacker@commands~moving-files:~$ /challenge/check
Congrats! You successfully moved the flag to /tmp/hack-the-planet! Here it is:
pwn.college{kIB_oUBmfTZ8NBerZxh_2va09r8.0VOxEzNxwCM2kzNzEzW}
```

## What I learned
`mv` renames/moves files; ensure destination path exists or use `mkdir -p` to create it first.

## References
`man mv`; filesystem move semantics.

---

# hidden-files
Find dot-prepended hidden files under `/` and read the flagged hidden file.

## My solve
**Flag:** `pwn.college{ogycPgWWn7G2Yg4V9L-VAMVXoe9.QXwUDO0wCM2kzNzEzW}`

I used `ls -a` to reveal hidden files in `/` and `cat`ed the discovered hidden flag file.

WSL terminal session:
```wsl
Connected!
hacker@commands~hidden-files:~$ cd /
hacker@commands~hidden-files:/$ ls -a
.   .dockerenv            bin   challenge  etc   lib    lib64   media  nix  proc  run   srv  tmp  var
..  .flag-17796259223008  boot  dev        home  lib32  libx32  mnt    opt  root  sbin  sys  usr
hacker@commands~hidden-files:/$ cat /.flag-17796259223008
pwn.college{ogycPgWWn7G2Yg4V9L-VAMVXoe9.QXwUDO0wCM2kzNzEzW}
```

## What I learned
Hidden files begin with `.` and are only shown by `ls -a`; they can hold important data or clues.

## References
Didn't use any reference

---

# making-directories (/tmp/pwn)
Create `/tmp/pwn`, add `college`, then run the checker.

## My solve
**Flag:** `pwn.college{szzZMZ9gpYR6DBdprHJqZNIwBjW.QXxMDO0wCM2kzNzEzW}`

I created the directory, created the `college` file, and ran `/challenge/run` to get the flag.

WSL terminal session:
```wsl
root@LAPTOP-FOONIF69:~# ssh -i ./key hacker@dojo.pwn.college
Connected!
hacker@commands~making-directories:~$ mkdir /tmp/pwn
hacker@commands~making-directories:~$ cd /tmp/pwn
hacker@commands~making-directories:/tmp/pwn$ touch college
hacker@commands~making-directories:/tmp/pwn$ /challenge/run
Success! Here is your flag:
pwn.college{szzZMZ9gpYR6DBdprHJqZNIwBjW.QXxMDO0wCM2kzNzEzW}
```

## What I learned
`mkdir` creates directories and `touch` creates files inside them; checkers can require specific directory structure/filenames.

## References
Didn't use any reference

---

# finding-files (find)
Search the filesystem for files named `flag` and inspect them for the real flag.

## My solve
**Flag:** `pwn.college{cbv7iuPEUU5ZU9OZLBV1PpJXKeb.QXyMDO0wCM2kzNzEzW}pwn.college{cbv7iuPEUU5ZU9OZLBV1PpJXKeb.QXyMDO0wCM2kzNzEzW}`

I ran `find / -name flag`, filtered candidate results, and `cat`ed the relevant file.

WSL terminal session:
```wsl
Connected!
hacker@commands~finding-files:~$ find / -name flag
/usr/local/lib/python3.8/dist-packages/pwnlib/flag
/usr/lib/python3/dist-packages/sympy/integrals/rubi/tests/flag
... (other matches) ...
/nix/store/5qz6hgb1qzpvjrsw20wyiylx5zw8b9bk-pwntools-4.14.0/lib/python3.13/site-packages/pwnlib/flag

hacker@commands~finding-files:~$ cat /usr/lib/python3/dist-packages/scipy/spatial/transform/_pycache_/flag
pwn.college{cbv7iuPEUU5ZU9OZLBV1PpJXKeb.QXyMDO0wCM2kzNzEzW}
```

## What I learned
`find` can search whole filesystem trees; expect and ignore permission-denied noise; focus on accessible results.

## References
Didn't use any reference

# linking-files
Make a symlink so a script that `cat`s a specific path prints the real flag.

## My solve
**Flag:** `pwn.college{kdOY2qV2VjNTm6d3A6-q2FFz9Fx.QX5ETN1wCM2kzNzEzW}`

I created a symlink from `/flag` to `/home/hacker/not-the-flag`, then ran the script that reads that fixed path.

WSL terminal session:
```wsl
hacker@commands~linking-files:~$ ln -s /flag /home/hacker/not-the-flag
hacker@commands~linking-files:~$ /challenge/catflag
About to read out the /home/hacker/not-the-flag file!
pwn.college{kdOY2qV2VjNTm6d3A6-q2FFz9Fx.QX5ETN1wCM2kzNzEzW}
```

## What I learned
Symbolic links (`ln -s`) let you satisfy programs/scripts that read fixed file paths by pointing those paths to the real file.

## References
Didn't use any reference
# an-epic-filesystem-quest
Follow a chain of clues (hidden/delayed/trapped) across many directories to the final flag.

## My solve
**Flag:** `pwn.college{UCH835FGbmepkr-SLzHHI4VvOwD.QX5IDO0wSN0EzNzEzW}`

I followed breadcrumb clues starting at `/`, used `ls -a` for hidden clues, `cd` when clues were delayed, and `cat` by full path for trapped clues. The final trapped clue revealed the flag.

WSL terminal session:
```wsl
Connected!
hacker@commands~an-epic-filesystem-quest:~$ cd /
hacker@commands~an-epic-filesystem-quest:/$ ls
LEAD  boot       dev  flag  lib    lib64   media  nix  proc  run   srv  tmp  var
bin   challenge  etc  home  lib32  libx32  mnt    opt  root  sbin  sys  usr
hacker@commands~an-epic-filesystem-quest:/$ cat LEAD
Great sleuthing!
The next clue is in: /usr/local/lib/python3.8/dist-packages/git/__pycache__

The next clue is **hidden** --- its filename starts with a '.' character. You'll need to look for it using special options to 'ls'.
hacker@commands~an-epic-filesystem-quest:/$ ls -a
.   .dockerenv  bin   challenge  etc   home  lib32  libx32  mnt  opt   root  sbin  sys  usr
..  LEAD        boot  dev        flag  lib   lib64  media   nix  proc  run   srv   tmp  var
hacker@commands~an-epic-filesystem-quest:/$ ls /usr/local/lib/python3.8/dist-packages/git/__pycache__
__init__.cpython-38.pyc  compat.cpython-38.pyc  db.cpython-38.pyc    exc.cpython-38.pyc     types.cpython-38.pyc
cmd.cpython-38.pyc       config.cpython-38.pyc  diff.cpython-38.pyc  remote.cpython-38.pyc  util.cpython-38.pyc
hacker@commands~an-epic-filesystem-quest:/$ ls -a /usr/local/lib/python3.8/dist-packages/git/__pycache__
.       __init__.cpython-38.pyc  config.cpython-38.pyc  exc.cpython-38.pyc     util.cpython-38.pyc
..      cmd.cpython-38.pyc       db.cpython-38.pyc      remote.cpython-38.pyc
.BRIEF  compat.cpython-38.pyc    diff.cpython-38.pyc    types.cpython-38.pyc
hacker@commands~an-epic-filesystem-quest:/$ cat .BRIEF
cat: .BRIEF: No such file or directory
hacker@commands~an-epic-filesystem-quest:/$ ls -a .BRIEF
ls: cannot access '.BRIEF': No such file or directory
hacker@commands~an-epic-filesystem-quest:/$ ls -a
.   .dockerenv  bin   challenge  etc   home  lib32  libx32  mnt  opt   root  sbin  sys  usr
..  LEAD        boot  dev        flag  lib   lib64  media   nix  proc  run   srv   tmp  var
hacker@commands~an-epic-filesystem-quest:/$ cd /usr/local/lib/python3.8/dist-packages/git/__pycache__
hacker@commands~an-epic-filesystem-quest:/usr/local/lib/python3.8/dist-packages/git/__pycache__$ cat .BRIEF
Great sleuthing!
The next clue is in: /usr/lib/python3/dist-packages/sympy/strategies/branch/__pycache__

Watch out! The next clue is **trapped**. You'll need to read it out without 'cd'ing into the directory; otherwise, the clue will self destruct!
hacker@commands~an-epic-filesystem-quest:/usr/local/lib/python3.8/dist-packages/git/__pycache__$ ls /usr/lib/python3/dist-packages/sympy/strategies/branch/__pycache__
BLUEPRINT-TRAPPED  __init__.cpython-38.pyc  core.cpython-38.pyc  tools.cpython-38.pyc  traverse.cpython-38.pyc
hacker@commands~an-epic-filesystem-quest:/usr/local/lib/python3.8/dist-packages/git/__pycache__$ ls /usr/lib/python3/dist-packages/sympy/strategies/branch/__pycache__ | grep BLUEPRINT BLUEPRINT-TRAPPED
grep: BLUEPRINT-TRAPPED: No such file or directory
hacker@commands~an-epic-filesystem-quest:/usr/local/lib/python3.8/dist-packages/git/__pycache__$  ls /usr/lib/python3/dist-packages/sympy/strategies/branch/__pycache__
BLUEPRINT-TRAPPED  __init__.cpython-38.pyc  core.cpython-38.pyc  tools.cpython-38.pyc  traverse.cpython-38.pyc
hacker@commands~an-epic-filesystem-quest:/usr/local/lib/python3.8/dist-packages/git/__pycache__$ ls /usr/lib/python3/dist-packages/sympy/strategies/branch/__pycache__ | grep BLUEPRINT
BLUEPRINT-TRAPPED
hacker@commands~an-epic-filesystem-quest:/usr/local/lib/python3.8/dist-packages/git/__pycache__$ cat /usr/lib/python3/dist-packages/sympy/strategies/branch/__pycache__/BLUEPRINT-TRAPPED
Lucky listing!
The next clue is in: /opt/linux/linux-5.4/fs/omfs
hacker@commands~an-epic-filesystem-quest:/usr/local/lib/python3.8/dist-packages/git/__pycache__$ cd /opt/linux/linux-5.4/fs/omfs
hacker@commands~an-epic-filesystem-quest:/opt/linux/linux-5.4/fs/omfs$ ls -a
.  ..  Kconfig  Makefile  TRACE  bitmap.c  dir.c  file.c  inode.c  omfs.h  omfs_fs.h
hacker@commands~an-epic-filesystem-quest:/opt/linux/linux-5.4/fs/omfs$ cat TRACE
Lucky listing!
The next clue is in: /opt/linux/linux-5.4/drivers/gpu/drm/vkms

The next clue is **delayed** --- it will not become readable until you enter the directory with 'cd'.
hacker@commands~an-epic-filesystem-quest:/opt/linux/linux-5.4/fs/omfs$ cd /opt/linux/linux-5.4/drivers/gpu/drm/vkms
hacker@commands~an-epic-filesystem-quest:/opt/linux/linux-5.4/drivers/gpu/drm/vkms$ ls
CLUE  Makefile  vkms_composer.c  vkms_crtc.c  vkms_drv.c  vkms_drv.h  vkms_gem.c  vkms_output.c  vkms_plane.c
hacker@commands~an-epic-filesystem-quest:/opt/linux/linux-5.4/drivers/gpu/drm/vkms$ cat CLUE
Lucky listing!
The next clue is in: /usr/lib/python3/dist-packages/sphinx/directives

Watch out! The next clue is **trapped**. You'll need to read it out without 'cd'ing into the directory; otherwise, the clue will self destruct!
hacker@commands~an-epic-filesystem-quest:/opt/linux/linux-5.4/drivers/gpu/drm/vkms$ ls /usr/lib/python3/dist-packages/sphinx/directives
TIP-TRAPPED  __init__.py  __pycache__  code.py  other.py  patches.py
hacker@commands~an-epic-filesystem-quest:/opt/linux/linux-5.4/drivers/gpu/drm/vkms$ ls /usr/lib/python3/dist-packages/sphinx/directives | grep TIP
TIP-TRAPPED
hacker@commands~an-epic-filesystem-quest:/opt/linux/linux-5.4/drivers/gpu/drm/vkms$ cat /usr/lib/python3/dist-packages/sphinx/directives/TIP-TRAPPED
Congratulations, you found the clue!
The next clue is in: /opt/pwndbg/.venv/lib/python3.8/site-packages/pip/_internal/index/__pycache__
hacker@commands~an-epic-filesystem-quest:/opt/linux/linux-5.4/drivers/gpu/drm/vkms$ cd  /opt/pwndbg/.venv/lib/python3.8/site-packages/pip/_internal/index/__pycache__
hacker@commands~an-epic-filesystem-quest:/opt/pwndbg/.venv/lib/python3.8/site-packages/pip/_internal/index/__pycache__$ ls
HINT  __init__.cpython-38.pyc  collector.cpython-38.pyc  package_finder.cpython-38.pyc  sources.cpython-38.pyc
hacker@commands~an-epic-filesystem-quest:/opt/pwndbg/.venv/lib/python3.8/site-packages/pip/_internal/index/__pycache__$ cat HINT
Lucky listing!
The next clue is in: /usr/lib/python3/dist-packages/Cython/__pycache__

Watch out! The next clue is **trapped**. You'll need to read it out without 'cd'ing into the directory; otherwise, the clue will self destruct!
hacker@commands~an-epic-filesystem-quest:/opt/pwndbg/.venv/lib/python3.8/site-packages/pip/_internal/index/__pycache__$ ls /usr/lib/python3/dist-packages/Cython/__pycache__
CodeWriter.cpython-38.pyc  Debugging.cpython-38.pyc  Shadow.cpython-38.pyc        TestUtils.cpython-38.pyc  __init__.cpython-38.pyc
Coverage.cpython-38.pyc    SNIPPET-TRAPPED           StringIOTree.cpython-38.pyc  Utils.cpython-38.pyc
hacker@commands~an-epic-filesystem-quest:/opt/pwndbg/.venv/lib/python3.8/site-packages/pip/_internal/index/__pycache__$ ls /usr/lib/python3/dist-packages/Cython/__pycache__ | grep SNIPPET
SNIPPET-TRAPPED
hacker@commands~an-epic-filesystem-quest:/opt/pwndbg/.venv/lib/python3.8/site-packages/pip/_internal/index/__pycache__$ cat /usr/lib/python3/dist-packages/Cython/__pycache__/SNIPPET-TRAPPED
Congratulations, you found the clue!
The next clue is in: /usr/lib/aarch64-linux-gnu

The next clue is **delayed** --- it will not become readable until you enter the directory with 'cd'.
hacker@commands~an-epic-filesystem-quest:/opt/pwndbg/.venv/lib/python3.8/site-packages/pip/_internal/index/__pycache__$ cd /usr/lib/aarch64-linux-gnu
hacker@commands~an-epic-filesystem-quest:/usr/lib/aarch64-linux-gnu$ ls -a
.  ..  SECRET  ldscripts
hacker@commands~an-epic-filesystem-quest:/usr/lib/aarch64-linux-gnu$ cat SECRET
CONGRATULATIONS! Your perserverence has paid off, and you have found the flag!
It is: pwn.college{wHWu-niU337UfBi5OjwicmW333U.QX5IDO0wCM2kzNzEzW}
```

## What I learned
Combining `ls`, `ls -a`, `cd`, and `cat` is powerful for filesystem forensics; pay attention to instructions (hidden/delayed/trapped).

## References
Didn't use any reference

---
