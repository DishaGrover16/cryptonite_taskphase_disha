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

As we combine more and more commands to achieve complex effects, the length of the combined prompt quickly gets really annoying to deal with. When this happens, you can put these commands in a file, called a shell script, and run them by executing the file. Thus I chained the commands ```/challenge/pwn``` and ```/challenge/college``` and then created a shell script to store these commands. ```bash x.sh``` was used to execute the file in order to get the flag.

```
Connected!
hacker@chaining~your-first-shell-script:~$ echo "/challenge/pwn;/challenge/college">x.sh
hacker@chaining~your-first-shell-script:~$ bash x.sh
Great job, you've written your first shell script! Here is the flag:
pwn.college{o3otx6zs3lqK9aFo1Jp9QG3MZlE.dFzN4QDLwQDO0czW}
```

***3.Redirecting Script Output***

I chained the commands ```/challenge/pwn``` and ```/challenge/college``` and then created a shell script to store these commands. In this challenge, we have to pipe the output of the script into a single invocation of the ```/challenge/solve``` command. Following this, I got the flag.

```
Connected!
hacker@chaining~redirecting-script-output:~$ echo "/challenge/pwn;/challenge/college">x.sh
hacker@chaining~redirecting-script-output:~$ bash x.sh | /challenge/solve
Correct! Here is your flag:
pwn.college{oXMF6xCiTE8HAuaJ8bIwvzfZV7e.dhTM5QDLwQDO0czW}
```

***4.Executable Shell Scripts***

In this challenge, we had to create a script ```x.sh``` and then store the command ```/challenge/solve``` in it. Then I changed to file's permissions to give the user executable rights using the chmod command. Then I ran the file in order to get the flag.

```
Connected!
hacker@chaining~executable-shell-scripts:~$ touch x.sh
hacker@chaining~executable-shell-scripts:~$ echo "/challenge/solve">x.sh
hacker@chaining~executable-shell-scripts:~$ chmod u+x x.sh
hacker@chaining~executable-shell-scripts:~$ ./x.sh
Congratulations on your shell script execution! Your flag:
pwn.college{Awmqgh6kGUj0ufqAaqxFLc0pvsr.dRzNyUDLwQDO0czW}
```
