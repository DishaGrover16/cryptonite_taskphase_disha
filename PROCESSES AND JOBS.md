**PROCESSES AND JOBS**

***1.Listing Processes***

In this challenge, we had to find /challenge/run file under a random filename so after using commands ```ps -ef```
and ```ps -aux``` as both show commands. "Standard" Syntax: in this syntax, you can use -e to list "every" process and -f for a "full format" output, including arguments. These can be combined into a single argument -ef.

"BSD" Syntax: in this syntax, you can use a to list processes for all users, x to list processes that aren't running in a terminal, and u for a "user-readable" output. These can be combined into a single argument aux. After reading the output, I found a command similar to /challenge/run and when I ran it, I got the flag.

```
Connected!
hacker@processes~listing-processes:~$ ps -ef
UID          PID    PPID  C STIME TTY          TIME CMD
root           1       0  0 05:59 ?        00:00:00 /sbin/docker-init -- /nix/var/nix/profiles/default/bin/dojo-init /ru
root           7       1  0 05:59 ?        00:00:00 /run/dojo/bin/sleep 6h
root          68       1  0 05:59 ?        00:00:00 /challenge/17087-run-4394
root          72      68  0 05:59 ?        00:00:00 sleep 6h
hacker        73       0  1 05:59 pts/0    00:00:00 /run/dojo/bin/ssh-entrypoint
hacker        90      73  0 05:59 pts/0    00:00:00 ps -ef
hacker@processes~listing-processes:~$ ps -aux
USER         PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root           1  0.2  0.0   1056   640 ?        Ss   05:59   0:00 /sbin/docker-init -- /nix/var/nix/profiles/default/bi
root           7  0.0  0.0   5052  2240 ?        S    05:59   0:00 /run/dojo/bin/sleep 6h
root          68  0.0  0.0   4132  2560 ?        S    05:59   0:00 /challenge/17087-run-4394
root          72  0.0  0.0   2744  1280 ?        S    05:59   0:00 sleep 6h
hacker        73  0.2  0.0   5372  3840 pts/0    Ss   05:59   0:00 /run/dojo/bin/ssh-entrypoint
hacker        91  0.0  0.0   7868  3200 pts/0    R+   06:00   0:00 ps -aux
hacker@processes~listing-processes:~$ /challenge/17087-run-4394
Yahaha, you found me! Here is your flag:
pwn.college{odhkIxzPGXkzAndYyrVMMJYYmS0.dhzM4QDLwQDO0czW}
Now I will sleep for a while (so that you could find me with 'ps').
```

***2.Killing Processes***

After listing all the processes working in the terminal, I found th process PID of /challenge/dont_run. Using ```kill``` command and the PID number as an argument, I killed the command ```/challenge/dont_run```. This further allowed the command ```/challenge/run``` to give me an output.

```
Connected!
hacker@processes~killing-processes:~$ ps -ef
UID          PID    PPID  C STIME TTY          TIME CMD
root           1       0  0 06:07 ?        00:00:00 /sbin/docker-init -- /nix/var/nix/profiles/default/bin/dojo-init /run/dojo/bin/sl
root           7       1  0 06:07 ?        00:00:00 /run/dojo/bin/sleep 6h
root          71       1  0 06:07 ?        00:00:00 su -c /challenge/.launcher hacker
hacker        73      71  0 06:07 ?        00:00:00 /challenge/dont_run
hacker        74      73  0 06:07 ?        00:00:00 sleep 6h
hacker        75       0  0 06:07 pts/0    00:00:00 /run/dojo/bin/ssh-entrypoint
hacker        92      75  0 06:08 pts/0    00:00:00 ps -ef
hacker@processes~killing-processes:~$ ps -aux
USER         PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root           1  0.2  0.0   1056   640 ?        Ss   06:07   0:00 /sbin/docker-init -- /nix/var/nix/profiles/default/bin/dojo-init /
root           7  0.0  0.0   5052  2560 ?        S    06:07   0:00 /run/dojo/bin/sleep 6h
root          71  0.0  0.0   4732  2880 ?        S    06:07   0:00 su -c /challenge/.launcher hacker
hacker        73  0.0  0.0   4976  3200 ?        Ss   06:07   0:00 /challenge/dont_run
hacker        74  0.0  0.0   5052  2240 ?        S    06:07   0:00 sleep 6h
hacker        75  0.1  0.0   5372  4160 pts/0    Ss   06:07   0:00 /run/dojo/bin/ssh-entrypoint
hacker        93  0.0  0.0   7868  3520 pts/0    R+   06:08   0:00 ps -aux
hacker@processes~killing-processes:~$ kill 73
hacker@processes~killing-processes:~$ /challenge/run
Great job! Here is your payment:
pwn.college{koZvb5U52CNLx_6jCTYnUNRlu8f.dJDN4QDLwQDO0czW}
```

***3.Interrupting Processes***

In this challenge, when I ran the ```/challenge/run``` command, it gave me the instruction to exit the process first to get the flag. Thus using ctrl+c I interrupted the process and caught the flag.

```
Connected!
hacker@processes~interrupting-processes:~$ /challenge/run
I could give you the flag... but I won't, until this process exits. Remember,
you can force me to exit with Ctrl-C. Try it now!
^C
Good job! You have used Ctrl-C to interrupt this process! Here is your flag:
pwn.college{s5Hg4wUqnMGVq007o1FF_yXeqjp.dNDN4QDLwQDO0czW}
```

