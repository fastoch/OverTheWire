https://overthewire.org/wargames/bandit/  

---

## Solutions 

### Level 0 

- check your openSSH and openSSL versions: `ssh -V`
- enable the ssh daemon at boot time: `sudo systemctl enable sshd`  
- Connect to the server: `ssh bandit0@bandit.labs.overthewire.org -p 2220`
- enter the first pwd = bandit0

### Level 0 --> Level 1

- check the contents of the current directory: `ls`
- display the contents of the readme file: `cat readme`

pwd for the nxt level = ZjLjTmM6FvvyRnrb2rfNWOZOTa6ip5If

### Level 1 --> Level 2

- exit the current ssh session: `exit`
- log into bandit1: `ssh bandit1@bandit.labs.overthewire.org -p 2220`
- enter the pwd you've just found (ctrl+shift+c then ctrl+shift+v)
- check the presence of the file called - with `ls`
- since you cannot display the contents of this file with `cat -`, you need to use `cat ./-`
- the previous cmd means "display the contentes of the file located in the current folder that is called - 

>[!tip]
>On a Linux system, a dot means "current folder" and two dots means "parent folder"

pwd for the nxt level = 263JGJPfgU6LtdEvgfWU1XP5yac29mFx

### Level 2 --> Level 3

- exit the current ssh session: `exit`
- log into bandit1: `ssh bandit2@bandit.labs.overthewire.org -p 2220`
- enter the pwd you've just found
- 


---
EOF
