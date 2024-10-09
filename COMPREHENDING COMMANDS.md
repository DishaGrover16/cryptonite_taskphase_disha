**COMPREHENDING COMMANDS**

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

In Linux, you remove files with the rm command. In this challenge the file delete_me had to be removed, so i first listed all the files and then used ```rm delete_me``` to delete the files and then listed again to check the result. ```/challenge/run``` command gave me the flag..

```
Connected!
hacker@commands~removing-files:~$ ls
COLLEGE  Desktop  college  d  delete_me  f  myflag
hacker@commands~removing-files:~$ rm delete_me
hacker@commands~removing-files:~$ ls
COLLEGE  Desktop  college  d  f  myflag
hacker@commands~removing-files:~$ /challenge/check
Excellent removal. Here is your reward:
pwn.college{M0MaUys0a_fQk1-j5frAlkBfLZC.dZTOwUDLwQDO0czW}
```

***8.hidden files***

ls doesn't list all the files by default. Linux has a convention where files that start with a . don't show up by default in ls and in a few other contexts. To view them with ls, you need to invoke ls with the -a flag. Thus after cding into / directory, I listed using command ```ls``` and ```ls-a``` to see the difference. I found a ```.flag-275631971312451``` file which i read using the cat command in order to get my flag.

```
Connected!
hacker@commands~hidden-files:~$ cd /
hacker@commands~hidden-files:/$ ls
bin        dev   lib    libx32  nix   root  srv  usr
boot       etc   lib32  media   opt   run   sys  var
challenge  home  lib64  mnt     proc  sbin  tmp
hacker@commands~hidden-files:/$ ls -a
.                      challenge  lib64   proc  tmp
..                     dev        libx32  root  usr
.dockerenv             etc        media   run   var
.flag-275631971312451  home       mnt     sbin
bin                    lib        nix     srv
boot                   lib32      opt     sys
hacker@commands~hidden-files:/$ cat .flag-275631971312451
pwn.college{8pdSpr6IwwbQ37AzmGYSUNu3RpP.dBTN4QDLwQDO0czW}
```

***9.An Epic Filesystem Quest***

After entering in the / directory, ls command is implemented to find the clue which is then argument of the cat command. As we cannot cd into the next directory, we use ls to see the contents and then the clue received is used as the location of the file which is catted for the next clue. Similarly after following a series of clues and hints, the flag is grabbed using cat, ls,ls-a,etc. commands.

