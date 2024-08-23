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

- **ls** : List files and directories. ls can be attached to other parameters like -l, -la, -lt,etc.

```shell

┌──(eniola㉿Eniola)-[~]
└─$ ls
Burp-Suite-Pro  Desktop  Documents  Downloads  Music  Pictures  Public  Templates  Videos  dead.letter  healthy-diets.vercel.app  trail.sh  trial  update.sh

```

## File Management

### Types of Files

```shell


|  File_Type  |  Symbol  |                     Meaning                                |
| ----------- | -------- | ---------------------------------------------------------- |
| Regular     |    -     | Normal files such as text, data or executable files        |
| ----------- | -------- | ---------------------------------------------------------- |
| Directory   |    d     | Files that are lists of other files                        |
| ----------- | -------- | ---------------------------------------------------------- |
| Link        |    l     | A shortcut that points to the location of the actual file. |
| ----------- | -------- | ---------------------------------------------------------- |
| Special     |    c     | Mechanism used for input and output such as files in /dev  |
| ----------- | -------- | ---------------------------------------------------------- |
| Socket      |    s     | A special file that provides inter-process networking      |
| ----------- | -------- | ---------------------------------------------------------- |
| Pipe        |    p     | Allows Processes to communicate with each other            |
| ----------- | -------- | ---------------------------------------------------------- |

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

### File Permission

#### Symbolic Method

1. _r_ : permission to read a file or list a directory's contents
2. _w_ : permission to write to a file or create and remove files from a directory
3. _x_ : permission to execute a program or change into a directory and do a long listing of the directory
4. _-_ : no permission

```shell

┌──(eniola㉿Eniola)-[~/Templates]
└─$ ls -la
total 12
drwxr-xr-x  3 eniola eniola 4096 Aug 23 12:39 .
drwx------ 21 eniola eniola 4096 Aug 23 12:12 ..
-rw-r--r--  1 eniola eniola    0 Aug 23 12:13 myfirstfile
drwxr-xr-x  2 eniola eniola 4096 Aug 23 12:38 starter1

```

Using -la will gave a long listing. Made it easy to identify the type of files and the files permissions.
Also exposed the hidden files which were directories in this case.

myfirstfile is a file because it started with _-_ while the starter1 is a directory because it starts with _d_.
The permissions are divided into three,

| users | Groups | Others |
| ----- | ------ | ------ |
| rwx   | rwx    | rwx    |

For myfirstfile, we have

| users | Groups | Others |
| ----- | ------ | ------ |
| rw-   | r--    | r--    |

user: Can read and write

group and other : Can only read

For stater1, we have

| users | Groups | Others |
| ----- | ------ | ------ |
| rwx   | r-x    | r-x    |

users: Can read, write and execute

groups and others: Can read and execute

File permissions can be changed by using **chmod**. It is used to add or remove permission.

Use **+** to add and **-** to remove. I only did the addition here but still the same process.

To add permission for the user only

```shell

┌──(eniola㉿Eniola)-[~/Templates]
└─$ chmod +x myfirstfile
┌──(eniola㉿Eniola)-[~/Templates]
└─$ ls -la
total 12
drwxr-xr-x  3 eniola eniola 4096 Aug 23 12:39 .
drwx------ 21 eniola eniola 4096 Aug 23 12:12 ..
-rwxr-xr-x  1 eniola eniola    0 Aug 23 12:13 myfirstfile
drwxr-xr-x  2 eniola eniola 4096 Aug 23 12:38 starter1

```

To add permission for the group only

```shell
┌──(eniola㉿Eniola)-[~/Templates]
└─$ chmod g+w myfirstfile
┌──(eniola㉿Eniola)-[~/Templates]
└─$ ls -la
total 12
drwxr-xr-x  3 eniola eniola 4096 Aug 23 12:39 .
drwx------ 21 eniola eniola 4096 Aug 23 12:12 ..
-rwxrwxr-x  1 eniola eniola    0 Aug 23 12:13 myfirstfile
drwxr-xr-x  2 eniola eniola 4096 Aug 23 12:38 starter1

```

To add permission for others

```shell

┌──(eniola㉿Eniola)-[~/Templates]
└─$ chmod o+w myfirstfile
┌──(eniola㉿Eniola)-[~/Templates]
└─$ ls -la
total 12
drwxr-xr-x  3 eniola eniola 4096 Aug 23 12:39 .
drwx------ 21 eniola eniola 4096 Aug 23 12:12 ..
-rwxrwxrwx  1 eniola eniola    0 Aug 23 12:13 myfirstfile
drwxr-xr-x  2 eniola eniola 4096 Aug 23 12:38 starter1

```

#### Numeric Method

Uses a three digit mode number

- First digit specifies owner's permissions
- Second digit specifies group permissions
- Third digit specifies others' permissions

How To Calculate Permissions

- 4 : read
- 2 : write
- 1 : execute

| users | Groups | Others |
| ----- | ------ | ------ |
| 4+2+1 | 4+2+1  | 4+2+1  |
| ----- | ------ | ------ |
| 7     | 7      | 7      |

This denote that the user, group and others have full permission.

Change the permission of myfirstfile, the user should have read and write permissions only, group should have read only while others should have no permission at all.

All to do is to add up the numbers. 4 is for read, 2 is for write and 1 is for execute for each of them, This should give 640 if calculated well.

```shell

┌──(eniola㉿Eniola)-[~/Templates]
└─$ ls -la
total 12
drwxr-xr-x  3 eniola eniola 4096 Aug 23 12:39 .
drwx------ 21 eniola eniola 4096 Aug 23 12:12 ..
-rwxrwxrwx  1 eniola eniola    0 Aug 23 12:13 myfirstfile
drwxr-xr-x  2 eniola eniola 4096 Aug 23 12:38 starter1
┌──(eniola㉿Eniola)-[~/Templates]
└─$ chmod 640 myfirstfile
┌──(eniola㉿Eniola)-[~/Templates]
└─$ ls -la
total 12
drwxr-xr-x  3 eniola eniola 4096 Aug 23 12:39 .
drwx------ 21 eniola eniola 4096 Aug 23 12:12 ..
-rw-r-----  1 eniola eniola    0 Aug 23 12:13 myfirstfile
drwxr-xr-x  2 eniola eniola 4096 Aug 23 12:38 starter1

```
