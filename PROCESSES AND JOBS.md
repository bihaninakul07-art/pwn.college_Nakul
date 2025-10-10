# PROCESSES AND JOBS
# LISTING PROCESSES
**FLAG**:pwn.college{gxskEmiGfB-9nf0pD_kN4mrTa8o.QX4MDO0wCM2kzNzEzW}
CODE:
```wsl
Connected!
hacker@processes~listing-processes:~$ ps -efww
UID          PID    PPID  C STIME TTY          TIME CMD
root           1       0  0 13:51 ?        00:00:00 /sbin/docker-init -- /nix/var/nix/profiles/dojo-workspace/bin/dojo-init /run/dojo/bin/sleep 6h
root           7       1  0 13:51 ?        00:00:00 /run/dojo/bin/sleep 6h
root         132       1  0 13:51 ?        00:00:00 /challenge/19900-run-8061
root         135     132  0 13:51 ?        00:00:00 sleep 6h
hacker       137       0  0 13:51 pts/0    00:00:00 /nix/store/0nxvi9r5ymdlr2p24rjj9qzyms72zld1-bash-interactive-5.2p37/bin/bash /run/dojo/bin/ssh-entrypoint
hacker       143     137  0 13:51 pts/0    00:00:00 /run/dojo/bin/bash --login
hacker       174       0  0 13:57 pts/1    00:00:00 /nix/store/0nxvi9r5ymdlr2p24rjj9qzyms72zld1-bash-interactive-5.2p37/bin/bash /run/dojo/bin/ssh-entrypoint
hacker       180     174  0 13:57 pts/1    00:00:00 /run/dojo/bin/bash --login
hacker       189     180  0 13:57 pts/1    00:00:00 ps -efww
hacker@processes~listing-processes:~$ ps -efww | grep /challenge
root         132       1  0 13:51 ?        00:00:00 /challenge/19900-run-8061
hacker       191     180  0 13:57 pts/1    00:00:00 grep --color=auto /challenge
hacker@processes~listing-processes:~$ /challenge/19900-run-8061
Yahaha, you found me! Here is your flag:
pwn.college{gxskEmiGfB-9nf0pD_kN4mrTa8o.QX4MDO0wCM2kzNzEzW}
Now I will sleep for a while (so that you could find me with 'ps').
```
# KILLING PROCESSES
**FLAG**:pwn.college{sWDw4Dt9nVKMhmoxk06BzX2rOyP.QXyQDO0wCM2kzNzEzW}
CODE:
```wsl
Connected!
hacker@processes~killing-processes:~$ ps -efww | grep /challenge/dont_run
hacker       136     135  0 13:59 ?        00:00:00 /challenge/dont_run
hacker       155     145  0 13:59 pts/0    00:00:00 grep --color=auto /challenge/dont_run
hacker@processes~killing-processes:~$ kill 136
hacker@processes~killing-processes:~$ ps -efww | grep /challenge/dont_run
hacker       157     145  0 14:00 pts/0    00:00:00 grep --color=auto /challenge/dont_run
hacker@processes~killing-processes:~$ kill 157
bash: kill: (157) - No such process
hacker@processes~killing-processes:~$ /challenge/run
Great job! Here is your payment:
pwn.college{sWDw4Dt9nVKMhmoxk06BzX2rOyP.QXyQDO0wCM2kzNzEzW}
```
# INTERRUPTING PROCESSES
**FLAG**:pwn.college{sOPislCZXQn9jnVkcYTN6DSP_QX.QXzQDO0wCM2kzNzEzW}
CODE:
```wsl
Connected!
hacker@processes~interrupting-processes:~$ /challenge/run
I could give you the flag... but I won't, until this process exits. Remember,
you can force me to exit with Ctrl-C. Try it now!
^C
Good job! You have used Ctrl-C to interrupt this process! Here is your flag:
pwn.college{sOPislCZXQn9jnVkcYTN6DSP_QX.QXzQDO0wCM2kzNzEzW}
```
# KILLING MISBEHAVING PROCESSES
**FLAG**:
CODE:
```wsl
hacker@processes~killing-misbehaving-processes:~$ ps auxww | grep /challenge/decoy
hacker       217  0.0  0.0 230696  2560 pts/3    S+   14:04   0:00 grep --color=auto /challenge/decoy
hacker@processes~killing-misbehaving-processes:~$ cat /tmp/flag_fifo
pwn.college{Khx2XSyB1k-q2nLMsYxfJvGa5B.aIkLbcZ7VYzXTAl8-jDt}
pwn.college{KAfLwo-Y3Ww2jq2YYfZVba8Gauo3hzpZrZwrXogaaVBs12j}
pwn.college{sJM9jqmsm5jCuO-Rhc4Z5dxh1L2am6LDU4w2QAoe9n6wFOv}
pwn.college{bErbSlZTSvBY6.f6upy8dx8CDfb2da7YwkRzNo2swlNaysB}
pwn.college{-uC5N1ivT3rN9P5qrhxAAaYZiMdJH4bwR.tAMfJRiizXB4k}
pwn.college{VpK4lpn9.G5skEn2y9SfINldRv8rRrSw7J4WmH9Tv0UZKqS}
pwn.college{6gcOjy.PlF1UR.kB6j5mDFRv7DDD.K9oI3U5GLNhLFpXdhn}
pwn.college{SvDFNAAcaz28Di5yxPIMHDNiUgmzjuO1HX3ihIrph.uTpof}
pwn.college{xkaxyNq1-2jrStH1zsEQX3t.ZNWJlitqa6LqqCK6QCQnKe7}
pwn.college{FIJ1c27CusBc4JGq-KOg2Kqgt3S-JmW3vU.hswrX5MLW.ku}
pwn.college{tFjzLHq7B72oGhorVxDONc7pWykhoj5oNdU3TObLVW-Y.px}
pwn.college{C46hDe7Za7kaSkMzO7R.KYzs-dxaulg4QkBZC1GcBve5frt}
pwn.college{fO0o-dQxOtULpjrMQXk9iuqgajkPBtvs1VzvFPISHl0q6bQ}
pwn.college{WWPBMDleIl-q5a-xWt3xkCS3DEnD9.YROGEZYhIqJC6E2gw}
pwn.college{w9djpz.1L9D420AWkAnZ7PkZNVoSG5RrRmMOTkK20IPvt3q}
pwn.college{rSodCyPT7fbvtCipsJMqk2JK9mFrHvgpgDiUOSc34r6hHra}
pwn.college{lKvhJ5dfPbWyG1S7FHzakPzbfyxTn.-fPOiv-.0EYkbKa9m}
pwn.college{Q.TJHoGrmTE6gBNH.zZr8j9OHFHBRxRKwjJaoEwxbfs3iPg}
pwn.college{ntT5ArYead2uvlteJEZmQ1F3K6EQit78KtKojiJwq9jIBdJ}
pwn.college{BmdGrsGQWE3uGYOFqRTX4M7cVEfB0RbmGmo7YpEGBnDFLv8}
pwn.college{qdNMz8BGc1JySphCiNwQqmlKKYHauwWAUPzO-goxO823rHa}
pwn.college{5lhXJNSpZ.HkDePvsQgUYG9MUAcHkDpA6GJJTyoha9VNexv}
pwn.college{KI0kOVg0n9VKglR9SRschCSYOywgvaQMVOi7M89TJi5jV9z}
pwn.college{f4xJCTeVGI1X0Wc1ln14zkUbDNCySuzsugbZJiU-nfoN80b}
pwn.college{7E4la-Hlv-n0DLHc1yrIjc1VdnsZ.JIML8wfKZECOe4qF4g}
pwn.college{PkCs9l7oiYL7QalmUtL-Avs2XpDUTjZvNTLxMdb.efjtsdF}
pwn.college{agun.TiLOg9CHJkUmcenQ4aUE7BWIy84P4EYInzA5AEbpws}
pwn.college{MfdQREbke9DkA9p4DnX4d6f7oXG5Uw3guz8ULwDz0pZX127}
pwn.college{ypbEDbBWRw1pQqEFbocoswOBuN77sgKvQ7DF9hoCXmCSooZ}
pwn.college{0Zo87Pr20HgUcDpc8jQX5S6J1uHhfSOn8hwIRXaTv-qOdz3}
pwn.college{U5isYPj8as8tWXUwSDuvwKkN5u6ClR.5PidxHZJvHNznxAP}
pwn.college{KV4rPFjD25fiPvSa-RgTNdtaB0hqICVjXauYdAaZBvQzQDr}
pwn.college{znS5g3rdZ2lrNCgABhyeNK2iz2.7ST1tY5qFnevpQAqqGWH}
pwn.college{rh3IuPJl91DKqQivWoNDrKHkolyLQzpf-fWICHHAzSueZPZ}
pwn.college{AFognUvx2pZRlcczGdU8jZHDL2JYbsHJsRGiClMbeb.CYc5}
pwn.college{ColqcmYlL1QERfLir5aN-x-7cCDY-l.hB77m7vKEDfnHhPm}
pwn.college{mHTJ9e3Gae8lSnUI.z9ouLLwndU10miBBJm3WEa9Kszheov}
pwn.college{QKmUSt21cPKs1EX3oaJufFo.fFoYJYjMHi6ELIXXL48KD7e}
pwn.college{o68DgRsfnL5tvW5czDMZwZcPMWVpfp3xTTWLVtbitDF2U0y}
pwn.college{PoeCkNXRqkLokB.gTcLGXrtpNt.jJ1pTTMR7D2DxoILcpfX}
pwn.college{WYsnnu-4YrfP6u6GqAscpQcwLOCJFfdqkugofsuhwOBohmh}
pwn.college{2fjGL7O0k2xdOhNv1ilxxtyRyhjtFWGqPst1HAkEzXpv2S8}
pwn.college{oWVTFeLMoP0ZBXXD3PIwnMY6lkl4tG3AirZry8PJFTEmUzg}
pwn.college{iEevD52eUsFixro8CWIBMr0AYQ9VZYSJlu-4HFPKL7NDtif}
pwn.college{u08bHD-wHmX.8SVs4Bd2dK5c8ds9ffv6sU3becXBwgsA4Lr}
pwn.college{JfRhOosE5wM4HR64.po3ncJ.ylwqi1oxvngIVMkuPdVlK5q}
pwn.college{-FdHjwlW142r6MruolJVpTXOF1B48nppBWsz.2uRTs6tztb}
pwn.college{XvB0HmTy03g8ldlvN9ggO6jZnaqVqTxzUcN3SBo2wkehIBE}
pwn.college{u5Ze3hq.AhTj03JeNoZbPUk9vEKOUciEf-ftXzgQJ6fgqJv}
pwn.college{XFBTEofibIMzzz3v4I7Og45HN66l0ZJQYt.h4wFQodjD.h6}
pwn.college{YkrRZlVJshrlqqfPhLFybdAFIidqC78OE0Q6T55j-m23OOs}
pwn.college{05qy4i1cHKP.B8u13nyrzZ-s5OhzzbZ8eVJUETobn4KwKH5}
pwn.college{8QWxYrk80l1MtZsq0wIQjk-p9X4d9gVO1e6K2NxSyymQK7N}
pwn.college{hhU65ceRR6UOG03k7ToH-EQPsQFFtHAlWXJYAjZk5izrssw}
pwn.college{zo8F8Kf8HXZIqqGJ1tSx8UtXedRy1Qw2XZ-GvX2EMrATIf4}
pwn.college{jIrSZpjGBPke4ROdx6Z.cadEnDWHOnZ-icIchbgVjjGlMXo}
pwn.college{ff.DrfV.gqfapPpnGmog-QcExnRxzFI0sb9Hcuj5iOXE.Cq}
pwn.college{d4G8D24n0-56jo-lnnPN8wycMB89NCeN-aooiIdvN6mHa0z}
pwn.college{2Jx9pXQer9XfhgrgDPpmLH2eXx88UBs.uQ9r5HTwgGwcFgU}
pwn.college{GZjHhZAbFz33LWmP28sguj3VYA3.NEt2Eih36CakfT.AUCB}
pwn.college{6i3UJPyfFpyXw2a8NG0cjUw4jieHIUGrdzibvbXi.ULPSPs}
pwn.college{ipZTL9KbRlECjoKQ7blthnmMMXY2xWF6GwObB6NcJsRigbI}
```
# SUSPENDING PROCESSES
**FLAG**:pwn.college{8QeH1TnPb-qhzAk-K1A4rHjCzkk.QX1QDO0wCM2kzNzEzW}
code:
```wsl
hacker@processes~suspending-processes:~$ /challenge/run
I'll only give you the flag if there's already another copy of me running in
this terminal... Let's check!

UID          PID    PPID  C STIME TTY          TIME CMD
root         138     129  0 14:31 pts/0    00:00:00 bash /challe
root         140     138  0 14:31 pts/0    00:00:00 ps -f

I don't see a second me!

To pass this level, you need to suspend me and launch me again! You can
background me with Ctrl-Z or, if you're not ready to do that for whatever
reason, just hit Enter and I'll exit!
^Z
[1]+  Stopped                 /challenge/run
hacker@processes~suspending-processes:~$ /challenge/run
I'll only give you the flag if there's already another copy of me running in
this terminal... Let's check!

UID          PID    PPID  C STIME TTY          TIME CMD
root         138     129  0 14:31 pts/0    00:00:00 bash /challe
root         145     129  0 14:32 pts/0    00:00:00 bash /challe
root         147     145  0 14:32 pts/0    00:00:00 ps -f

Yay, I found another version of me! Here is the flag:
pwn.college{8QeH1TnPb-qhzAk-K1A4rHjCzkk.QX1QDO0wCM2kzNzEzW}
```
# RESUMING PROCESSES
**FLAG**:pwn.college{wEvItvs8pE9vRRmFCKxOwR3YQ0g.QX2QDO0wCM2kzNzEzW}
code:
```wsl
Connected!
hacker@processes~resuming-processes:~$  /challenge/run
Let's practice resuming processes! Suspend me with Ctrl-Z, then resume me with
the 'fg' command! Or just press Enter to quit me!
^Z
[1]+  Stopped                 /challenge/run
hacker@processes~resuming-processes:~$ jobs
[1]+  Stopped                 /challenge/run
hacker@processes~resuming-processes:~$ /challenge/run
Let's practice resuming processes! Suspend me with Ctrl-Z, then resume me with
the 'fg' command! Or just press Enter to quit me!
fg
Goodbye!
hacker@processes~resuming-processes:~$ jobs
[1]+  Stopped                 /challenge/run
hacker@processes~resuming-processes:~$ fg %1
/challenge/run
I'm back! Here's your flag:
pwn.college{wEvItvs8pE9vRRmFCKxOwR3YQ0g.QX2QDO0wCM2kzNzEzW}
```
# BACKGROUNDING PROCESSES
**FLAG**:pwn.college{k6VQ2WIVOsw38xKyKnhmWSNSENG.QX3QDO0wCM2kzNzEzW}
code:
```wsl
Connected!
hacker@processes~backgrounding-processes:~$ /challenge/run
I'll only give you the flag if there's already another copy of me running *and
not suspended* in this terminal... Let's check!

UID          PID STAT CMD
root         137 S+   bash /challenge/run
root         139 R+   ps -o user=UID,pid,stat,cmd

I don't see a second me!

To pass this level, you need to suspend me, resume the suspended process in the
background, and then launch a new version of me! You can background me with
Ctrl-Z (and resume me in the background with 'bg') or, if you're not ready to
do that for whatever reason, just hit Enter and I'll exit!
^Z
[1]+  Stopped                 /challenge/run
hacker@processes~backgrounding-processes:~$ bg
[1]+ /challenge/run &
hacker@processes~backgrounding-processes:~$


Yay, I'm now running the background! Because of that, this text will probably
overlap weirdly with the shell prompt. Don't panic; just hit Enter a few times
to scroll this text out.

hacker@processes~backgrounding-processes:~$ /challenge/run
I'll only give you the flag if there's already another copy of me running *and
not suspended* in this terminal... Let's check!

UID          PID STAT CMD
root         137 S    bash /challenge/run
root         147 S    sleep 6h
root         148 S+   bash /challenge/run
root         150 R+   ps -o user=UID,pid,stat,cmd

Yay, I found another version of me running in the background! Here is the flag:
pwn.college{k6VQ2WIVOsw38xKyKnhmWSNSENG.QX3QDO0wCM2kzNzEzW}
```
# FOREGROUNDING PROCESSES
**FLAG**:pwn.college{4UlPuMiMrB9DoNJeEzaevApkKxm.QX4QDO0wCM2kzNzEzW}
code:
```wsl
Connected!
hacker@processes~foregrounding-processes:~$ /challenge/run
To pass this level, you need to suspend me, resume the suspended process in the
background, and *then* foreground it without re-suspending it! You can
background me with Ctrl-Z (and resume me in the background with 'bg') or, if
you're not ready to do that for whatever reason, just hit Enter and I'll exit!
^Z
[1]+  Stopped                 /challenge/run
hacker@processes~foregrounding-processes:~$ bg
[1]+ /challenge/run &
hacker@processes~foregrounding-processes:~$


Yay, I'm now running the background! Because of that, this text will probably
overlap weirdly with the shell prompt. Don't panic; just hit Enter a few times
to scroll this text out. After that, resume me into the foreground with 'fg';
I'll wait.

hacker@processes~foregrounding-processes:~$ fg
/challenge/run
YES! Great job! I'm now running in the foreground. Hit Enter for your flag!

pwn.college{4UlPuMiMrB9DoNJeEzaevApkKxm.QX4QDO0wCM2kzNzEzW}
```
# STARTING BACKGROUNDED PROCESSES
**FLAG**:pwn.college{09ZAZAHxafj_P3pmahS-muJaFN9.QX5QDO0wCM2kzNzEzW}
code:
```wsl
Connected!
hacker@processes~starting-backgrounded-processes:~$ /challenge/run
You've started me in the foreground! You must start me in the background (by
appending '&' to the command) to get the flag!
hacker@processes~starting-backgrounded-processes:~$ /challenge/run &
[1] 141
hacker@processes~starting-backgrounded-processes:~$


Yay, you started me in the background! Because of that, this text will probably
overlap weirdly with the shell prompt, but you're used to that by now...

Anyways! Here is your flag!
pwn.college{09ZAZAHxafj_P3pmahS-muJaFN9.QX5QDO0wCM2kzNzEzW}
```
# PROCESS EXIT CODE
**FLAG**:pwn.college{IG9f694fVUsafbWS1kt_tp-fJWm.QX5YDO1wCM2kzNzEzW}
code:
```wsl
Connected!
hacker@processes~process-exit-codes:~$ /challenge/get-code
Exiting with an error code!
hacker@processes~process-exit-codes:~$ /challenge/submit-code $?
CORRECT! Here is your flag:
pwn.college{IG9f694fVUsafbWS1kt_tp-fJWm.QX5YDO1wCM2kzNzEzW}
```
