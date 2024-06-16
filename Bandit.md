https://overthewire.org/wargames/bandit/  

---

# Solutions 

## Level 0 --> Level 1

- check your openSSH and openSSL versions: `ssh -V`
- enable the ssh daemon at boot time: `sudo systemctl enable sshd`  
- Connect to the server as bandit0: `ssh bandit0@bandit.labs.overthewire.org -p 2220`
- enter the first pwd => bandit0
- check the contents of the current directory: `ls -al` (-a to include hidden files, -l for long list format)
- display the contents of the readme file: `cat readme`

=> password for the next level = ZjLjTmM6FvvyRnrb2rfNWOZOTa6ip5If

## Level 1 --> Level 2

- exit the current ssh session: `exit`
- log into bandit1: `ssh bandit1@bandit.labs.overthewire.org -p 2220`
- enter the pwd you've just found (ctrl+shift+c then ctrl+shift+v)
- check the presence of the file called - with `ls -al`
- since you cannot display the contents of this file with `cat -`, you need to use `cat ./-`
- the previous cmd means "display the contents of the - file that is located in the current folder

>[!tip]
>On a Linux system, a dot `.` means "current folder" and two dots `..` means "parent folder"

=> passwd for the nxt level = 263JGJPfgU6LtdEvgfWU1XP5yac29mFx

## Level 2 --> Level 3

- exit the current ssh session: `exit`
- log into bandit2: `ssh bandit2@bandit.labs.overthewire.org -p 2220`
- enter the pwd you've just found
- this one is very easy since you just have to use autocompletion
- type ` cat s` then press the Tab key to autocomplete
- this will complete the command as follows: `cat spaces\ in\ this\ filename`

