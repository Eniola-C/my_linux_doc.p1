# Linux Commands

## Brief Introduction to Linux

**Linux** is an open source software with a source code that anyone can inspect, modify, and enhance.

## Important Directories

- **Home Directories** : /root, /home/username
- **User Executable** : /bin, /usr/bin, usr/local/bin
- **System Executable** : /sbin, /usr/sbin, /usr/local/sbin
- **Other Mount Points** : /media, /mnt
- **Configuration** : /etc
- **Temporary Files** : /tmp
- **Kernels and Bootloader** : /boot
- **Server Data** : /var, /srv
- **System Information** : /proc, /sys
- **Shared Libraries** : /lib, /usr/lib, /usr/local/lib

**Note** : / - Its the root directory while /root - is the root users home directory.

## Basic Navigation

- **cd** : Used to change directory

```shell

   ┌──(eniola㉿Eniola)-[~]
└─$ ls
Burp-Suite-Pro  Desktop  Documents  Downloads  Music  Pictures  Public  Templates  Videos  dead.letter  healthy-diets.vercel.app  trail.sh  trial  update.sh
┌──(eniola㉿Eniola)-[~]
└─$ cd Desktop

```

- **pwd** : Print Working Directory. Can be used to check an absolute path of the directory you are.

```shell

┌──(eniola㉿Eniola)-[~/Desktop]
└─$ pwd
/home/eniola/Desktop

```

- **ls** : List files and directories

```shell

┌──(eniola㉿Eniola)-[~]
└─$ ls
Burp-Suite-Pro  Desktop  Documents  Downloads  Music  Pictures  Public  Templates  Videos  dead.letter  healthy-diets.vercel.app  trail.sh  trial  update.sh

```

## File Management

### Types of Files

```shell


| _File Type_ | _Symbol_ | _Meaning_                                                  |
| ----------- | -------- | ---------------------------------------------------------- |
| _Regular_   | -        | Normal files such as text, data or executable files        |
| ----------- | ----     | ---------------------------------------------------------- |
| _Directory_ | d        | Files that are lists of other files                        |
| ----------- | ----     | ---------------------------------------------------------- |
| _Link_      | l        | A shortcut that points to the location of the actual file. |
| ----------- | ----     | ---------------------------------------------------------- |
| _Special_   | c        | Mechanism used for input and output such as files in /dev  |
| ----------- | ----     | ---------------------------------------------------------- |
| _Socket_    | s        | A special file that provides inter-process networking      |
| ----------- | ----     | ---------------------------------------------------------- |
| _Pipe_      | p        | Allows Processes to communicate with each other            |
| ----------- | ----     | ---------------------------------------------------------- |

```

### Creation of Files

- **mkdir** : Create a new directory

```shell

 ┌──(eniola㉿Eniola)-[~/Desktop]
└─$ mkdir starter
┌──(eniola㉿Eniola)-[~/Desktop]
└─$ ls
starter

```

- **rmdir** : Remove an empty directory

```shell

┌──(eniola㉿Eniola)-[~/Desktop]
└─$ rmdir starter
┌──(eniola㉿Eniola)-[~/Desktop]
└─$ ls

```

- **touch** : Create a new empty file

```shell

┌──(eniola㉿Eniola)-[~/Desktop]
└─$ touch myfirstfile
┌──(eniola㉿Eniola)-[~/Desktop]
└─$ ls
myfirstfile

```

- **cp** : Copy files and directories

```shell

┌──(eniola㉿Eniola)-[~/Desktop]
└─$ cp /home/eniola/Desktop/myfirstfile /home/eniola/Templates
┌──(eniola㉿Eniola)-[~/Desktop]
└─$ cd ..
┌──(eniola㉿Eniola)-[~]
└─$ cd Templates
┌──(eniola㉿Eniola)-[~/Templates]
└─$ ls
myfirstfile

```

- **mv** : Move or rename files and directories

```shell

┌──(eniola㉿Eniola)-[~/Desktop]
└─$ mkdir starter1
┌──(eniola㉿Eniola)-[~/Desktop]
└─$ ls
myfirstfile  starter1
┌──(eniola㉿Eniola)-[~/Desktop]
└─$ mv /home/eniola/Desktop/starter1 /home/eniola/Templates
┌──(eniola㉿Eniola)-[~/Desktop]
└─$ ls
myfirstfile
┌──(eniola㉿Eniola)-[~/Desktop]
└─$ cd ..
┌──(eniola㉿Eniola)-[~]
└─$ cd Templates
┌──(eniola㉿Eniola)-[~/Templates]
└─$ ls
myfirstfile  starter1

```

- **rm** : Remove files and directories
- **rm -rf** : Forcefully remove files
