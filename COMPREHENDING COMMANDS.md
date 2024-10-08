** COMPREHENDING COMMANDS**

***1.cat:not the pet, but the command!***

Cat command is most often used to read files. We only had to read the flag file stored in home directory with cat in order to get the flag. Therefore, ```cat flag``` is used.

```
Connected!
hacker@commands~cat-not-the-pet-but-the-command:~$ cat flag
pwn.college{IsCzBJsPa4sg3j2PJjZGYtv5Ofb.dFzN1QDLwQDO0czW}
```

***2.catting absolute paths***

flag file had to be read using its absolute path and thus /flag is used with cat in order to get the flag.

```
Connected!
hacker@commands~catting-absolute-paths:~$ cat /flag
pwn.college{oClpvrhQdr8e2d02GYrBVbXesQ6.dlTM5QDLwQDO0czW}
```

***3.more catting practice***

Cding into the directory was not allowed and it was given that flag is in this location ```/lib/R/site-library/flag```. As I was aware of the fact that cat command is used to read files and I know the location of the file, the cat command could read the file without cding into the directory. 

```
Connected!
You cannot use the 'cd' command in this level, and must retrieve the flag by
absolute path. Plus, I hid the flag in a different directory! You can find it
in the file /lib/R/site-library/flag. Go cat it out **without** cding into that
directory!
hacker@commands~more-catting-practice:~$ cat /lib/R/site-library/flag
pwn.college{kZEEKo7lQlksx9JBZTRfZqbstrf.dBjM5QDLwQDO0czW}
```

***4.grepping for a needle in a haystack***

grep command is usually used to search the file for lines of text containing SEARCH_STRING and print them to the console. Since I had the search string ```pwn.college``` and the location ```/challenge/data.txt```, I used the grep command to print the flag.

```
Connected!
hacker@commands~grepping-for-a-needle-in-a-haystack:~$ grep pwn.college /challenge/data.txt
pwn.college{EjgRM7CdMMUPMC2wLNhau8srG_G.ddTM4QDLwQDO0czW}
```

***5.listing files***

ls will list files in all the directories provided to it as arguments, and in the current directory if no arguments are provided. Thus I first listed all the files in /challenge and then found the flag.
```
Connected!
hacker@commands~listing-files:~$ ls /challenge
30374-renamed-run-13534  DESCRIPTION.md
hacker@commands~listing-files:~$ /challenge/30374-renamed-run-13534
Yahaha, you found me! Here is your flag:
pwn.college{4-4oviqoBcg8Aijlsu1Rbi0fsMp.dhjM4QDLwQDO0czW}
```

***6.touching files***

/tmp/pwn and /tmp/college are to be created so I changed my directory to /tmp and used to touch command to create pwn and college files.
```
Connected!
hacker@commands~touching-files:~$ cd /tmp
hacker@commands~touching-files:/tmp$ touch pwn
hacker@commands~touching-files:/tmp$ touch college
hacker@commands~touching-files:/tmp$ /challenge/run
Success! Here is your flag:
pwn.college{QRZrcpz8cQACtvFkFX9-o67-NF4.dBzM4QDLwQDO0czW}
```

***7.removing files***

