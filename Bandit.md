https://overthewire.org/wargames/bandit/  

---

## Solutions 

### Level 0 --> Level 1

- check your openSSH and openSSL versions: `ssh -V`
- enable the ssh daemon at boot time: `sudo systemctl enable sshd`  
- Connect to the server as bandit0: `ssh bandit0@bandit.labs.overthewire.org -p 2220`
- enter the first pwd => bandit0
- check the contents of the current directory: `ls`
- display the contents of the readme file: `cat readme`

=> password for the next level = ZjLjTmM6FvvyRnrb2rfNWOZOTa6ip5If

### Level 1 --> Level 2

- exit the current ssh session: `exit`
- log into bandit1: `ssh bandit1@bandit.labs.overthewire.org -p 2220`
- enter the pwd you've just found (ctrl+shift+c then ctrl+shift+v)
- check the presence of the file called - with `ls`
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
- check the contents of the current directory: `ls`
- display the contents of inhere, including hidden files: `ls -a inhere/`
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
- 


---
EOF
