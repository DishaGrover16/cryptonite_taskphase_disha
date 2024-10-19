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