```
Connected!
cdhacker@commands~an-epic-filesystem-quest:~$ cd /
hacker@commands~an-epic-filesystem-quest:/$ ls
NUGGET  boot       dev  flag  lib    lib64   media  nix  proc  run   srv  tmp  var
bin     challenge  etc  home  lib32  libx32  mnt    opt  root  sbin  sys  usr
hacker@commands~an-epic-filesystem-quest:/$ cat NUGGET
Yahaha, you found me!
The next clue is in: /opt/radare2/libr/arch/p/arm/v35/arch-armv7/.git/refs/tags

Watch out! The next clue is **trapped**. You'll need to read it out without 'cd'ing into the directory; otherwise, the clue will self destruct!
hacker@commands~an-epic-filesystem-quest:/$ ls /opt/radare2/libr/arch/p/arm/v35/arch-armv7/.git/refs/tags
BLUEPRINT-TRAPPED
hacker@commands~an-epic-filesystem-quest:/$ ls /opt/radare2/libr/arch/p/arm/v35/arch-armv7/.git/refs/tags/BLUEPRINT-TRAPPED
/opt/radare2/libr/arch/p/arm/v35/arch-armv7/.git/refs/tags/BLUEPRINT-TRAPPED
hacker@commands~an-epic-filesystem-quest:/$ cat  /opt/radare2/libr/arch/p/arm/v35/arch-armv7/.git/refs/tags/BLUEPRINT-TRAPPED
Congratulations, you found the clue!
The next clue is in: /usr/share/racket/pkgs/scribble-lib/scribble/elsarticle/lang

The next clue is **hidden** --- its filename starts with a '.' character. You'll need to look for it using special options to 'ls'.
hacker@commands~an-epic-filesystem-quest:/$ ls -a /usr/share/racket/pkgs/scribble-lib/scribble/elsarticle/lang
.  ..  .INFO  compiled  reader.rkt
hacker@commands~an-epic-filesystem-quest:/$ cat /usr/share/racket/pkgs/scribble-lib/scribble/elsarticle/lang/.INFO
Great sleuthing!
The next clue is in: /opt/radare2/libr/arch/p/chip8
hacker@commands~an-epic-filesystem-quest:/$ cat opt/radare2/libr/arch/p/chip8
cat: opt/radare2/libr/arch/p/chip8: Is a directory
hacker@commands~an-epic-filesystem-quest:/$ ls opt/radare2/libr/arch/p/chip8
DISPATCH  plugin.c  plugin.d  plugin.o  pseudo.c  pseudo.d  pseudo.o
hacker@commands~an-epic-filesystem-quest:/$ cat opt/radare2/libr/arch/p/chip8/DISPATCH
Yahaha, you found me!
The next clue is in: /usr/share/racket/pkgs/scheme-lib/scheme/private/provider/lang/compiled
hacker@commands~an-epic-filesystem-quest:/$ ls /usr/share/racket/pkgs/scheme-lib/scheme/private/provider/lang/compiled
WHISPER  reader_rkt.dep  reader_rkt.zo
hacker@commands~an-epic-filesystem-quest:/$ cat /usr/share/racket/pkgs/scheme-lib/scheme/private/provider/lang/compiled/WHISPER
Lucky listing!
The next clue is in: /opt/linux/linux-5.4/arch/arm/mach-ebsa110

The next clue is **delayed** --- it will not become readable until you enter the directory with 'cd'.
hacker@commands~an-epic-filesystem-quest:/$ ls /opt/linux/linux-5.4/arch/arm/mach-ebsa110
Makefile  Makefile.boot  POINTER  core.c  core.h  include  io.c  leds.c
hacker@commands~an-epic-filesystem-quest:/$ cd /opt/linux/linux-5.4/arch/arm/mach-ebsa110
hacker@commands~an-epic-filesystem-quest:/opt/linux/linux-5.4/arch/arm/mach-ebsa110$ cat POINTER
Tubular find!
The next clue is in: /usr/local/lib/python3.8/dist-packages/angr/exploration_techniques

The next clue is **hidden** --- its filename starts with a '.' character. You'll need to look for it using special options to 'ls'.
hacker@commands~an-epic-filesystem-quest:/opt/linux/linux-5.4/arch/arm/mach-ebsa110$ ls -a /usr/local/lib/python3.8/dist-packages/angr/exploration_techniques
.            __pycache__    director.py       local_loop_seer.py    oppologist.py  stochastic.py    threading.py  veritesting.py
..           bucketizer.py  driller_core.py   loop_seer.py          slicecutor.py  suggestions.py   timeout.py
.SNIPPET     common.py      explorer.py       manual_mergepoint.py  spiller.py     symbion.py       tracer.py
__init__.py  dfs.py         lengthlimiter.py  memory_watcher.py     spiller_db.py  tech_builder.py  unique.py
hacker@commands~an-epic-filesystem-quest:/opt/linux/linux-5.4/arch/arm/mach-ebsa110$ cat /usr/local/lib/python3.8/dist-packages/angr/exploration_techniques/.SNIPPET
Great sleuthing!
The next clue is in: /opt/capstone/suite/x86/verify

Watch out! The next clue is **trapped**. You'll need to read it out without 'cd'ing into the directory; otherwise, the clue will self destruct!
hacker@commands~an-epic-filesystem-quest:/opt/linux/linux-5.4/arch/arm/mach-ebsa110$ ls /opt/capstone/suite/x86/verify
BRIEF-TRAPPED  README
hacker@commands~an-epic-filesystem-quest:/opt/linux/linux-5.4/arch/arm/mach-ebsa110$ cat /opt/capstone/suite/x86/verify/^C
hacker@commands~an-epic-filesystem-quest:/opt/linux/linux-5.4/arch/arm/mach-ebsa110$ cat /opt/capstone/suite/x86/verify/BRIEF-TRAPPED
Congratulations, you found the clue!
The next clue is in: /usr/share/man/man7

The next clue is **delayed** --- it will not become readable until you enter the directory with 'cd'.
hacker@commands~an-epic-filesystem-quest:/opt/linux/linux-5.4/arch/arm/mach-ebsa110$ cd /usr/share/man/man7
hacker@commands~an-epic-filesystem-quest:/usr/share/man/man7$ ls
DOSSIER                           file-hierarchy.7.gz     iso_8859_14.7.gz             qemu-qmp-ref.7.gz
Ed25519.7ssl.gz                   fsf-funding.7gcc.gz     iso_8859_15.7.gz             random.7.gz
Ed448.7ssl.gz                     ftm.7.gz                iso_8859_16.7.gz             raw.7.gz
PAM.7.gz                          futex.7.gz              iso_8859_2.7.gz              re_format.7.gz
RAND.7ssl.gz                      gfdl.7gcc.gz            iso_8859_3.7.gz              regex.7.gz
RAND_DRBG.7ssl.gz                 gitcli.7.gz             iso_8859_4.7.gz              rtld-audit.7.gz
RSA-PSS.7ssl.gz                   gitcore-tutorial.7.gz   iso_8859_5.7.gz              rtnetlink.7.gz
SM2.7ssl.gz                       gitcredentials.7.gz     iso_8859_6.7.gz              sched.7.gz
X25519.7ssl.gz                    gitcvs-migration.7.gz   iso_8859_7.7.gz              scrypt.7ssl.gz
X448.7ssl.gz                      gitdiffcore.7.gz        iso_8859_8.7.gz              sd-boot.7.gz
address_families.7.gz             giteveryday.7.gz        iso_8859_9.7.gz              sem_overview.7.gz
aio.7.gz                          gitglossary.7.gz        kernel-command-line.7.gz     session-keyring.7.gz
apt-patterns.7.gz                 gitnamespaces.7.gz      keyrings.7.gz                shm_overview.7.gz
armscii-8.7.gz                    gitremote-helpers.7.gz  keyutils.7.gz                sigevent.7.gz
arp.7.gz                          gitrevisions.7.gz       koi8-r.7.gz                  signal-safety.7.gz
ascii.7.gz                        gitsubmodules.7.gz      koi8-u.7.gz                  signal.7.gz
asymmetric-key.7.gz               gittutorial-2.7.gz      latin1.7.gz                  sock_diag.7.gz
attributes.7.gz                   gittutorial.7.gz        latin10.7.gz                 socket.7.gz
bash-builtins.7.gz                gitworkflows.7.gz       latin2.7.gz                  spufs.7.gz
bio.7ssl.gz                       glibc.7.gz              latin3.7.gz                  ssl.7ssl.gz
boot.7.gz                         glob.7.gz               latin4.7.gz                  standards.7.gz
bootparam.7.gz                    gpl.7gcc.gz             latin5.7.gz                  suffixes.7.gz
bootup.7.gz                       hier.7.gz               latin6.7.gz                  svipc.7.gz
bpf-helpers.7.gz                  hostname.7.gz           latin7.7.gz                  symlink.7.gz
builtins.7.gz                     icmp.7.gz               latin8.7.gz                  systemd-boot.7.gz
capabilities.7.gz                 inode.7.gz              latin9.7.gz                  systemd.directives.7.gz
cgroup_namespaces.7.gz            inotify.7.gz            libbsd.7.gz                  systemd.environment-generator.7.gz
cgroups.7.gz                      intro.7.gz              libc.7.gz                    systemd.generator.7.gz
charsets.7.gz                     ip.7.gz                 locale.7.gz                  systemd.index.7.gz
cmake-buildsystem.7.gz            ipc_namespaces.7.gz     mailaddr.7.gz                systemd.journal-fields.7.gz
cmake-commands.7.gz               ipv6.7.gz               man-pages.7.gz               systemd.net-naming-scheme.7.gz
cmake-compile-features.7.gz       iso-8859-1.7.gz         man.7.gz                     systemd.offline-updates.7.gz
cmake-developer.7.gz              iso-8859-10.7.gz        math_error.7.gz              systemd.special.7.gz
cmake-env-variables.7.gz          iso-8859-11.7.gz        mount_namespaces.7.gz        systemd.syntax.7.gz
cmake-file-api.7.gz               iso-8859-13.7.gz        mq_overview.7.gz             systemd.time.7.gz
cmake-generator-expressions.7.gz  iso-8859-14.7.gz        namespaces.7.gz              sysvipc.7.gz
cmake-generators.7.gz             iso-8859-15.7.gz        netdevice.7.gz               tc-hfsc.7.gz
cmake-language.7.gz               iso-8859-16.7.gz        netlink.7.gz                 tcp.7.gz
cmake-modules.7.gz                iso-8859-2.7.gz         network_namespaces.7.gz      term.7.gz
cmake-packages.7.gz               iso-8859-3.7.gz         nptl.7.gz                    termio.7.gz
cmake-policies.7.gz               iso-8859-4.7.gz         numa.7.gz                    thread-keyring.7.gz
cmake-properties.7.gz             iso-8859-5.7.gz         operator.7.gz                time.7.gz
cmake-qt.7.gz                     iso-8859-6.7.gz         ossl_store-file.7ssl.gz      tis-620.7.gz
cmake-server.7.gz                 iso-8859-7.7.gz         ossl_store.7ssl.gz           udp.7.gz
cmake-toolchains.7.gz             iso-8859-8.7.gz         packet.7.gz                  udplite.7.gz
cmake-variables.7.gz              iso-8859-9.7.gz         pam.7.gz                     unicode.7.gz
complex.7.gz                      iso_8859-1.7.gz         pam_env.7.gz                 units.7.gz
cp1251.7.gz                       iso_8859-10.7.gz        pam_selinux.7.gz             unix.7.gz
cp1252.7.gz                       iso_8859-11.7.gz        passphrase-encoding.7ssl.gz  uri.7.gz
cpack-generators.7.gz             iso_8859-13.7.gz        path_resolution.7.gz         url.7.gz
cpuset.7.gz                       iso_8859-14.7.gz        pcap-filter.7.gz             urn.7.gz
credentials.7.gz                  iso_8859-15.7.gz        pcap-linktype.7.gz           user-keyring.7.gz
crypto.7ssl.gz                    iso_8859-16.7.gz        pcap-tstamp.7.gz             user-session-keyring.7.gz
ct.7ssl.gz                        iso_8859-2.7.gz         persistent-keyring.7.gz      user_namespaces.7.gz
daemon.7.gz                       iso_8859-3.7.gz         pid_namespaces.7.gz          utf-8.7.gz
ddp.7.gz                          iso_8859-4.7.gz         pipe.7.gz                    utf8.7.gz
deb-version.7.gz                  iso_8859-5.7.gz         pkeys.7.gz                   uts_namespaces.7.gz
des_modes.7ssl.gz                 iso_8859-6.7.gz         posixoptions.7.gz            vdso.7.gz
editline.7edit.gz                 iso_8859-7.7.gz         precedence.7.gz              vsock.7.gz
environ.7.gz                      iso_8859-8.7.gz         process-keyring.7.gz         x25.7.gz
epoll.7.gz                        iso_8859-9.7.gz         proxy-certificates.7ssl.gz   x509.7ssl.gz
evp.7ssl.gz                       iso_8859_1.7.gz         pthreads.7.gz                xattr.7.gz
fanotify.7.gz                     iso_8859_10.7.gz        pty.7.gz                     xkeyboard-config.7.gz
feature_test_macros.7.gz          iso_8859_11.7.gz        qemu-block-drivers.7.gz
fifo.7.gz                         iso_8859_13.7.gz        qemu-cpu-models.7.gz
hacker@commands~an-epic-filesystem-quest:/usr/share/man/man7$ cat DOSSIER
CONGRATULATIONS! Your perserverence has paid off, and you have found the flag!
It is: pwn.college{0didma2XCfWb6lOMpnMmWfB3Q2V.dljM4QDLwQDO0czW}
```


