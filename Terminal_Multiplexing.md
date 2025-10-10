# Terminal Multiplexing — Formatted Solutions

This module demonstrates terminal multiplexers (`screen` and `tmux`). Each challenge below contains the **goal**, the **flag**, the **terminal session** (in a `bash` code block), a short **what I learned**, and **references**.

---

## Launching `screen`

**Goal:** Start a `screen` session and discover the flag shown inside it.

**Flag**

```
pwn.college{QEnGTcqaEoyOepSXtCcTsL2yJX0.0VN4IDOxwCM2kzNzEzW}
```

**Terminal**

```bash
Congratulations! You're inside a screen session!
Here's your flag:
pwn.college{QEnGTcqaEoyOepSXtCcTsL2yJX0.0VN4IDOxwCM2kzNzEzW}
hacker@terminal-multiplexing~launching-screen:~$
```

**What I learned**

* `screen` creates virtual terminals inside a single real terminal. Use `exit` or `Ctrl-D` to leave a screen window.

**References**

* pwn.college

---

## Detaching and Attaching (screen)

**Goal:** Detach a `screen` session and reattach to retrieve the flag.

**Flag**

```
pwn.college{s4Vxbv8136QnJnvcvobUwzs7zF0.0lN4IDOxwCM2kzNzEzW}
```

**Terminal**

```bash
hacker@terminal-multiplexing~detaching-and-attaching:~$ echo Yes! Flag is: pwn.college{s4Vxbv8136QnJnvcvobUwzs7zF0.0lN4IDOxwCM2kzNzEzW}
Yes! Flag is: pwn.college{s4Vxbv8136QnJnvcvobUwzs7zF0.0lN4IDOxwCM2kzNzEzW}
```

**What I learned**

* Detach with `Ctrl-A d` and reattach with `screen -r` to resume sessions.

**References**

* pwn.college

---

## Finding Sessions (screen)

**Goal:** Locate the correct `screen` session that contains the flag.

**Flag**

```
pwn.college{4uCCKdYOrAJVnL2BasmMQ29Qwsr.01N4IDOxwCM2kzNzEzW}
```

**Terminal**

```bash
hacker@terminal-multiplexing~finding-sessions:~$  echo 'Congratulations! You found the right session!'
Congratulations! You found the right session!
hacker@terminal-multiplexing~finding-sessions:~$  echo pwn.college{4uCCKdYOrAJVnL2BasmMQ29Qwsr.01N4IDOxwCM2kzNzEzW}
pwn.college{4uCCKdYOrAJVnL2BasmMQ29Qwsr.01N4IDOxwCM2kzNzEzW}
```

**What I learned**

* Use `screen -ls` to list sessions and `screen -r <pid|name>` to attach to the right one.

**References**

* pwn.college

---

## Switching Windows (screen)

**Goal:** Switch between windows inside `screen` and find the flag in a specific window.

**Flag**

```
pwn.college{8jA5RsxhdaRYfB38knB1PM1t6aS.0FO4IDOxwCM2kzNzEzW}
```

**Terminal**

```bash
hacker@terminal-multiplexing~switching-windows:~$  cat <<MSG
> Excellent work! You found window 0!
> Here is your flag: pwn.college{8jA5RsxhdaRYfB38knB1PM1t6aS.0FO4IDOxwCM2kzNzEzW}
> MSG
Excellent work! You found window 0!
Here is your flag: pwn.college{8jA5RsxhdaRYfB38knB1PM1t6aS.0FO4IDOxwCM2kzNzEzW}
```

**What I learned**

* Useful `screen` shortcuts:

  * `Ctrl-A c` — create window
  * `Ctrl-A n` — next window
  * `Ctrl-A p` — previous window
  * `Ctrl-A 0..9` — jump to numbered windows
  * `Ctrl-A "` — window list

**References**

* pwn.college

---

## Detaching and Attaching (`tmux`)

**Goal:** Use `tmux` to create a session, let a program send a message to it, then reattach to see the flag.

**Flag**

```
pwn.college{gNuCQWfmEw907T08hDOTYKQxGja.0VO4IDOxwCM2kzNzEzW}
```

**Terminal**

```bash
hacker@terminal-multiplexing~detaching-and-attaching-tmux:~$ tmux
[detached (from session 0)]
hacker@terminal-multiplexing~detaching-and-attaching-tmux:~$ /challenge/run
Found detached tmux session: 0
Sending flag to your tmux session...

Flag sent! Now reattach to your tmux session with:
  tmux attach

hacker@terminal-multiplexing~detaching-and-attaching-tmux:~$  echo Congratulations, here is your flag: pwn.college{gNuCQWfmEw907T08hDOTYKQxGja.0VO4IDOxwCM2kzNzEzW}
Congratulations, here is your flag: pwn.college{gNuCQWfmEw907T08hDOTYKQxGja.0VO4IDOxwCM2kzNzEzW}
```

**What I learned**

* `tmux` is a modern terminal multiplexer. Create sessions with `tmux`, list with `tmux ls`, attach with `tmux attach` or `tmux a`.

**References**

* pwn.college

---

## Switching Windows (tmux)

**Goal:** Switch windows inside `tmux` to find the flag.

**Flag**

```

```

**Terminal**

```bash

```

**What I learned**

* Useful `tmux` shortcuts:

  * `Ctrl-B c` — create window
  * `Ctrl-B n` — next window
  * `Ctrl-B p` — previous window
  * `Ctrl-B 0..9` — jump to windows
  * `Ctrl-B w` — window picker
* `tmux` shows windows in a status bar and marks the active one with `*`.

**References**

* pwn.college
* ChatGPT (for clarifying `tmux` shortcuts)

---

*Would you like this exported as a PDF or merged into your master study guide?*
