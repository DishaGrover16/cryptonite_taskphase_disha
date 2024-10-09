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

I redirected the output of ```/challenge/run``` to the file myflag. To read the flag, I used cat as my command.

```
Connected!
hacker@piping~redirecting-more-output:~$ /challenge/run > myflag
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge will check that output is redirected to a specific file path : myflag
[INFO] - the challenge will output a reward file if all the tests pass : /flag

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] If you pass these checks, you will receive the /flag file.

[TEST] You should have redirected my stdout to a file called myflag. Checking...

[PASS] The file at the other end of my stdout looks okay!
[PASS] Success! You have satisfied all execution requirements.
hacker@piping~redirecting-more-output:~$ cat myflag

[FLAG] Here is your flag:
[FLAG] pwn.college{s1oL4yJBWgaBGDo8hhrWCZIzJzv.dVjN1QDLwQDO0czW}
```

***3.Appending Output***



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

