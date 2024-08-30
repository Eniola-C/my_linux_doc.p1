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

## Filter

- **Grep**: Used to find texts from any text inputs

```shell
┌──(eniola㉿Eniola)-[~/Templates]
└─$ grep -i fire /home/eniola/Templates/starter1/testinggrep
firewall
firewWALL enabled
FIREWALL
```

Here I created a file in the starter1 directory called testinggrep and added different words in the file.I tried to use grep to search for a specific text. The -i is used to ignore case sensitivity.

**Grep** can also be used to search for text in the directory consisting of different files incase one is not sure of the location of the text in the files.

```shell

┌──(eniola㉿Eniola)-[~/Templates/starter1]
└─$ grep -i firewall *
test2grep:firewall enabled
testinggrep:firewall
testinggrep:FIREWALL
```

The -i is used to ignore case sensitivity
The wildcard \* is used to select all
The -v can be used in an opposite way

```shell

┌──(eniola㉿Eniola)-[~/Templates/starter1]
└─$ grep -iv firewall *
testinggrep:DNS
testinggrep:WIFI
testinggrep:WIFI 3.0
testinggrep:Penetration testing
testinggrep:Soc Analyst
testinggrep:DevSecOps
testinggrep:SWOT
testinggrep:Development
testinggrep:Frontend Development
testinggrep:Backend Development
```

**SED** is a stream editor for text processing. It is used for multiple files.

**Basic Commands**

- Substitute a word for another in the file

```shell

┌──(eniola㉿Eniola)-[~/Templates/starter1]
└─$ cat testinggrep
firewall
fireWALL enabled
DNS
WIFI
WIFI 3.0
Penetration testing
Soc Analyst
DevSecOps
SWOT
Development
Frontend Development
Backend Development
FIREWALL
┌──(eniola㉿Eniola)-[~/Templates/starter1]
└─$ sed -i 's/DNS/TCP/' testinggrep
┌──(eniola㉿Eniola)-[~/Templates/starter1]
└─$ cat testinggrep
firewall
fireWALL enabled
TCP
WIFI
WIFI 3.0
Penetration testing
Soc Analyst
DevSecOps
SWOT
Development
Frontend Development
Backend Development
FIREWALL
```

I substituted DNS for TCP in the above.

- Delete Line

```shell

──(eniola㉿Eniola)-[~/Templates/starter1]
└─$ sed '/Development/d' testinggrep
firewall
fireWALL enabled
TCP
WIFI
WIFI 3.0
Penetration testing
Soc Analyst
DevSecOps
SWOT
FIREWALL

```

The command deleted the line containing `Development`. Use `d` to delete.

Print Lines Containing a Word

```shell

┌──(eniola㉿Eniola)-[~/Templates/starter1]
└─$ sed -n '/fire/p' testinggrep
firewall
firewall
fireWALL enabled
fireWALL enabled
```

This is used to print lines containing fire in the file testinggrep. Use `p` to print.

**AWK** is used for pattern scanning and processing

**Basic Commands:**

- Print

```shell
┌──(eniola㉿Eniola)-[~/Templates/starter1]
└─$ awk '{print $1}' testinggrep
firewall
firewall
fireWALL
fireWALL
TCP
WIFI
WIFI
Penetration
Soc
DevSecOps
SWOT
Development
Frontend
Backend
FIREWALL
┌──(eniola㉿Eniola)-[~/Templates/starter1]
└─$ awk '{print $2}' testinggrep
is

enabled
enabled


3.0
testing
Analyst



Development
Development


```

In the above, i printed the first line and second line of my file. It is vertically not horizontally. The empty lines are for those with just one word so there is nothing to print out.

- NR: Current record number

```shell

──(eniola㉿Eniola)-[~/Templates/starter1]
└─$ awk 'NR==1 {print}' testinggrep
Always enable your firewall
┌──(eniola㉿Eniola)-[~/Templates/starter1]
└─$ awk 'NR==4 {print}' testinggrep
fireWALL enabled
```

It printed any row indicated

- NF: Number of fields in the current record