***4.Suspending Processes***

On running the command ```/challenge/run```, we got to know that another of copy of the command was running in the terminal. So to suspend it, we had to press ctrl+z. Then on running the command, I caught the flag.

```
Connected!
hacker@processes~suspending-processes:~$ /challenge/run
I'll only give you the flag if there's already another copy of me running in
this terminal... Let's check!

UID          PID    PPID  C STIME TTY          TIME CMD
root          82      65  0 06:26 pts/0    00:00:00 bash /challenge/run
root          84      82  0 06:26 pts/0    00:00:00 ps -f

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
root          82      65  0 06:26 pts/0    00:00:00 bash /challenge/run
root          89      65  0 06:26 pts/0    00:00:00 bash /challenge/run
root          91      89  0 06:26 pts/0    00:00:00 ps -f

Yay, I found another version of me! Here is the flag:
pwn.college{UF4kMJXkEBUOWzCy8YlhyO2t95n.dVDN4QDLwQDO0czW}
```

***5.Resuming Processes***

In this challenge, first the challenge's run was required to be suspended and then resumed so I used ctrl+z and fg respectively. On the execution, I got the flag.

```
Connected!
hacker@processes~resuming-processes:~$ /challenge/run
Let's practice resuming processes! Suspend me with Ctrl-Z, then resume me with
the 'fg' command! Or just press Enter to quit me!
^Z
[1]+  Stopped                 /challenge/run
hacker@processes~resuming-processes:~$ fg
/challenge/run
I'm back! Here's your flag:
pwn.college{8JmoC4IH747iPkuXRnPnxJ_btm-.dZDN4QDLwQDO0czW}
```

***6.Backgrouding Processes***

I learned that we can also resume the process in background using bg command. Firstly, I suspended the process in the terminal and resumed it in the background. Then on executing ```/challenge/run```, I got the flag.

```
hacker@processes~backgrounding-processes:~$ /challenge/run
I'll only give you the flag if there's already another copy of me running *and
not suspended* in this terminal... Let's check!

UID          PID STAT CMD
root          82 S+   bash /challenge/run
root          84 R+   ps -o user=UID,pid,stat,cmd

I don't see a second me!

To pass this level, you need to suspend me, resume the suspended process in the
background, and then launch a new version of me! You can background me with
Ctrl-Z (and resume me in the background with 'bg') or, if you're not ready to
do that for whatever reason, just hit Enter and I'll exit!
^Z
[1]+  Stopped                 /challenge/run
hacker@processes~backgrounding-processes:~$ bg
[1]+ /challenge/run &



Yay, I'm now running the background! Because of that, this text will probably
overlap weirdly with the shell prompt. Don't panic; just hit Enter a few times
to scroll this text out.
hacker@processes~backgrounding-processes:~$ /challenge/run
I'll only give you the flag if there's already another copy of me running *and
not suspended* in this terminal... Let's check!

UID          PID STAT CMD
root          82 S    bash /challenge/run
root          92 S    sleep 6h
root          93 S+   bash /challenge/run
root          95 R+   ps -o user=UID,pid,stat,cmd

Yay, I found another version of me running in the background! Here is the flag:
pwn.college{sKQ6ttzKdGrhaQSALjeqAL4io9x.ddDN4QDLwQDO0czW}
```

***7.Foregrounding Processes***

In this challenge, first, we have to suspend the process and then resume it in the background. After doing that we have to foreground it without suspending it. ```fg``` is the command used to foreground whereas ```bg``` is used to resume it in background. On following the above instructions, I got the flag.

```
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



Yay, I'm now running the background! Because of that, this text will probably
overlap weirdly with the shell prompt. Don't panic; just hit Enter a few times
to scroll this text out. After that, resume me into the foreground with 'fg';
I'll wait.
hacker@processes~foregrounding-processes:~$ fg
/challenge/run
YES! Great job! I'm now running in the foreground. Hit Enter for your flag!

pwn.college{MnYWpgOHO79FPrNbgU-vdbIlaU9.dhDN4QDLwQDO0czW}
```

***8.Starting Background Processes***

We don't have to suspend processes to background them: instead, we can start the background right off after appending a ```&``` to the command. Therefore, I used a & after the command /challenge/run to start it in the background.

```
Connected!
hacker@processes~starting-backgrounded-processes:~$ /challenge/run &
[1] 82

hacker@processes~starting-backgrounded-processes:~$ Yay, you started me in the background! Because of that, this text will probably
overlap weirdly with the shell prompt, but you're used to that by now...

Anyways! Here is your flag!
```

***9.Process Exit Codes***

We learned that commands that succeed typically return 0 and commands that fail typically return a non-zero value, most commonly 1 but sometimes an error code that identifies a specific failure mode. In this challenge on running the command ```/challenge/get-code``` we received an error code and when I checked the command returned 194 which is a non-zero number and thus our command failed. On further following instructions I executed ```/challenge/submit-code 194``` which is the correct command and thus it also returned flag and 1 upon checking.

```
Connected!
hacker@processes~process-exit-codes:~$ /challenge/get-code
Exiting with an error code!
hacker@processes~process-exit-codes:~$ echo $?
194
hacker@processes~process-exit-codes:~$ /challenge/submit-code 194
CORRECT! Here is your flag:
pwn.college{A9NtUKp1fJ5BfH5noY7YQ19VUaa.dljN4UDLwQDO0czW}
hacker@processes~process-exit-codes:~$ echo $?
0
```
