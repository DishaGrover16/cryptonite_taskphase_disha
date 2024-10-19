**Perceiving Permissions**

***1.Changing File Ownership***

We can change the ownership of files. This is done via the chown (change owner) command: chown [username] [file] 
In this challenge, we first changed the ownership of the flag file to hacker and then executed the cat command on the flag file to get the flag. 

```
Connected!
hacker@permissions~changing-file-ownership:~$ chown hacker /flag
hacker@permissions~changing-file-ownership:~$ cat flag
cat: flag: No such file or directory
hacker@permissions~changing-file-ownership:~$ cat /flag
pwn.college{cEIrA-zvYJIACFt4zPNB_cfakxq.dFTM2QDLwQDO0czW}
```

***2.Groups and Files***

In this challenge, we have to change the ownership of the group flag from root to the hacker user to read the flag. Thus using the command ```chgrp hacker /flag``` I changed the ownership and used the cat command to read the flag.

```
Connected!
hacker@permissions~groups-and-files:~$ chgrp hacker /flag
hacker@permissions~groups-and-files:~$ cat /flag
pwn.college{smFURMcOsfIXlr5kU3xufIDOHJP.dFzNyUDLwQDO0czW}
```

***3. Fun with Group Names***

In this challenge, we had to first identify the group in which the hacker belongs and then chgrp to change the ownership of the flag in order to cat the flag and read it.  

```
Connected!
hacker@permissions~fun-with-groups-names:~$ id
uid=1000(hacker) gid=1000(grp18440) groups=1000(grp18440)
hacker@permissions~fun-with-groups-names:~$ chgrp grp18440 /flag
hacker@permissions~fun-with-groups-names:~$ cat /flag
pwn.college{kaFxAcpazxOfm5Ja3EhjMlNqsl-.dJzNyUDLwQDO0czW}
```

***4.Changing Permissions***

File permissions can also be changed. This is done with the chmod (change mode) command. The basic usage for chmod is: ```chmod [OPTIONS] MODE FILE```. Thus i executed the command ```chmod ugo+rwx /flag```. chmod with arguments ugo(+/-)rwx, where ugo is the user, group, or other, (+/-) is adding or removing permissions and rwx is read, write, and execute permissions. Thus after executing ```cat /flag``` , I got the flag.

```
Connected!
hacker@permissions~changing-permissions:~$ chmod ugo+rwx /flag
hacker@permissions~changing-permissions:~$ cat /flag
pwn.college{cUiZ4okPAWmr9FWyexLfZrXpiFg.dNzNyUDLwQDO0czW}
```

***5.Executable Files***

In this challenge, we had to make the command ```/challenge/run``` executable. Thus for this, we had to change some permissions. After changing the permissions, on executing ```/challenge/run```, I got the flag.

```
Connected!
hacker@permissions~executable-files:~$ chmod ugo+rwx /challenge/run
hacker@permissions~executable-files:~$ /challenge/run
Successful execution! Here is your flag:
pwn.college{EHGT8UesA2JSnjkElp9mByHhXSD.dJTM2QDLwQDO0czW}
```

***6.Permission Tweaking Practice***

```


