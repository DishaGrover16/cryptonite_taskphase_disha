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
