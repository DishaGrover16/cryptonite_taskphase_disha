**Chaining Commands**

***1.Chaining with semicolons***

; separates commands in a similar way to how Enter separates lines. Thus when you hit Enter, your shell executes your typed command and, after that command terminates, give you the prompt to input another command.
Thus I executed the command ```/challenge/pwn; /challenge/college``` this is a chained command. This gave me the flag.

```
Connected!
hacker@chaining~chaining-with-semicolons:~$ /challenge/pwn; /challenge/college
Yes! You chained /challenge/pwn and /challenge/college! Here is your flag:
pwn.college{Mop8FqbAMY4M11UpRlXxF2VsGNK.dVTN4QDLwQDO0czW}
```

***2.Your First Shell Script***

```
Connected!
hacker@chaining~your-first-shell-script:~$ echo "/challenge/pwn;/challenge/college">x.sh
hacker@chaining~your-first-shell-script:~$ bash x.sh
Great job, you've written your first shell script! Here is the flag:
pwn.college{o3otx6zs3lqK9aFo1Jp9QG3MZlE.dFzN4QDLwQDO0czW}
```
