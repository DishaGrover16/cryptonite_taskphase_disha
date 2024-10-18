**SHELL VARIABLES**

***1.Printing Variables***

As we know that ```echo``` prints stuff. Now if we want to print out the flag variable we have to use the argument ```$FLAG``` with ```echo``` as a command.

```
Connected!
hacker@variables~printing-variables:~$ echo $FLAG
pwn.college{g1oSoHLoHdCG3sZay0ybMHdDiHt.ddTN1QDLwQDO0czW}
```

***2.Setting Variables***

I learned how to assign a value to a variable. ```PWN=COLLEGE``` with no spaces in between would assign the value of COLLEGE to the variable PWN. Thus, after setting the PWN variable properly, I got the flag.

```
Connected!
hacker@variables~setting-variables:~$ PWN=COLLEGE
You've set the PWN variable properly! As promised, here is the flag:
pwn.college{kz8dM0GAFpFJucRW7Bpz8IXzvqD.dlTN1QDLwQDO0czW}
hacker@variables~setting-variables:~$ echo $PWN
COLLEGE
You've set the PWN variable properly! As promised, here is the flag:
pwn.college{kz8dM0GAFpFJucRW7Bpz8IXzvqD.dlTN1QDLwQDO0czW}
```

***3.Multi-word Variables***

I need to have no spaces around the =. When the shell sees a space, it ends the variable assignment and interprets the next word as a command. So, to avoid this, I have to quote the entire sting I want to assign to the variable. Thus I ran the command PWN="COLLEGE YEAH" to get the flag.

```
Connected!
hacker@variables~multi-word-variables:~$ PWN="COLLEGE YEAH"
You've set the PWN variable properly! As promised, here is the flag:
pwn.college{gHfsRdOUo5R4rCZtylTFcWQ6akD.dBjN1QDLwQDO0czW}
hacker@variables~multi-word-variables:~$ echo $PWN
COLLEGE YEAH
You've set the PWN variable properly! As promised, here is the flag:
pwn.college{gHfsRdOUo5R4rCZtylTFcWQ6akD.dBjN1QDLwQDO0czW}
```

***4.Exporting Variables***

In this challenge, we had to invoke /challenge/run with the PWN variable exported and set to the value COLLEGE, and the COLLEGE variable set to the value PWN but not exported. Thus I followed the commands and used ```export``` as a command as when we export the variables, they are passed into the environment variables of child processes.

```
Connected!
hacker@variables~exporting-variables:~$ PWN=COLLEGE
You've set the PWN variable to the proper value!
hacker@variables~exporting-variables:~$ export PWN
You've set the PWN variable to the proper value!
hacker@variables~exporting-variables:~$ COLLEGE=PWN
You've set the PWN variable to the proper value!
You've set the COLLEGE variable to the proper value!
hacker@variables~exporting-variables:~$ sh
sh-5.2$ echo "PWN is: $PWN"
PWN is: COLLEGE
sh-5.2$ echo "COLLEGE is: $COLLEGE"
COLLEGE is:
sh-5.2$ /challenge/run
CORRECT!
You have exported PWN=COLLEGE and set, but not exported, COLLEGE=PWN. Great
job! Here is your flag:
pwn.college{IDKwlbWfSkgLxAAD9FQKWScaxxj.dJjN1QDLwQDO0czW}
```
***5.Printing Exported Variables***

env command: it'll print out every exported variable set in your shell. Thus instead of using ```echo``` as a command for reading the variables, I used ```env```

```
Connected!
hacker@variables~printing-exported-variables:~$ env $FLAG
env: ‘pwn.college{oPST-XsYhJUh7ZuXo3oYI_EsL_1.dhTN1QDLwQDO0czW}’: No such file or directory
```

***6.Storing Command Output***

In this challenge, we have to store the output of some command ```/challenge/run``` into a variable ```PWN```. Thus, I first stored the output of /challenge/run in PWN variable and then printed that variable using echo command. This way I got the flag.

```
Connected!
hacker@variables~storing-command-output:~$ PWN=$(/challenge/run)
Congratulations! You have read the flag into the PWN variable. Now print it out
and submit it!
hacker@variables~storing-command-output:~$ echo "$PWN"
pwn.college{kyI3xR9iMtW202xCU6OSzl-54Q0.dVzN0UDLwQDO0czW}
```

***7.Reading Input***

We use the read function to read input from the user. Thus, I first used the read function in the challenge to assign a value to the variable ```PWN```.

```
Connected!
hacker@variables~reading-input:~$ echo $PWN  
hacker@variables~reading-input:~$ read PWN
COLLEGE
You've set the PWN variable properly! As promised, here is the flag:
pwn.college{459-AzOzhj9vzVPjEpQyZckNjZr.dhzN1QDLwQDO0czW}
```

***8.Reading Files***


In this challenge, I redirected ```/challenge/read_me``` into the standard input of read, and so when ```read``` reads into ```PWN```, it reads from the file. Thus after redirecting, I got the flag.

```
Connected!
hacker@variables~reading-files:~$ echo PWN > /challenge/read_me
ssh-entrypoint: /challenge/read_me: Permission denied
hacker@variables~reading-files:~$ read PWN < /challenge/read_me
You've set the PWN variable properly! As promised, here is the flag:
pwn.college{wFGrdiVxKcFRV5OJomQAeS8_xr2.dBjM4QDLwQDO0czW}
hacker@variables~reading-files:~$ echo $PWN
icXEwSPwewJTI4WZjeOeF7zzmBm35cKFcwmrVBqUrPdRfJ
You've set the PWN variable properly! As promised, here is the flag:
pwn.college{wFGrdiVxKcFRV5OJomQAeS8_xr2.dBjM4QDLwQDO0czW}
```