>[!important]
>the `\` character is used to escape special characters

=> pwd for the nxt lvl = MNk8KNH3Usiio41PRUEoDFPqfxLPlSmx

### Level 3 --> Level 4

- exit the current ssh session: `exit`
- log into bandit3: `ssh bandit3@bandit.labs.overthewire.org -p 2220`
- enter the pwd you've just found
- check the contents of the current directory: `ls -al`
- display the contents of inhere, including hidden files: `ls -al inhere/`
- display the contents of the hidden file located in the inhere folder: `cat inhere/...Hiding-From-You`
- for the previous command, you can use autocompletion

=> pwd for the next level = 2WmrDFRmJIq3IPxneAaMGhap0pFhF3NJ

## Level 4 --> Level 5

- exit the current ssh session: `exit`
- log into bandit4: `ssh bandit4@bandit.labs.overthewire.org -p 2220`
- enter the pwd you've just found
- display the types of all files contained in the inhere folder: `file inhere/*`
- only one file will be human-readable, the one which type is ASCII text. Its name is -file07
- display the pwd: `cat inhere/-file07` (use autocompletion)

=> pwd for the next level = 4oQYVPkxZOOEOO5pTW81FB8j8lxXGUQw

## Level 5 --> Level 6

- exit the current ssh session: `exit`
- log into bandit5: `ssh bandit5@bandit.labs.overthewire.org -p 2220`
- enter the pwd you've just found
- find files under the inhere folder that are 1033 bytes in size: `find inhere/* -size 1033c` 
- https://linuxconfig.org/how-to-use-find-command-to-search-for-files-based-on-file-size
- the previous cmd will return `inhere/maybehere07/.file2`
- we can check this file's size and if it's executable or not with: `ls -al inhere/maybehere07 | grep '\.file2'`
- the previous cmd confirms the file size is 1033 bytes and it's not executable (the `\` is for escaping the `.` (dot) character)
- last thing to check is if the file is human-readable: `file inhere/maybehere07/.file2`
- it is human-readable, so we can now display the pwd: `cat inhere/maybehere07/.file2`

=> pwd for the next level = HWasnPhtq9AVKe0dmk45nxy20cvUa6EG

## Level 6 --> Level 7

- exit the current ssh session: `exit`
- log into bandit5: `ssh bandit6@bandit.labs.overthewire.org -p 2220`
- enter the pwd you've just found
- find a file owned by user bandit7 and by group bandit6: `find / -group bandit6 -user bandit7 -ls 2>/dev/null`

We search the whole file system, hence the `/` (slash) at the beginning of our cmd.

We pass the `-ls` option to the `find` to list the results in ls command format.  
https://www.cyberciti.biz/faq/how-do-i-find-all-the-files-owned-by-a-particular-user-or-group/  

`2>/dev/null` is to redirect standard error to /dev/null.  
All data written on the /dev/null special file is discarded by the system.  
https://www.cyberciti.biz/faq/bash-find-exclude-all-permission-denied-messages/  

- now we can display the password: `cat /var/lib/dpkg/info/bandit7.password`

=> pwd for the next level = morbNTDkSW6jIlUc0ymOdMaLnOlFVAaj

## Level 7 --> Level 8

- exit the current ssh session: `exit`
- log into bandit5: `ssh bandit7@bandit.labs.overthewire.org -p 2220`
- enter the pwd you've just found
- find the file: `find -name data.txt`
- find the password: `cat data.txt | grep millionth`

=> pwd for the next level = dfwvzFQi4mU0wfNbFOe9RoWskMLg7eEc

## Level 8 --> Level 9

- exit the current ssh session: `exit`
- log into bandit5: `ssh bandit8@bandit.labs.overthewire.org -p 2220`
- enter the pwd you've just found
- find the only line of txt that occurs only once: `sort data.txt | uniq -u`

`uniq` filters out the **adjacent** matching lines from the input file (that is required as an argument).  
We need to use the `sort` cmd because repeated lines are not necessarily adjacent in our case.  
The -u option will only output lines that are unique in the input.  
https://www.geeksforgeeks.org/uniq-command-in-linux-with-examples/  

=> pwd for the next level = 4CKMh1JI91bUIZZPXDqGanal4xvAg0JM

## Level 9 --> Level 10

- exit the current ssh session: `exit`
- log into bandit5: `ssh bandit9@bandit.labs.overthewire.org -p 2220`
- enter the pwd you've just found
- check the file format of data.txt: `file data.txt` => data.txt is a binary file (data)

Binary files (such as program files) may contain strings of human-readable text. But how do we get to see them?  
If we use `cat` or `less`, we are likely to end up with a hung terminal window.  

https://www.howtogeek.com/427805/how-to-use-the-strings-command-on-linux/  

The `strings` command extracts strings of printable characters from files so that other commands can use the strings   
without having to contend with non-printable characters. 

- To find the human-readable strings preceded by several '=' characters: `strings data.txt | grep ==`

=> pwd for the next level = FGUW5ilLVJrxX9kMYMmlN4MgbpfMiqey

## Level 10 --> Level 11

- exit the current ssh session: `exit`
- log into bandit5: `ssh bandit10@bandit.labs.overthewire.org -p 2220`
- enter the pwd you've just found
- to decode the base64 encoded data: `cat data.txt | base64 -d`

=> pwd for the next level = dtR173fZKb0RRsDFSGsg2RWnpNVj3qRr

## Level 11 --> Level 12

- exit the current ssh session: `exit`
- log into bandit5: `ssh bandit11@bandit.labs.overthewire.org -p 2220`
- enter the pwd you've just found
- translate upper and lower case letters by 13 positions: `tr 'n-zabcdefghijklm:N-ZABCDEFGHIJKLM' 'a-z:A-Z' < data.txt`

https://www.baeldung.com/linux/tr-command  

=> pwd for the next level = 7x16WNeHIi5YkIhWsfFIqoognUTyj9Q4

## Level 12 --> Level 13

- exit the current ssh session: `exit`
- log into bandit5: `ssh bandit12@bandit.labs.overthewire.org -p 2220`
- enter the pwd you've just found

---

### Some theory

**Hexdumps** can be used to figure out the type of a file. Each **file type** has a **magic number/file signature**.  
This is **very important** because sometimes files might not have the correct or any file ending to identify their type.  

**Compression** is a method of encoding that aims to reduce the original size of a file without losing (much) information.  

**gzip** is a command to compress or decompress (-d) files. A ‘gzip’ file generally ends with **.gz**.  
**bzip2** is another command which allows for compressing and decompressing (-d) files. A ‘bzip2’ file generally ends with **.bz2**.

An **Archive** File is a file that contains one or multiple files and their metadata. This can allow easier **portability**.  

**tar** is a command that creates **archive** files (-cf). It also allows **extracting** these files again (-xf).  
A tar archive generally ends with **.tar**.

---

There will be 3 tasks:
- Setting up a temporary directory
- Reverting the hexdump
- Decompressing

### Create a directory, copy the file, rename it

- once logged in, check home directory content: `ls`
- navigate to the tmp folder: `cd /tmp`
- create a temporary folder: `mktemp -d`
- navigate to this folder, in my case: `cd tmp.r0JOTbLpJ2`
- copy the data file from the home dir to the temp dir: `cp ~/data.txt .`
- check the copy with `ls`
- rename the file: `mv data.txt hexdump_data`
- check the renaming with `ls`

### Revert the hexdump and decompress the file

- look at the first lines of the file to check if it is hexdump data: `cat hexdump_data | head` 
- to operate on the actual data, we first need to revert the hexdump: `xxd -r hexdump_data compressed_data`
- run `ls` to see that we now have 2 files: the hexdump and the actual data in a compressed format

We now need to decompress the data.  
To figure out what decompression we need to use, look at the first bytes in the hexdump to find the file signature.  

src = https://www.garykessler.net/library/file_sigs.html  
For **gzip** files the header is 1F 8B 08  
For **bzip2** files the header is 42 5A 68

- to show the first bytes of the hexdump: `cat hexdump_data | head` => 1f 8b 08
- now we know this is a gzip file, we can add the correct file ending and decompress the file
- `mv compressed_data compressed_data.gz`
- `gzip -d compressed_data.gz`
- However, the data is still not fully decompressed, so we look at the first bytes again
- `xxd compressed_data | head` => 42 5A 68
- we can rename the file with the appropriate file ending (.bz2) and decompress it
- `mv compressed_data compressed_data.bz2`
- `bzip2 -d compressed_data.bz2`
- And the file is still compressed. `xxd compressed_data | head` shows that it is gzip.
- We repeat the previous steps
- `mv compressed_data compressed_data.gz`
- `gzip -d compressed_data.gz`
- now if we run `file compressed_data`, it returns `POSIX tar archive (GNU)`
- rename the file: `mv compressed_data compressed_data.tar`
- show the contents of the archive: `tar -tf compressed_data.tar` => only contains one file named data5.bin
- `tar -xf compressed_data.tar` to extract the file and `ls` to check
- `file data5.bin` reveals that it's another archive file
- rename the file: `mv data5.bin data5.tar`
- check the archive contents: `tar -tf data5.tar` => contains one file named data6.bin
- extract the archive: `tar -xf data5.tar` and `ls` to check
- `file data6.bin` shows that it's bzip2 compressed data
- `mv data6.bin data6.bz2`
- `bzip2 -d data6.bz2`
- `file data6.bin` => tar archive
- `mv data6.bin data6.tar`
- `tar -tf data6.tar` => 1 file named data8.bin
- `tar -xf data6.tar`
- `file data8.bin` => gzip file
- `mv data8.bin data8.gz`
- `gzip -d data8.gz` => data8
- `cat data8`

=> pwd for the next level = FO5dwFsc0cbaIiH0h8J2eUks2vdTDwAn

## Level 13 --> Level 14

- exit the current ssh session: `exit`
- log into bandit5: `ssh bandit13@bandit.labs.overthewire.org -p 2220`
- enter the pwd you've just found
- 

---
EOF
