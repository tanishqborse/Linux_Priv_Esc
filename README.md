# Linux Privilege Escalation

Welcome to the **Linux Privilege Escalation Repository**! This repository is a collection of resources, guides, and cheatsheets to help you understand and practice Linux privilege escalation techniques.

## 📂 Repository Contents
- **Guides & Tutorials**: Step-by-step instructions for privilege escalation techniques.
- **Cheatsheets**: Quick reference lists for common privilege escalation methods.
- **Scripts & Automation**: Tools to help identify and exploit privilege escalation vulnerabilities.
- **Real-World Scenarios**: Practical examples of privilege escalation from CTFs and penetration testing.

## 🔗 Recommended Resources

Here are some must-read resources on Linux Privilege Escalation:

1. **TCM Security - Linux Privilege Escalation Resources**  
   📌 [GitHub Repository](https://github.com/TCM-Course-Resources/Linux-Privilege-Escalation-Resources)

2. **g0tmi1k's Blog - Basic Linux Privilege Escalation**  
   📌 [Read the Blog](https://blog.g0tmi1k.com/2011/08/basic-linux-privilege-escalation/)

3. **PayloadsAllTheThings - Linux Privilege Escalation**  
   📌 [GitHub Repository](https://github.com/swisskyrepo/PayloadsAllTheThings/blob/master/Methodology%20and%20Resources/Linux%20-%20Privilege%20Escalation.md)

4. **HackTricks - Linux Privilege Escalation**  
   📌 [Online Guide](https://book.hacktricks.wiki/en/linux-hardening/privilege-escalation/index.html)

5. **Total OSCP Guide - Linux Privilege Escalation**  
   📌 [GitBook](https://sushant747.gitbooks.io/total-oscp-guide/content/privilege_escalation_-_linux.html)

## 🛠️ Linux Privilege Escalation Techniques

### 🔍 System Enumeration
```cpp
hostname
uname -a 
//tells us the kernel we are running 
//simple google search can tell us if there are available exploits
//look for kernel exploits

cat /proc/version
//kernel version

cat /etc/issue
//distribution

lscpu
//anything about the CPU's
//core,threads to run exploits 

ps aux
//what services are running?
//kind of like task manager

ps aux | grep root
//to check what tasks are being run by the root user
ps aux | grep TCM/user
//to check what tasks am i running right now?
```

### 🔍 User Enumeration
```cpp
whoami
//checks user

id
/*
uid=user id (=1000|)
gid=group id (|)
*/

sudo -l 
//What commands we can run as SUDO?

cat /etc/passwd
//users 
cat /etc/passwd | cut -d : -f 1
//just users nothing else

cat /etc/shadow
//sensitive files

cat /etc/group
//group files

history
//find the commands run before
ls -la
//to check if we have bash_history files available 
cat .bash_history

sudo su -
```

### 🔍 Network Information
```cpp
ifconfig
//print out network info

ip a 
//see ip addresses 

ip route
//if we are sourcing some other ip through our ip using a gateway

arp -a 
ip neigh
//table to show whats reachable,stale etc

netstat -ano
//what ports are open?
//what communications exist?
//traffic flowing? can we intercept? exploit?
```

### 🔍 Password Hunting
```cpp
grep --color=auto -rnw '/' -ie "PASSWORD=" --color=always 2> /dev/null
//look for the word PASSWORD anywhere in the files and spit it out in RED

locate password | more
//find password as a file name

find / -name authorized_keys

find / -name id_rsa 2> /dev/null
```

### 🔍 Automated Tools
- `LinPeas.sh`
- `LinEnum.sh`
- `linux-exploit-suggester`
- `linuxprivchecker.py`

### 🔍 File Permissions
```cpp
ls -la /etc/passwd
//shows the users, groups, id's 

ls -la /etc/shadow
//contains the hash 

gedit passwd
gedit shadow
//store the contents of these files in this file 

unshadow passwd shadow
//it will combine these two files.
```

### 🔍 SSH Key Escalation
```cpp
gedit id_rsa
chmod 600 id_rsa
ssh -i id_rsa root@ip_address
```

## 📜 Disclaimer
This repository is intended for **educational purposes only**. Do not use these techniques on unauthorized systems.

---
**Happy Hacking!** 🚀

