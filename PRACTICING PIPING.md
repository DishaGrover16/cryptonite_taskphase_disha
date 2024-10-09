**PRACTICING PIPING**

***1.Redirecting Output***

In this challenge, you must use this input redirection to write the word PWN (all uppercase) to the filename COLLEGE (all uppercase).Thus with our knowledge, we used the command ```echo PWN > COLLEGE``` to get the flag.

```
Connected!
You have created the COLLEGE file and wrote the right value to it, but it
doesn't look like you did it via input redirection.
hacker@piping~redirecting-output:~$ echo PWN > COLLEGE
Correct! You successfully redirected 'PWN' to the file 'COLLEGE'! Here is your
flag:
pwn.college{s0S-eQmL8IbzCGMxgPP3e1BU91T.dRjN1QDLwQDO0czW}
```

***2.Redirecting More Output***


***5. Redirecting Input***

According to the challenge, PWN file should contain the value COLLEGE. Thus  first directed COLLEGE to PWN file. Then the challenge requires to redirect PWN file to /challenge/run. Thus we got the flag.

```
Connected!
hacker@piping~redirecting-input:~$  echo COLLEGE > PWN
hacker@piping~redirecting-input:~$ /challenge/run < PWN
Reading from standard input...
Correct! You have redirected the PWN file into my standard input, and I read
the value 'COLLEGE' out of it!
Here is your flag:
pwn.college{IDqvmzmJUrUj3ZDJG43XPfc09g4.dBzN1QDLwQDO0czW}
```

***6. Grepping Stored Results***

```
