# Untangling Users — Formatted Solutions

This module explores user identity and privilege escalation on Linux (`su`, `sudo`, password cracking, switching users). Each challenge contains the **goal**, **flag**, the **terminal session** (in a `bash` code block), **what I learned**, and **references**.

---
## Becoming Root with `su`

**Goal:** Become `root` using `su` and read the flagged file.

**Flag**

```
pwn.college{EVyNW_t5KABnf7y_Z7ZxCih56CE.QX1UDN1wCM2kzNzEzW}
```

**Terminal**
```wsl
Connected!
hacker@users~becoming-root-with-su:~$ su
Password:
root@users~becoming-root-with-su:/home/hacker# cat /flag
pwn.college{EVyNW_t5KABnf7y_Z7ZxCih56CE.QX1UDN1wCM2kzNzEzW}
```
**What I learned**

* `su` switches to another user (default `root`) with the target user’s password. Once root, you can access privileged files.

**References**

* pwn.college

## Other Users with `su - username`

**Goal:** Switch to a specific user (`zardus`) and run the challenge binary.

**Flag**

```
pwn.college{kJLCkn_mhkEKr2NYTMIC5co_vaP.QX2UDN1wCM2kzNzEzW}
```

**Terminal**
```wsl
hacker@users~other-users-with-su:~$ su - zardus
WARNING: you are invoking 'su' without specifying the 'zardus' user.
Password:
zardus@users~other-users-with-su:~$ /challenge/run
Congratulations, you have become Zardus! Here is your flag:
pwn.college{kJLCkn_mhkEKr2NYTMIC5co_vaP.QX2UDN1wCM2kzNzEzW}
```
**What I learned**

* `su - username` switches to another user and loads their login environment.

**References**

* pwn.college

---
## Cracking Passwords (john)

**Goal:** Use `john` to crack leaked password hashes, then `su` to log in as that user.

**Flag**

```
pwn.college{kOJDwtRvVId8KQS2bLbvHZhoh92.QX3UDN1wCM2kzNzEzW}
```

**TerminaL**

```wsl
hacker@users~cracking-passwords:~$ ls -l /challenge/shadow-leak
-rw-r--r-- 1 root root 858 Oct 10 15:31 /challenge/shadow-leak
hacker@users~cracking-passwords:~$ cat /challenge/shadow-leak
root:*:20182:0:99999:7:::
daemon:*:20182:0:99999:7:::
bin:*:20182:0:99999:7:::
sys:*:20182:0:99999:7:::
sync:*:20182:0:99999:7:::
games:*:20182:0:99999:7:::
man:*:20182:0:99999:7:::
lp:*:20182:0:99999:7:::
mail:*:20182:0:99999:7:::
news:*:20182:0:99999:7:::
uucp:*:20182:0:99999:7:::
proxy:*:20182:0:99999:7:::
www-data:*:20182:0:99999:7:::
backup:*:20182:0:99999:7:::
list:*:20182:0:99999:7:::
irc:*:20182:0:99999:7:::
gnats:*:20182:0:99999:7:::
nobody:*:20182:0:99999:7:::
_apt:*:20182:0:99999:7:::
systemd-timesync:*:20357:0:99999:7:::
systemd-network:*:20357:0:99999:7:::
systemd-resolve:*:20357:0:99999:7:::
mysql:!:20357:0:99999:7:::
messagebus:*:20357:0:99999:7:::
sshd:*:20357:0:99999:7:::
hacker::20357:0:99999:7:::
zardus:$6$epmT2FKVOIUdxE.B$dDFdEE1oetBYGgfyN8liKelCvM5MbMOYbndCLS1mqSnsx3hlKgcnRpoSjbfCctpd8QS9cdNHyG6AjihmbkdT31:20371:0:99999:7:::
hacker@users~cracking-passwords:~$ john /challenge/shadow-leak
Created directory: /home/hacker/.john
Loaded 1 password hash (crypt, generic crypt(3) [?/64])
Press 'q' or Ctrl-C to abort, almost any other key for status
0g 0:00:00:10 99% 1/3 0g/s 286.2p/s 286.2c/s 286.2C/s zardus999991915..999991900
0g 0:00:00:16 0% 2/3 0g/s 288.8p/s 288.8c/s 288.8C/s rockie..surfing
aardvark         (zardus)
1g 0:00:00:20 1% 2/3 0.04933g/s 287.2p/s 287.2c/s 287.2C/s Johnson..buzz
Use the "--show" option to display all of the cracked passwords reliably
Session aborted
hacker@users~cracking-passwords:~$ john --status
1g 0:00:00:21 1% 2/3 0.04761g/s 277.2p/s 277.2c/s 277.2C/s
hacker@users~cracking-passwords:~$ john --show /challenge/shadow-leak
hacker:NO PASSWORD:20357:0:99999:7:::
zardus:aardvark:20371:0:99999:7:::

2 password hashes cracked, 0 left
hacker@users~cracking-passwords:~$ john --wordlist=/usr/share/wordlists/rockyou.txt --format=sha512crypt /challenge/shadow-leak
Unknown ciphertext format name requested
hacker@users~cracking-passwords:~$ john --incremental --format=sha512crypt /challenge/shadow-leak
Unknown ciphertext format name requested
hacker@users~cracking-passwords:~$ john /challenge/shadow-leak
Loaded 1 password hash (crypt, generic crypt(3) [?/64])
No password hashes left to crack (see FAQ)
hacker@users~cracking-passwords:~$ john --show /challenge/shadow-leak
hacker:NO PASSWORD:20357:0:99999:7:::
zardus:aardvark:20371:0:99999:7:::

2 password hashes cracked, 0 left
hacker@users~cracking-passwords:~$ su - zardus
WARNING: you are invoking 'su' without specifying the 'zardus' user.
Password:
zardus@users~cracking-passwords:~$ /challenge/run
Congratulations, you have become Zardus! Here is your flag:
pwn.college{kOJDwtRvVId8KQS2bLbvHZhoh92.QX3UDN1wCM2kzNzEzW}
```
**What I learned**

