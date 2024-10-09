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

Running ```/challenge/run``` with an append-mode redirect of the output to the file /home/hacker/the-flag because we know that on redirecting in truncation mode (>), the second half will overwrite the first and we won't get the flag!
Then after using append mode of redirect we read the file /home/hacker/the-flag with cat command to get the flag.

```
Connected!
hacker@piping~appending-output:~$ /challenge/run >> /home/hacker/the-flag
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge will check that output is redirected to a specific file path : /home/hacker/the-flag

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] Good luck!

[TEST] You should have redirected my stdout to a file called /home/hacker/the-flag. Checking...

[HINT] File descriptors are inherited from the parent, unless the FD_CLOEXEC is set by the parent on the file descriptor.
[HINT] For security reasons, some programs, such as python, do this by default in certain cases. Be careful if you are
[HINT] creating and trying to pass in FDs in python.

[PASS] The file at the other end of my stdout looks okay!
[PASS] Success! You have satisfied all execution requirements.
I will write the flag in two parts to the file /home/hacker/the-flag! I'll do
the first write directly to the file, and the second write, I'll do to stdout
(if it's pointing at the file). If you redirect the output in append mode, the
second write will append to (rather than overwrite) the first write, and you'll
get the whole flag!
hacker@piping~appending-output:~$ cat /home/hacker/the-flag
 |
\|/ This is the first half:
 v
pwn.college{ENmFbGEtbamq2oLJgLciAxppxaw.ddDM5QDLwQDO0czW}
                              ^
     that is the second half /|\
                              |

If you only see the second half above, you redirected in *truncate* mode (>)
rather than *append* mode (>>), and so the write of the second half to stdout
overwrote the initial write of the first half directly to the file. Try append
mode!
```

***4.Redirecting Errors***

Firstly, I redirected the output of /challenge/run to myflag and then redirected its errors to a file called instructions. Thus after using cat command on myflag, I got the flag.

```
Connected!
hacker@piping~redirecting-errors:~$ /challenge/run > myflag 2> instructions
hacker@piping~redirecting-errors:~$ cat myflag

[FLAG] Here is your flag:
[FLAG] pwn.college{wn99pcXrXgmBYoM0-oiXmj5aPJt.ddjN1QDLwQDO0czW}
```



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

Firstly I redirected the output of /challenge/run to /tmp/data.txt file. Using grep command to find "pwn.college" in the file helped me grab the flag.

```
Connected!
hacker@piping~grepping-stored-results:~$ /challenge/run > /tmp/data.txt
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge will check that output is redirected to a specific file path : /tmp/data.txt
[INFO] - the challenge will output a reward file if all the tests pass : /challenge/.data.txt

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] If you pass these checks, you will receive the /challenge/.data.txt file.

[TEST] You should have redirected my stdout to a file called /tmp/data.txt. Checking...

[HINT] File descriptors are inherited from the parent, unless the FD_CLOEXEC is set by the parent on the file descriptor.
[HINT] For security reasons, some programs, such as python, do this by default in certain cases. Be careful if you are
[HINT] creating and trying to pass in FDs in python.

[PASS] The file at the other end of my stdout looks okay!
[PASS] Success! You have satisfied all execution requirements.
hacker@piping~grepping-stored-results:~$ grep "pwn.college" /tmp/data.txt
pwn.college{EDJdVbxKLqsA9dmc7c8rq7Q2vy3.dhTM4QDLwQDO0czW}
```

***7.Grepping Live Output***

Standard output from the command to the left of the pipe will be connected to (piped into) the standard input of the command to the right of the pipe. Thus I used the pipe operator to transfer the standard output of ```/challenge/run``` to standard input of the grep command. This got me the flag.

```
Connected!
hacker@piping~grepping-live-output:~$ /challenge/run | grep "pwn.college"
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge checks for a specific process at the other end of stdout : grep
[INFO] - the challenge will output a reward file if all the tests pass : /challenge/.data.txt

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] If you pass these checks, you will receive the /challenge/.data.txt file.

[TEST] You should have redirected my stdout to another process. Checking...
[TEST] Performing checks on that process!

[INFO] The process' executable is /nix/store/xpq4yhadyhazkcsggmqd7rsgvxb3kjy4-gnugrep-3.11/bin/grep.
[INFO] This might be different than expected because of symbolic links (for example, from /usr/bin/python to /usr/bin/python3 to /usr/bin/python3.8).
[INFO] To pass the checks, the executable must be grep.

[PASS] You have passed the checks on the process on the other end of my stdout!
[PASS] Success! You have satisfied all execution requirements.
pwn.college{cosYIDV4FZRQ4oDM0ziFG0yd07E.dlTM4QDLwQDO0czW}
```

***8.Grepping Errors***