***10.making directories***

I created a directory using mkdir command and after moving in to that directory, I created a file. On running /challenge/run command, flag came.

```
Connected!
hacker@commands~making-directories:~$ mkdir /tmp/pwn
hacker@commands~making-directories:~$ cd /tmp/pwn
hacker@commands~making-directories:/tmp/pwn$ touch college
hacker@commands~making-directories:/tmp/pwn$ /challenge/run
Success! Here is your flag:
pwn.college{85rdGREEJrwBMkjNfCfgmh2Dfn-.dFzM4QDLwQDO0czW}
```

***11.finding files***

I searched the whole filesystem using the command ```find / -name flag```.On getting some paths to directories and files, used cat command on every path to get the flag finally..

```
Connected!
hacker@commands~finding-files:~$ find / -name flag
find: ‘/root’: Permission denied
find: ‘/proc/1/task/1/fd’: Permission denied
find: ‘/proc/1/task/1/fdinfo’: Permission denied
find: ‘/proc/1/task/1/ns’: Permission denied
find: ‘/proc/1/fd’: Permission denied
find: ‘/proc/1/map_files’: Permission denied
find: ‘/proc/1/fdinfo’: Permission denied
find: ‘/proc/1/ns’: Permission denied
find: ‘/proc/7/task/7/fd’: Permission denied
find: ‘/proc/7/task/7/fdinfo’: Permission denied
find: ‘/proc/7/task/7/ns’: Permission denied
find: ‘/proc/7/fd’: Permission denied
find: ‘/proc/7/map_files’: Permission denied
find: ‘/proc/7/fdinfo’: Permission denied
find: ‘/proc/7/ns’: Permission denied
find: ‘/var/log/private’: Permission denied
find: ‘/var/log/apache2’: Permission denied
find: ‘/var/log/mysql’: Permission denied
find: ‘/var/cache/ldconfig’: Permission denied
find: ‘/var/cache/apt/archives/partial’: Permission denied
find: ‘/var/cache/private’: Permission denied
find: ‘/var/lib/apt/lists/partial’: Permission denied
find: ‘/var/lib/php/sessions’: Permission denied
find: ‘/var/lib/mysql-files’: Permission denied
find: ‘/var/lib/private’: Permission denied
find: ‘/var/lib/mysql-keyring’: Permission denied
find: ‘/var/lib/mysql’: Permission denied
find: ‘/tmp/tmp.XvrUsDZh8M’: Permission denied
find: ‘/run/mysqld’: Permission denied
find: ‘/run/sudo’: Permission denied
find: ‘/etc/ssl/private’: Permission denied
/usr/local/lib/python3.8/dist-packages/pwnlib/flag
/usr/local/share/radare2/5.9.5/flag
/opt/angr-management/_internal/PySide6/Qt/qml/Qt3D/Input/flag
/opt/pwndbg/.venv/lib/python3.8/site-packages/pwnlib/flag
/opt/radare2/libr/flag
/nix/store/pmvk2bk4p550w182rjfm529kfqddnvh3-python3.11-pwntools-4.12.0/lib/python3.11/site-packages/pwnlib/flag
/nix/store/1yagn5s8sf7kcs2hkccgf8d0wxlrv5sz-radare2-5.9.0/share/radare2/5.9.0/flag
hacker@commands~finding-files:~$ cat /usr/local/lib/python3.8/dist-packages/pwnlib/flag
cat: /usr/local/lib/python3.8/dist-packages/pwnlib/flag: Is a directory
hacker@commands~finding-files:~$ cat /usr/local/share/radare2/5.9.5/flag
cat: /usr/local/share/radare2/5.9.5/flag: Is a directory
hacker@commands~finding-files:~$ cat /opt/angr-management/_internal/PySide6/Qt/qml/Qt3D/Input/flag
pwn.college{ciC4jHnQg_2IMEtr4ipAqwcjzHk.dJzM4QDLwQDO0czW}
```

***12.linking files***

```