* `john` (John the Ripper) can crack weak hashes found in leaked files; compromised credentials let you switch users.
* Always protect password hashes and use strong passwords.

**References**

* pwn.college
* John the Ripper

---
## Using `sudo`

**Goal:** Use `sudo` to run commands as root (or other users) without a password when permitted.

**Flag**

```
pwn.college{smPhxtemry_JdthQXj9oZctfED5.QX4UDN1wCM2kzNzEzW}
```

**Terminal**
```wsl
hacker@users~using-sudo:~$ sudo /challenge/run
In the olden days, a typical Linux system had a `root` password that administrators would use to `su` to root (after logging into their account with their normal account password).
But `root` passwords are a pain to maintain, they (or their hashes!) can leak, and they don't lend themselves well to larger environments (e.g., fleets of servers).
To address this, in recent decades, the world has moved from administration via `su` to administration via `sudo` (*Fun Fact*: `sudo` originally stood for **su**peruser **do**, but has changed to "`su` 'do'", and because `su` stands for "substitute user", the current meaning of `sudo` is "substitute user, do").

Unlike `su`, which defaults to launching a shell as a specified user, `sudo` defaults to running a command as `root`:

```console
hacker@dojo:~$ whoami
hacker
hacker@dojo:~$ sudo whoami
root
hacker@dojo:~$
```

Or, more relevant to getting flags:

```console
hacker@dojo:~$ grep hacker /etc/shadow
grep: /etc/shadow: Permission denied
hacker@dojo:~$ sudo grep hacker /etc/shadow
hacker:$6$Xro.e7qB3Q2Jl2sA$j6xffIgWn9xIxWUeFzvwPf.nOH2NTWNJCU5XVkPuONjIC7jL467SR4bXjpVJx4b/bkbl7kyhNquWtkNlulFoy.:19921:0:99999:7:::
hacker@dojo:~$
```

Unlike `su`, which relies on password authentication, `sudo` checks policies to determine whether the user is authorized to run commands as `root`.
These policies are defined in `/etc/sudoers`, and though it's mostly out of scale for our purposes, there are plenty of [resources](https://www.digitalocean.com/community/tutorials/how-to-edit-the-sudoers-file) for learning about this!

So, the world has moved to `sudo` and has (for the purposes of system administration) left `su` behind.
In fact, even pwn.college's Practice Mode works by giving you `sudo` access to elevate privileges!

In this level, we will give you `sudo` access, and you will use it to read the flag.
Nice and easy!

----
**NOTE:**
After this level, we will enable Privileged Mode!
When you launch a challenge in Privileged Mode (by clicking the `Privileged` button instead of the `Start` button), the resulting container will give you full `sudo` access to allow you to introspect and debug to your heart's content, but of course with a placeholder flag.
hacker@users~using-sudo:~$ sudo cat /flag
pwn.college{smPhxtemry_JdthQXj9oZctfED5.QX4UDN1wCM2kzNzEzW}
```
**What I learned**

* `sudo` executes commands as another user (commonly root). `NOPASSWD` in `/etc/sudoers` allows running permitted commands without supplying a password.
* `sudo` provides finer-grained and auditable privilege delegation compared to `su`.

**References**

* pwn.college
* `man sudo`
