https://overthewire.org/wargames/bandit/  

---

## Solutions 

### Level 0 --> Level 1

- check your openSSH and openSSL versions: `ssh -V`
- enable the ssh daemon at boot time: `sudo systemctl enable sshd`  
- Connect to the server as bandit0: `ssh bandit0@bandit.labs.overthewire.org -p 2220`
- enter the first pwd => bandit0
- check the contents of the current directory: `ls -al` (-a to include hidden files, -l for long list format)
- display the contents of the readme file: `cat readme`

=> password for the next level = ZjLjTmM6FvvyRnrb2rfNWOZOTa6ip5If

### Level 1 --> Level 2

- exit the current ssh session: `exit`
- log into bandit1: `ssh bandit1@bandit.labs.overthewire.org -p 2220`
- enter the pwd you've just found (ctrl+shift+c then ctrl+shift+v)
- check the presence of the file called - with `ls -al`
- since you cannot display the contents of this file with `cat -`, you need to use `cat ./-`
- the previous cmd means "display the contents of the - file that is located in the current folder

>[!tip]
>On a Linux system, a dot `.` means "current folder" and two dots `..` means "parent folder"

=> passwd for the nxt level = 263JGJPfgU6LtdEvgfWU1XP5yac29mFx

### Level 2 --> Level 3

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

### Level 4 --> Level 5

- exit the current ssh session: `exit`
- log into bandit4: `ssh bandit4@bandit.labs.overthewire.org -p 2220`
- enter the pwd you've just found
- display the types of all files contained in the inhere folder: `file inhere/*`
- only one file will be human-readable, the one which type is ASCII text. Its name is -file07
- display the pwd: `cat inhere/-file07` (use autocompletion)

=> pwd for the next level = 4oQYVPkxZOOEOO5pTW81FB8j8lxXGUQw

### Level 5 --> Level 6

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

### Level 6 --> Level 7

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

### Level 7 --> Level 8

- exit the current ssh session: `exit`
- log into bandit5: `ssh bandit7@bandit.labs.overthewire.org -p 2220`
- enter the pwd you've just found
- find the file: `find -name data.txt`
- find the password: `cat data.txt | grep millionth`

=> pwd for the next level = dfwvzFQi4mU0wfNbFOe9RoWskMLg7eEc

### Level 8 --> Level 9

- exit the current ssh session: `exit`
- log into bandit5: `ssh bandit8@bandit.labs.overthewire.org -p 2220`
- enter the pwd you've just found
- find the only line of txt that occurs only once: `sort data.txt | uniq -u`

`uniq` filters out the **adjacent** matching lines from the input file (that is required as an argument).  
We need to use the `sort` cmd because repeated lines are not necessarily adjacent in our case.  
The -u option will only output lines that are unique in the input.  
https://www.geeksforgeeks.org/uniq-command-in-linux-with-examples/  

=> pwd for the next level = 4CKMh1JI91bUIZZPXDqGanal4xvAg0JM

### Level 9 --> Level 10

- exit the current ssh session: `exit`
- log into bandit5: `ssh bandit9@bandit.labs.overthewire.org -p 2220`
- enter the pwd you've just found
- 


---
EOF
