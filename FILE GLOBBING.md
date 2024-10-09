**FILE GLOBBING**

***1.Matching with****

The * matches any part of the filename except for / or a leading . character. As we know that when the system encounters any * character in any argument, tries to replace it with any file or directory that matches the pattern. Thus I implemented ```cd /ch*``` it took me to the challenge directory and there I executed ```/challenge/run``` to get the flag.

```
Connected!
This challenge resets your working directory to /home/hacker unless you change
directory properly...
hacker@globbing~matching-with-:~$ cd /ch*
hacker@globbing~matching-with-:/challenge$ /challenge/run
You ran me with the working directory of /challenge! Here is your flag:
pwn.college{ohZQBT7mMp8qWB3UNyqQjTS8PoA.dFjM4QDLwQDO0czW}
```

***2.Matching with ?***

As we studied that when the shell encounters a ? character in any argument, the shell will treat it as single-character wildcard. This works like *, but only matches one character. Thus for changing directories I executed ```cd /?ha??enge``` and ran the ```/challenge/run``` command from the directory to get the flag.

```
Connected!
This challenge resets your working directory to /home/hacker unless you change
directory properly...
hacker@globbing~matching-with-:~$ cd /?ha??enge
hacker@globbing~matching-with-:/challenge$ /challenge/run
You ran me with the working directory of /challenge! Here is your flag:
pwn.college{E1rexuiWkzXcs4UgDcMQwdZEQC0.dJjM4QDLwQDO0czW}
```

***3.Matching with []***

[] is a wildcard for some subset of potential characters, specified within the brackets. Thus after cding into /challenge/files, I ran the command /challenge/run file_[bash] to glob into file_b, file_a, file_s, and file_h.

```
Connected!
hacker@globbing~matching-with-:~$ cd  /challenge/files
hacker@globbing~matching-with-:/challenge/files$ /challenge/run file_[bash]
You got it! Here is your flag!
pwn.college{AWLQpdt2PNuvloyHG2Zzbzhdebe.dNjM4QDLwQDO0czW}
```

***4.Matching paths with []***

Starting from your home directory, run /challenge/run with a single argument that bracket-globs into the absolute paths to the file_b, file_a, file_s, and file_h files. Thus ```/challenge/run /challenge/files/file_[bash]``` is the absolute path to get the flag.

```
Connected!
hacker@globbing~matching-paths-with-:~$ /challenge/run /challenge/files/file_[bash]
You got it! Here is your flag!
pwn.college{o1TIU36B6JKMl2OGtQdt3cyyA_C.dRjM4QDLwQDO0czW}
```

***5.Mixing Globs***

In this challenge, we have to use the globbing methods to find three files-"challenging", "educational", and "pwning" in the directory. Thus we use cep to search for the first letters of these files in order to look for the files.

```Connected!
hacker@globbing~mixing-globs:~$ cd /challenge/files
hacker@globbing~mixing-globs:/challenge/files$ /challenge/run [cep]*
You got it! Here is your flag!
pwn.college{MrtOs8DPCHWLhUXfx4Vg_ATT-Wy.dVjM4QDLwQDO0czW}
```

***6.Exclusionary Globbing***


If the first character in the brackets is a ! or (in newer versions of bash) a ^, the glob inverts, and that bracket instance matches characters that aren't listed. Thus for this challenge, after cding into the directory, we execute ```/challenge/run [!pwn]*``` command in order to list all other files except these.

```
Connected!
hacker@globbing~exclusionary-globbing:~$ cd /challenge/files
hacker@globbing~exclusionary-globbing:/challenge/files$ /challenge/run [!pwn]*
You got it! Here is your flag!
pwn.college{guWBjNdcvsBkPNj4j9yshwI__ig.dZjM4QDLwQDO0czW}
```
