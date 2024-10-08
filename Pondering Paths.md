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