The shell has a >& operator, which redirects a file descriptor to another file descriptor. This means that we can have a two-step process to grep through errors: first, we redirect standard error to standard output (2>& 1) and then pipe the now-combined stderr and stdout as normal (|)! Thus I redirected standard error ```/challenge/run``` to standard output and then the pipe function helped me to normalise the stderr and stdout.

```
Connected!
hacker@piping~grepping-errors:~$ /challenge/run 2>& 1 | grep "pwn.college"
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge checks for a specific process at the other end of stderr : grep
[INFO] - the challenge will output a reward file if all the tests pass : /challenge/.data.txt

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] If you pass these checks, you will receive the /challenge/.data.txt file.

[TEST] You should have redirected my stderr to another process. Checking...
[TEST] Performing checks on that process!

[INFO] The process' executable is /nix/store/xpq4yhadyhazkcsggmqd7rsgvxb3kjy4-gnugrep-3.11/bin/grep.
[INFO] This might be different than expected because of symbolic links (for example, from /usr/bin/python to /usr/bin/python3 to /usr/bin/python3.8).
[INFO] To pass the checks, the executable must be grep.

[PASS] You have passed the checks on the process on the other end of my stderr!
[PASS] Success! You have satisfied all execution requirements.
pwn.college{EcyBq-3Cz1s1X8cBgka0-U9LSQY.dVDM5QDLwQDO0czW}
```

***9.Duplicating Piped Data with Tee***

The tee command duplicates data flowing through your pipes to any number of files provided on the command line. In this challenge, we had to pipe the /challenge/pwn which contains a secret code to /challenge/college. After piping the data, the data file is read through cat to find the secret code. On implementing  the code, we get the flag.

```
Connected!
hacker@piping~duplicating-piped-data-with-tee:~$ /challenge/pwn | tee data.txt | /challenge/college
Processing...
The input to 'college' does not contain the correct secret code! This code
should be provided by the 'pwn' command. HINT: use 'tee' to intercept the
output of 'pwn' and figure out what the code needs to be.
hacker@piping~duplicating-piped-data-with-tee:~$ cat data.txt
Usage: /challenge/pwn --secret [SECRET_ARG]
SECRET_ARG should be "MAo6g5t6"
hacker@piping~duplicating-piped-data-with-tee:~$ /challenge/pwn --MAo6g5t6
Processing...
You must pipe the output of /challenge/pwn into /challenge/college (or 'tee'
for debugging).
hacker@piping~duplicating-piped-data-with-tee:~$ /challenge/ pwn -- secret MAo6g5t6 | /challenge/college
ssh-entrypoint: /challenge/: Is a directory
/challenge/secret needs to the on the receiving end of the output of
'/challenge/pwn' (or 'tee' for debugging).
hacker@piping~duplicating-piped-data-with-tee:~$ tee --secret MAo6g5t6 | /challenge/college
/bin/tee: unrecognized option '--secret'
Try '/bin/tee --help' for more information.
/challenge/secret needs to the on the receiving end of the output of
'/challenge/pwn' (or 'tee' for debugging).
hacker@piping~duplicating-piped-data-with-tee:~$ /challenge/pwn --secret MAo6g5t6 | /challenge/college
Processing...
Correct! Passing secret value to /challenge/college...
Great job! Here is your flag:
pwn.college{MAo6g5t6xH5LSIUZefy21JighmW.dFjM5QDLwQDO0czW}
```

***10.Writing to Multiple Programs***

We had to run the /challenge/hack command, and duplicate its output as input to both the /challenge/the and the /challenge/planet commands. I redirected stdout to stdin of multiple programs using >() function. Further I used ```tee`` command to redirect the stdout to >(/challenge/the) and redirect the other copy as stdin to /challenge/planet.

```
Connected!
hacker@piping~writing-to-multiple-programs:~$ /challenge/hack | tee >(/challenge/the) | /challenge/planet
Congratulations, you have duplicated data into the input of two programs! Here
is your flag:
pwn.college{4S_is6LoWPpGcK8D2RcWEia-46K.dBDO0UDLwQDO0czW}
```

***11.Split-piping stderr and stdout***

In this challenge we have to redirect stderr to one program and stdout to another. Thus First, I redirected stdout from /challenge/hack to the pipe, then to /challenge/planet. Used the same approach for stderr, but only redirect errors using 2>. Thus I got my flag.

```
Connected!
hacker@piping~split-piping-stderr-and-stdout:~$ /challenge/hack > >(/challenge/planet) 2> >(/challenge/the)
Congratulations, you have learned a redirection technique that even experts
struggle with! Here is your flag:
pwn.college{YKASMILVxWL8gbEipiI7FLiESt1.dFDNwYDLwQDO0czW}
```
