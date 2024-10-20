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

