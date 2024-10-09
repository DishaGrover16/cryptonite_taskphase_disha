**DIGESTING DOCUMENTATION**

***1.Learning from Documentation***

We have to use the ```/challenge/challenge``` command with the ```--giveflag``` argument to get the flag
```
Connected!
hacker@man~learning-from-documentation:~$ /challenge/challenge --giveflag
Correct argument! Here is your flag:
pwn.college{k9FBHS2sPF8Kd0Q8A9DusD4_P_X.dRjM5QDLwQDO0czW}
```

***2.Learning Complex Usage***

With the ```--printfile``` arugment we can print arbitrary files to the terminal.The argument to the --printfile argument is the path of the flag to read. Thus using this I got the flag. 

```
Connected!
hacker@man~learning-complex-usage:~$ /challenge/challenge --printfile /flag
Correct argument! Here is the /flag file:
pwn.college{EB8mD29kwDJ7psG23WVDbEr7GyL.dVjM5QDLwQDO0czW}
```

***3.Reading Manuals***

As we know that man command will display (if available) the manual of the command you pass as an argument, thus I implemented ```man challenge``` command to print the manual of challenge. On reading that I found the way to flag.

```
Connected!
hacker@man~reading-manuals:~$ man challenge

CHALLENGE(1)                                      Challenge Commands                                     CHALLENGE(1)

NAME
       /challenge/challenge - print the flag!

SYNOPSIS
       challenge OPTION

DESCRIPTION
       Output the flag when called with the right arguments.

       --fortune
              read a fortune

       --version
              output version information and exit

       --ldlvhe NUM
              print the flag if NUM is 064

AUTHOR
       Written by Zardus.

REPORTING BUGS
       The repository for this dojo: <https://github.com/pwncollege/linux-luminarium/>

SEE ALSO
       man(1) bash-builtins(7)

pwn.college                                            May 2024                                          CHALLENGE(1)
hacker@man~reading-manuals:~$ /challenge/challenge --ldlvhe 064
Correct usage! Your flag: pwn.college{A0H6ldlFvWXhegkyqLH4MKQJdSO.dRTM4QDLwQDO0czW}
```

***4.Searching Manuals***

First I opened the challenge manual and using ```/flag``` I started the search. I used n to skip down to the next result and this way found an argument ```--rqt``` which gave me the flag.

```
Connected!
hacker@man~searching-manuals:~$ man challenge
hacker@man~searching-manuals:~$ /challenge/challenge --rqt
Initializing...
Correct usage! Your flag: pwn.college{k5yZIeuCb7f9D9H50UCOHhTn5i3.dVTM4QDLwQDO0czW}
```

***5.Searching for Manuals***

To search for the right man page, I used the command ```man man``` . On reading the manual, -k flag argument is discovered which could contain the required term. Further, to print the flag we find ```kpbukywdnx``` in the manual. At the end on using ```man kpbukywdnx``` we get the required argument to print the flag.

```
Connected!
hacker@man~searching-for-manuals:~$ man man
MAN(1)                                                  Manual pager utils                                                 MAN(1)

NAME
       man - an interface to the system reference manuals

SYNOPSIS
       man [man options] [[section] page ...] ...
       man -k [apropos options] regexp ...
       man -K [man options] [section] term ...
       man -f [whatis options] page ...
       man -l [man options] file ...
       man -w|-W [man options] page ...

DESCRIPTION
       man is the system's manual pager.  Each page argument given to man is normally the name of a program, utility or function.
       The manual page associated with each of these arguments is then found and displayed.  A section, if provided, will  direct
       man  to look only in that section of the manual.  The default action is to search in all of the available sections follow‐
       ing a pre-defined order (see DEFAULTS), and to show only the first page found, even if page exists in several sections.

       The table below shows the section numbers of the manual followed by the types of pages they contain.

       1   Executable programs or shell commands
       2   System calls (functions provided by the kernel)
       3   Library calls (functions within program libraries)
       4   Special files (usually found in /dev)
       5   File formats and conventions, e.g. /etc/passwd
       6   Games
       7   Miscellaneous (including macro packages and conventions), e.g. man(7), groff(7)
       8   System administration commands (usually only for root)
       9   Kernel routines [Non standard]

       A manual page consists of several sections.

       Conventional section names include NAME, SYNOPSIS, CONFIGURATION, DESCRIPTION, OPTIONS, EXIT STATUS, RETURN VALUE, ERRORS,
       ENVIRONMENT, FILES, VERSIONS, CONFORMING TO, NOTES, BUGS, EXAMPLE, AUTHORS, and SEE ALSO.

hacker@man~searching-for-manuals:~$ man -k flag
dpkg-buildflags (1)  - returns build flags to use during package build
Dpkg::BuildFlags (3perl) - query build flags
fegetexceptflag (3)  - floating-point rounding and exception handling
fesetexceptflag (3)  - floating-point rounding and exception handling
i386 (8)             - change reported architecture in new program environment and/or set personality flags
ioctl_iflags (2)     - ioctl() operations for inode flags
kpbukywdnx (1)       - print the flag!
linux32 (1)          - change reported architecture in new program environment and/or set personality flags
linux64 (1)          - change reported architecture in new program environment and/or set personality flags
pcap-config (1)      - write libpcap compiler and linker flags to standard output
security_compute_av_flags (3) - query the SELinux policy database in the kernel
security_compute_av_flags_raw (3) - query the SELinux policy database in the kernel
set_matchpathcon_flags (3) - set flags controlling the operation of matchpathcon or matchpathcon_index and configure the behaviour...
set_matchpathcon_invalidcon (3) - set flags controlling the operation of matchpathcon or matchpathcon_index and configure the beha...
set_matchpathcon_printf (3) - set flags controlling the operation of matchpathcon or matchpathcon_index and configure the behaviou...
setarch (1)          - change reported architecture in new program environment and/or set personality flags
setarch (8)          - change reported architecture in new program environment and/or set personality flags
x86_64 (8)           - change reported architecture in new program environment and/or set personality flags
hacker@man~searching-for-manuals:~$ man kpbukywdnx

CHALLENGE(1)                                            Challenge Commands                                           CHALLENGE(1)

NAME
       /challenge/challenge - print the flag!

SYNOPSIS
       challenge OPTION

DESCRIPTION
       Output the flag when called with the right arguments.

       --fortune
              read a fortune

       --version
              output version information and exit

       --kpbuky NUM
              print the flag if NUM is 081

AUTHOR
       Written by Zardus.

REPORTING BUGS
       The repository for this dojo: <https://github.com/pwncollege/linux-luminarium/>

SEE ALSO
       man(1) bash-builtins(7)

pwn.college                                                  May 2024                                                CHALLENGE(1)
hacker@man~searching-for-manuals:~$ /challenge/challenge --kpbuky 081
Correct usage! Your flag: pwn.college{kp0bukX8ZEyUNwdn11BxkMmaLZL.dZTM4QDLwQDO0czW}
```
