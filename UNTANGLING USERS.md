**Untangling Users**

***1.Becoming root with su***

In this challenge, we learned that because it has the SUID bit set, su runs as root. Running as root, it can start a root shell! Of course, su is discerning: before allowing the user to elevate privileges to root, it checks to make sure that the user knows the root password. So firstly after executing su and entering the given password, in the root, I ran the command ```cat /flag``` in order to read the flag.

```
Connected!
hacker@users~becoming-root-with-su:~$ su
Password:
root@users~becoming-root-with-su:/home/hacker# cat /flag
pwn.college{USkTBKLuFZiE91ixD9S4feHsjFW.dVTN0UDLwQDO0czW}
```

***2.Other users with su***

In this challenge, after switching into zardus user, I executed the ```/challenge/run``` command and got the flag.

```
Connected!
hacker@users~other-users-with-su:~$ su zardus
Password:
zardus@users~other-users-with-su:/home/hacker$ /challenge/run
Congratulations, you have become Zardus! Here is your flag:
pwn.college{guXVn1DEIXsEfq9xFi4prsyeJTq.dZTN0UDLwQDO0czW}
```

***3.Cracking Passwords***

After cding into the challenge directory, executed the command ```john shadow-leak``` and after getting status I executed the command ```john --show shadow-leak``` wherein I got passwords for zardus user and the hacker user. I ran the command ```su zardus``` and then entered the given password following which I invoked ```/challenge/run``` command to get the flag.

```
Connected!
hacker@users~cracking-passwords:~$ cd /challenge
hacker@users~cracking-passwords:/challenge$ john shadow-leak
Loaded 1 password hash (crypt, generic crypt(3) [?/64])
Press 'q' or Ctrl-C to abort, almost any other key for status
0g 0:00:00:03 37% 1/3 0g/s 278.7p/s 278.7c/s 278.7C/s Ozardus99999...zardus
Session aborted
hacker@users~cracking-passwords:/challenge$ john shadow-leak
Loaded 1 password hash (crypt, generic crypt(3) [?/64])
Press 'q' or Ctrl-C to abort, almost any other key for status
0g 0:00:00:04 54% 1/3 0g/s 286.5p/s 286.5c/s 286.5C/s zrdus..zardus9999994
0g 0:00:00:10 99% 1/3 0g/s 283.7p/s 283.7c/s 283.7C/s zardus999991915..999991900
0g 0:00:00:12 0% 2/3 0g/s 282.8p/s 282.8c/s 282.8C/s brenda..keith
0g 0:00:00:14 0% 2/3 0g/s 282.8p/s 282.8c/s 282.8C/s serena..88888888
0g 0:00:00:15 0% 2/3 0g/s 282.4p/s 282.4c/s 282.4C/s deedee..grizzly
0g 0:00:00:16 0% 2/3 0g/s 282.4p/s 282.4c/s 282.4C/s national..rocket1
0g 0:00:00:17 1% 2/3 0g/s 282.4p/s 282.4c/s 282.4C/s 1234qwer..babygirl
0g 0:00:00:18 1% 2/3 0g/s 282.0p/s 282.0c/s 282.0C/s katrina..karla
0g 0:00:00:19 1% 2/3 0g/s 282.3p/s 282.3c/s 282.3C/s ncc1701d..1022
0g 0:00:00:20 1% 2/3 0g/s 282.6p/s 282.6c/s 282.6C/s Johnson..buzz
aardvark         (zardus)
1g 0:00:00:20 100% 2/3 0.04847g/s 282.2p/s 282.2c/s 282.2C/s Johnson..buzz
Use the "--show" option to display all of the cracked passwords reliably
Session completed
hacker@users~cracking-passwords:/challenge$ john --show shadow-leak
hacker:NO PASSWORD:20000:0:99999:7:::
zardus:aardvark:20015:0:99999:7:::

2 password hashes cracked, 0 left
hacker@users~cracking-passwords:/challenge$ su zardus
Password:
zardus@users~cracking-passwords:/challenge$ /challenge/run
Congratulations, you have become Zardus! Here is your flag:
pwn.college{4b8eTFSTLlzo3Ka3N2rgJIflQYR.ddTN0UDLwQDO0czW}
```

***4.Using Sudo***

Sudo defaults to running a command as root. In this challenge, we have to sudo cat /flag to read the /flag file with root access.

```
Connected!
hacker@users~using-sudo:~$ sudo cat /flag
pwn.college{oznRdtE16RmJswNpceSeMBQ2cWk.dhTN0UDLwQDO0czW}
```