```shell

TCP
WIFI
WIFI 3.0
Penetration testing
Soc Analyst
DevSecOps
SWOT
Development
Frontend Development
Backend Development
FIREWALL
┌──(eniola㉿Eniola)-[~/Templates/starter1]
└─$ awk 'NR>1 {print}' testinggrep
firewall
fireWALL enabled
fireWALL enabled
TCP
WIFI
WIFI 3.0
Penetration testing
Soc Analyst
DevSecOps
SWOT
Development
Frontend Development
Backend Development
FIREWALL
┌──(eniola㉿Eniola)-[~/Templates/starter1]
└─$ awk 'NR==1 {print}' testinggrep
Always enable your firewall
```

The first and second commands print records with more than whatever number indicated while the last is just equating to a specific row. One thing to notice when using the greater than sign is that it started from the second row of any number you indicated.

Check out for more commands as well.

**Cut** removes parts of lines from a file or input.

- To Extract Characters

```shell

┌──(eniola㉿Eniola)-[~/Templates/starter1]
└─$ cut -c 1-5 testinggrep
Alway
firew
fireW
fireW
TCP
WIFI
WIFI
Penet
Soc A
DevSe
SWOT
Devel
Front
Backe
FIREW
```

I extracted 5 characters from the file as seen above.

- Extract Field(s)

```shell
┌──(eniola㉿Eniola)-[~/Templates/starter1]
└─$ cut -d, -f1  testinggrep
Always
firewall
fireWALL
fireWALL
TCP
WIFI
WIFI
Penetration
Soc Analyst
DevSecOps
SWOT
Development
Frontend
Backend
FIREWALL
```

You can try that with your passwd file or just create a file and include either a comma or colon. -d: is a delimiter, you can use either comma or colon after d. Just make sure you use the one that marches your file content while f represent the field you want to cut.

**FIND** searches for files and directories based on various criteria.

`Common Criteria`

- name: Search by file name

```shell

┌──(eniola㉿Eniola)-[~]
└─$ find Templates -name test*
Templates/starter1/testinggrep
Templates/starter1/testinggrepn
Templates/starter1/test2grep
┌──(eniola㉿Eniola)-[~]
└─$ find . -name test*
./Templates/starter1/testinggrep
./Templates/starter1/testinggrepn
./Templates/starter1/test2grep
```

If you have an idea of where the file can be just use the directory name after find and then -name and the name of the file. The \* is a wildcard used to indicate that it should give an output of all the files with that word. It is used when you can not fully remember the file name. The second line of code is almost the same apart from the fact that i made you of a dot which signify the current directory. Use this when you can not even remember where the file is located.

- size: Search by file size

```shell

┌──(eniola㉿Eniola)-[~]
└─$ find Documents -type f -size -1G
Documents/myfirstfile
```

The directory to search from is Document and `-type f` means consider files(not directories) f stands for file. `-size -1G` means only consider files lesser than 1 Gigabyte. You can as well use + which means the opposite.

**LOCATE** quickly searches for files and directories based on their names. It uses pre-built database to achieve a faster result than `FIND`

```shell

┌──(eniola㉿Eniola)-[~]
└─$ locate Templates -i "testing"
/home/eniola/Templates/starter1/testinggrep
/home/eniola/Templates/starter1/testinggrepn

```

`-i` is to ignore case-sensitivity

```shell

┌──(eniola㉿Eniola)-[~]
└─$ locate Templates -r "test"
/home/eniola/Templates/starter1/test2grep
/home/eniola/Templates/starter1/testinggrep
/home/eniola/Templates/starter1/testinggrepn
┌──(eniola㉿Eniola)-[~]
└─$ locate Templates -r "test*"
/home/eniola/Templates
/home/eniola/Templates/myfirstfile
/home/eniola/Templates/starter1
/home/eniola/Templates/starter1/test2grep
/home/eniola/Templates/starter1/testinggrep
/home/eniola/Templates/starter1/testinggrepn
```

`-r`: Search using regular expressions.

## Conclusion:\t

There are still LESS, MORE, HEAD, Tail, /dev/null, piping, Archiiving and lots more to document. In other to reduce the length, i decided to stop here and continue in another repo.
