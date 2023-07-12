**Log files**
Most daemons (services) log to a file, usually stored in /var/log
View logs:
- Text editor
- journalctl -u < service name >
- systemctl status < service name >

**Root (UID 0)**
Highest level of priviledge, able to read and write anything on the system
- Security risk if used day to day
	- use a standard account day to day and only escalate when nessacary
	- never start services as root, allows hackers to have unlimited permissions

**Escalate priviledges**
Run a command with sudo < command > to gain elevated priviledges
- user priviledges defined in /etc/sudoers

Windows
- User
- Admin
- System
Linux
- User
- Root (admin)

**Users**
Each user has a home directory in /home/user
User creds stored in two files
- /etc/passwd - everyone can read
- /etc/shadow - only root should be able to read, contains encrypted passwords

Commands
- whoami - show username
- who - who is logged in
- w - show the above and what they are doing
- id - show user id, group id, and your groups (useful for CTF checking available groups)
- su < user > - switch to another user
- su - < user > - switch and use their shell environment
- su - escalate to admin

**User Manipulation**
- useradd < user name> -m : add user (-m add home directory)
- userdel -r -f < user name > : delete a user ( -f force, -r remove home directory and mail spool))
- usermod - modifiy user and perms etc
- passwd : reset your password
	- passwd < username > : reset a user's password (need priv)

**Groups**
Apply policies to multiple users at once
	This info is stored in /etc/groups
ex: sudo: x : 24 : devconnected,bob 
name   pass id    users in group

Commands
- groupadd < group name >: add a new group
- groupmod
- groupdel
- usermod -a -G < group > < user> - add user to group

**ownership and prmissions**
Owndership - everything owned by a user and group
permissions - everything has r/w/x permissions

Perms
-RWX RWX RWX 
user  group  other

-: normal file
r : directory contents can be listed
w : contents of a directory can be modified
x - directory can be entered (cd)
Moving or deleting afile is an operation on the directory
	- the directory is just a file itself, we may be able to move and delte things we don't own

commands
- ls -lh : check ownership and permissions 
- chown < user> < file > : change owner (-R is recursive)

**Permission Manipulation**
Two methods available, octal or symbolic
- chmod 640 test.txt
- chmod u=rw, g=r, o= test.txt
- chmod u+r test.txt
- chmod u+r o-r test.txt

Change so that only the file/directory owner can remove the file (+ root)
- chmod +t test
- chmod 1755 test

**SetUID and SetGID bits**
if set, the program executes as the owner/group
- allows admins to give granular priviledges
- can sometimes be used for priviledge escalation
- Little 's' has execute (rwx) priviledges vs big 'S' (rw-)

Commands
- chmod u+s test
- chmod g+s test

**Access control lists (ACLs)**
Most file systems support ACLs, and they provide an additional, flexible permission mechanism for file systems
- Enabled in /etc/fstab
- Allows for mutlple permission within a file


