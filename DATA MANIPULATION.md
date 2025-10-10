# DATA MANIPULATION
# TRANSLATING CHARACTERS
MY FLAG:pwn.college{sHVZESfRhX7-JKZuN14haS4ix6U.01MxEzNxwCM2kzNzEzW}
CODE:
hacker@data~translating-characters:~$ /challenge/run | tr 'A-Za-z' 'a-zA-Z'
yOUR CASE-SWAPPED FLAG:
pwn.college{sHVZESfRhX7-JKZuN14haS4ix6U.01MxEzNxwCM2kzNzEzW}
# DELETING CHARACTERS
MY FLAG: pwn.college{0RxDd2TnbtWIFarQFnjpxi424fs.0FNxEzNxwCM2kzNzEzW}
CODE:
hacker@data~deleting-characters:~$ /challenge/run | tr -d '^%'
Your character-stuffed flag:
pwn.college{0RxDd2TnbtWIFarQFnjpxi424fs.0FNxEzNxwCM2kzNzEzW}
# DELETING NEW LINES
MY FLAG:pwn.college{AiJwDLmQ3IWZu9B6iJmeDlitVjm.0VNxEzNxwCM2kzNzEzW}
CODE:
hacker@data~deleting-newlines:~$ /challenge/run | tr -d "\n"
Your line-split flag: pwn.college{AiJwDLmQ3IWZu9B6iJmeDlitVjm.0VNxEzNxwCM2kzNzEzW}
# EXECUTING THE FIRST LINES WITH HEAD
MY FLAG:
CODE:pwn.college{o81D8BsO68LcEbOCdF4ehhLRmSg.0lNxEzNxwCM2kzNzEzW}
hacker@data~extracting-the-first-lines-with-head:~$ /challenge/pwn | head -n 7 | /challenge/college
Congratulations, you piped the right codes!
pwn.college{o81D8BsO68LcEbOCdF4ehhLRmSg.0lNxEzNxwCM2kzNzEzW}
# EXTRACTING SPECIFIC SECTIONS OF TEXT
MY FLAG:pwn.college{4m--NBi6AfuTxGQJRjEiBSujgnH.01NxEzNxwCM2kzNzEzW}
CODE:
Connected!
hacker@data~extracting-specific-sections-of-text:~$ /challenge/run | cut -d ' ' -f 2 | tr -d "\n"
pwn.college{4m--NBi6AfuTxGQJRjEiBSujgnH.01NxEzNxwCM2kzNzEzW}
# SORTING DATA
MY FLAG:pwn.college{s9PNT9VNChj19LOmlXM38AsDQRN.0FM0MDOxwCM2kzNzEzW}
CODE:
Connected!
hacker@data~sorting-data:~$ sort /challenge/flags.txt | tail -n 1
pwn.college{s9PNT9VNChj19LOmlXM38AsDQRN.0FM0MDOxwCM2kzNzEzW}
