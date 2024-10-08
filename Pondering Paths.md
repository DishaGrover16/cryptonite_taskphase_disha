**PONDERING PATHS**

***1.The Root***

The task was to invoke the pwn program using its absolute path in order to capture the flag. 
Thus the / was to used to start the path of pwn from the root directory i.e. absolute path was used.

```
Connected!
hacker@paths~the-root:~$ /pwn
BOOM!!!
Here is your flag:
pwn.college{AemWnNYxxl2ed6xmq5fGEvdARo5.dhzN5QDLwQDO0czW}
```

***2.Program and Absolute Paths***

We want to execute the run file that is in the challenge directory that is, in turn, in the / directory using its absolute path.
Run is located in the challenge directory which is in turn located in the / directory. Therefore, the absolute path becomes 
/challenge/run

```
Connected!
hacker@paths~program-and-absolute-paths:~$ /challenge/run
Correct!!!
/challenge/run is an absolute path! Here is your flag:
pwn.college{UGcD7tqbtMaYpin78Qg6StAwVPn.dVDN1QDLwQDO0czW}
```

***3.Position thy self***

The challenge required us to move to the correct directory using the command cd.In order to find the correct directory, I ran /challenge/run.

```
hacker@paths~position-thy-self:~$ /challenge/run
Incorrect...
You are not currently in the /usr/share/build-essential directory.
Please use the `cd` utility to change directory appropriately.
```
The correct directory i.e. /usr/share/build-essential was thus located and correct commands were executed and I got the flag.

```
hacker@paths~position-thy-self:~$ cd /usr/share/build-essential
hacker@paths~position-thy-self:/usr/share/build-essential$ /challenge/run
Correct!!!
/challenge/run is an absolute path, invoked from the right directory!
Here is your flag:
pwn.college{EIG1rK8od8b2HF2VwEyOaDfraFU.dZDN1QDLwQDO0czW}
```

***4.Position Elsewhere***

The requirement of the challenge was to find the correct directory and execute the command /challenge/run. First, I ran the command to find the correct directory and thus finally executed it after cding into that directory. This way I got the flag.

```
Connected!
hacker@paths~position-elsewhere:~$ /challenge/run
Incorrect...
You are not currently in the /proc/67/fd directory.
Please use the `cd` utility to change directory appropriately.
hacker@paths~position-elsewhere:~$ cd /proc/67/fd
hacker@paths~position-elsewhere:/proc/67/fd$ /challenge/run
Correct!!!
/challenge/run is an absolute path, invoked from the right directory!
Here is your flag:
pwn.college{sWgiLHJw6Wcoe-AYgbRR0NOF0ed.ddDN1QDLwQDO0czW}
```

***5.Position Yet Elsewhere***

The requirement of the challenge was to find the correct directory and execute the command /challenge/run. First, I ran the command to find the correct directory and thus finally executed it after cding into that directory. This way I got the flag.
```
hacker@paths~position-yet-elsewhere:~$ /challenge/run
Incorrect...
You are not currently in the /usr/share/doc directory.
Please use the `cd` utility to change directory appropriately.
hacker@paths~position-yet-elsewhere:~$ cd /usr/share/doc
hacker@paths~position-yet-elsewhere:/usr/share/doc$ /challenge/run
Correct!!!
/challenge/run is an absolute path, invoked from the right directory!
Here is your flag:
pwn.college{oZWV8BGI_LLBheg6MtZ6s8NwMyW.dhDN1QDLwQDO0czW}
```

***6.implicit relative paths, from /***

Since the current working directory is /, it was important to change directory to the root directory. I then implemented /challenge/run which is wrong as it is a absolute path and not a relative one.

```
Connected!
hacker@paths~implicit-relative-paths-from-:~$ cd /
hacker@paths~implicit-relative-paths-from-:/$ /challenge/run
Incorrect...
You invoked this challenge with an absolute path. This challenge needs a relative path!
```

Since the path is supposed to be relative and not absolute challenge/run needed to be implemented. Thus I finally got the flag.

```
hacker@paths~implicit-relative-paths-from-:/$ challenge/run
Correct!!!
challenge/run is a relative path, invoked from the right directory!
Here is your flag:
pwn.college{oHTmmg4UlzAOyluXPy10iEpSatD.dlDN1QDLwQDO0czW}
```

***7. explicit relative paths, from /***

. represents the current working directory and relative paths are based on the current working directories. Thus the command to be implemented was ./challenge/run in order to get the flag.

```
Connected!
hacker@paths~explicit-relative-paths-from-:~$ cd /
hacker@paths~explicit-relative-paths-from-:/$ ./challenge/run
Correct!!!
./challenge/run is a relative path, invoked from the right directory!
Here is your flag:
pwn.college{shGYnPZOHCI2CM1OSmX1aaHck1D.dBTN1QDLwQDO0czW}
```

***8.implicit relative path***

As we know that Linux explicitly avoids automatically looking in the current directory when you provide a "naked" path. Thus to launch run command in this case, specifying a challenge directory was important. Moreover since . represents a current directory, therefore to launch run in /challenge directory, the command ./run can be put to use in order to get the flag.

```
Connected!
hacker@paths~implicit-relative-path:~$ cd /challenge
hacker@paths~implicit-relative-path:/challenge$ ./run
Correct!!!
./run is a relative path, invoked from the right directory!
Here is your flag:
pwn.college{oolCmCTQqDMp5ebp8Bd3oNZ3YgU.dFTN1QDLwQDO0czW}
```

***9.home sweet home***

In this challenge, /challenge/run will write a copy of the flag to any file you specify as an argument on the commandline, with these constraints:

1.Your argument must be an absolute path.
2.The path must be inside your home directory.
3.Before expansion, your argument must be three characters or less.
Due to rules and constraints path between home directory and argument is less than 3 characters there ~/d command was used. 

``` Connected!
hacker@paths~home-sweet-home:~$ /challenge/run ~/d
Writing the file to /home/hacker/d!
... and reading it back to you:
pwn.college{g9clYHIzWwpQ4OVkHblWVD_YZIx.dNzM4QDLwQDO0czW}
```



