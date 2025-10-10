# DATA MANIPULATION

This module covers common data-processing utilities (`tr`, `head`, `cut`, `sort`) and shows how to manipulate piped input, delete characters, remove newlines, extract lines or fields, and sort data.
---
# TRANSLATING CHARACTERS
**MY FLAG**:pwn.college{sHVZESfRhX7-JKZuN14haS4ix6U.01MxEzNxwCM2kzNzEzW}
CODE:
```wsl
hacker@data~translating-characters:~$ /challenge/run | tr 'A-Za-z' 'a-zA-Z'
yOUR CASE-SWAPPED FLAG:
pwn.college{sHVZESfRhX7-JKZuN14haS4ix6U.01MxEzNxwCM2kzNzEzW}
```
**What I learned**

* `tr` translates character sets; here it swaps letter case.

**Reference**
* pwn.college

# DELETING CHARACTERS
**MY FLAG**: pwn.college{0RxDd2TnbtWIFarQFnjpxi424fs.0FNxEzNxwCM2kzNzEzW}
CODE:
```wsl
hacker@data~deleting-characters:~$ /challenge/run | tr -d '^%'
Your character-stuffed flag:
pwn.college{0RxDd2TnbtWIFarQFnjpxi424fs.0FNxEzNxwCM2kzNzEzW}
```
**What I learned**

* `tr -d` deletes characters from the input stream.

**Reference**
* pwn.college

# DELETING NEW LINES
**MY FLAG**:pwn.college{AiJwDLmQ3IWZu9B6iJmeDlitVjm.0VNxEzNxwCM2kzNzEzW}
CODE:
```wsl
hacker@data~deleting-newlines:~$ /challenge/run | tr -d "\n"
Your line-split flag: pwn.college{AiJwDLmQ3IWZu9B6iJmeDlitVjm.0VNxEzNxwCM2kzNzEzW}
```
**What I learned**

* Use `tr -d '\n'` to join multiple lines into a single line.

**Reference**

* pwn.college
  ---

# EXECUTING THE FIRST LINES WITH HEAD
**MY FLAG**:pwn.college{o81D8BsO68LcEbOCdF4ehhLRmSg.0lNxEzNxwCM2kzNzEzW}
CODE:
```wsl
hacker@data~extracting-the-first-lines-with-head:~$ /challenge/pwn | head -n 7 | /challenge/college
Congratulations, you piped the right codes!
pwn.college{o81D8BsO68LcEbOCdF4ehhLRmSg.0lNxEzNxwCM2kzNzEzW}
```
**What I learned**

* `head -n N` prints the first N lines of its input; useful to limit verbose output.

**Reference**

* pwn.college

---
# EXTRACTING SPECIFIC SECTIONS OF TEXT
**MY FLAG**:pwn.college{4m--NBi6AfuTxGQJRjEiBSujgnH.01NxEzNxwCM2kzNzEzW}
CODE:
```wsl
Connected!
hacker@data~extracting-specific-sections-of-text:~$ /challenge/run | cut -d ' ' -f 2 | tr -d "\n"
pwn.college{4m--NBi6AfuTxGQJRjEiBSujgnH.01NxEzNxwCM2kzNzEzW}
```
**What I learned**

* `cut -d 'DELIM' -f N` extracts the Nth field using DELIM as separator. Combine with `tr -d '\n'` to join characters into one line.

**Reference**

* pwn.college

---
# SORTING DATA
**MY FLAG**:pwn.college{s9PNT9VNChj19LOmlXM38AsDQRN.0FM0MDOxwCM2kzNzEzW}
CODE:
```wsl
Connected!
hacker@data~sorting-data:~$ sort /challenge/flags.txt | tail -n 1
pwn.college{s9PNT9VNChj19LOmlXM38AsDQRN.0FM0MDOxwCM2kzNzEzW}
```
**What I learned**

* `sort` orders lines lexicographically; combine with `head`/`tail` to choose extremes.

**Reference**

* pwn.college

---
