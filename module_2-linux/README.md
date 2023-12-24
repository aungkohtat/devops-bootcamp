### This project is for the [DevOps Bootcamp](https://www.techworld-with-nana.com/devops-bootcamp) for "Operating Systems & Linux Basics" Module ###
<br />

**Commands used in the videos:**

<details>
<summary>Video: Basic Linux Commands (CLI - Part 2)</summary>
<br />

General Operations:
- `clear` = Clears the terminal

Directory Operatings:
- `pwd` = Show current directory. Example Output: `/home/nana`
- `ls` = List folders and files. Example Output: `Desktop  Downloads  Pictures  Documents`
- `cd [dirname]` = Change directory to [dir]
- `mkdir [dirname]` = Make directory [dirname]
- `cd ..` = Go up a directory

File Operations:
- `touch [filename]` = Create [filename]
- `rm [filename]` = Delete [filename]
- `rm -r [dirname]` = Delete a non-empty directory and all the files in it
- `rm -d [dirname]` or `rmdir [dirname]` = Delete an empty directory

Navigating in the File System:
- `cd usr/local/bin` = Navigate multiple dirs (relative path - relative to current dir). Move to bin directory
- `cd ../..` = Move up 2 hierarchies, so go to 'usr' directory
- `cd /usr` = Alternative to go to 'usr' directly (absolute path)
- `cd [absolute path]` = Move to any location by providing the full path
- `cd /home/nana` = Go to my home directory (absolute path)
- `cd ~` = Shortcut alternative to go to home directory
- `ls /etc/network` = List folders and files of 'network' directory

More File and Directory Operations
- `mv [filename] [new_filename]` = Rename the file to a new file name
- `cp -r [dirname] [new_dirname]` = Copy dirname to new_dirname recursively meaning including the files
- `cp [filename] [new_filename]` = Copy filename to new_filename

Some more useful commands
- `ls -R [dirname]` = Show dirs and files but also sub dirs and files
- `history` = Gives a list of all past commands typed in the current terminal session
- `history 20` = Show list of last 20 commands
- `CTRL + r` = Search history
- `CTRL + c` = Stop current command
- `CTRL + SHIFT + v` = Paste copied text into terminal
- `ls -a` = See hidden files too
- `cat [filename]` = Display the file content
- `cat .bash_history` = Example 1: Display the file content
- `cat Documents/java-app/Readme.md` = Example 2: Display the file content
 
Display OS Information
- `uname -a` = Show system and kernel
- `cat /etc/os-release` =  Show OS information
- `lscpu` = Display hardware information, e.g. how many CPU you have etc.
- `lsmem` = Display memory information

Execute commands as superuser
- `sudo [some command]` = Allows regular users to run programs with the security privileges of the superuser or root
- `su - admin` = Switch from nana user to admin
</details>

******

<details>
<summary>Video: Package Manager - Installing Software on Linux</summary>
<br />

APT Package Manager:
- `sudo apt search [package_name]` = Search for a given package
- `sudo apt install [package_name]` = Install a given package
- `sudo apt install [package_name] [package_name2]` = Install multiple packages with one command
- `sudo apt remove [package_name]` = Remove installed package
- `sudo apt update` = Updates the package index. Pulls the latest change sfrom the APT repositories

APT-GET Package Manager:
- `sudo apt-get install [package_name]` = Install package with apt-get package manager

SNAP Package Manager:
- `sudo snap install [package_name]` = Install a given package


</details>

******

<details>
<summary>Video: Working with Vim Editor</summary>
<br />

Install Vim, if it's not available:
- `sudo apt install vim` = Search for a given package

There are 2 Modes:
- Command Mode: default mode, everything is interpreted as a command
- Insert Mode: Allows to enter text

Vim Commands:
- `vim [filename]` = Open file with Vim
- `Press i key` = Switch to Insert Mode
- `Press esc key` = Switch to Command Mode
- `Type :wq` = Write File to disk and quit Vim
- `Type :q!` = Quit Vim without saving the changes
- `Type dd` = Delete entire line
- `Type d10` = Delete next 10 lines
- `Type u` = Undo
- `Type A` = Jump to end of line and switch to insert mode
- `Type 0` = Jump to start of the line
- `Type $` = Jump to end of the line
- `Type 12G` = Go to line 12
- `Type 16G` = Go to line 16
- `Type /pattern` = Search for pattern, e.g. `/nginx`
    - `Type n` = Jump to next match
    - `Type N` = Search in opposite direction
- `Type :%s/old/new` = Replace 'old' with 'new' throughout the file

</details>

******


<details>
<summary>Video: Linux Accounts & Groups (Users & Permissions Part 1)</summary>
 <br />

**Locations of Access Control Files:**
- /etc/passwd
- /etc/shadow
- /etc/group
<!-- -->
- `sudo adduser [username]` = Create a new user
- `sudo passwd [username]` = Change password of a user
- `su - [username]` = Login as username ('su' = short for substitute or switch user)
- `su -` = Login as root
<!-- -->
- `sudo groupadd [groupname]` = Create new group (System assigns next available GID)
- `sudo adduser [username]` = Switch to Insert Mode

**Note 2 different User/Group commands:**<br />
`adduser`, `addgroup`, `deluser`,  `delgroup` = interactive, more user friendly commands<br />
`useradd`, `groupadd`,  `userdel`,  `groupdel` = low-level utilities, more infos need provided by yourself

- `sudo usermod [OPTIONS] [username]` = Modify a user account
- `sudo usermod -g devops tom` = Assign 'devops' as the primary group for 'tom' user
- `sudo delgroup tom` = Removes group 'tom'
- `groups` = Display groups the current logged in user belongs to
- `groups [username]` = Display groups of the given username
- `sudo useradd -G devops nicole` = Create 'nicole' user and add nicole to 'devops' group (-G = secondary group, not primary)
- `sudo gpasswd -d nicole devops` = Removes user 'nicole' from group 'devops'

</details>

******

<details>
<summary>Video: File Ownership & Permissions (Users & Permissions Part 2)</summary>
 <br />

- `ls -l` = Print files in a long listing format, you can see ownership and permissions of the file

**Ownership:**
- `sudo chown [username]:[groupname] [filename]` = Change ownership
- `sudo chown tom:admin test.txt` = Change ownership of 'test.txt' file to 'tom' and group 'admin'
- `sudo chown admin test.txt` = Change ownership of 'test.txt' 'admin' user
- `sudo chgrp devops test.txt` = Make 'devops' group owner of test.txt file

**Possible File Permissions (Symbolic):**
- r = Read
- w = Write
- x = Execute
- '-' = No permission

**Change File Permissions for different owners**

File Permissions can be changed for:
- u = Owner
- g = Group
- o = Other (all other users)

Minus (-) removes the permission
- `sudo chmod -x api` = Takes 'execute' permission away for 'api' folder from all owners
- `sudo chmod g-w config.yaml` = Takes 'write' permission away for 'config.yaml' file from the group 

Plus (+) adds permission
- `sudo chmod g+x config.yaml` = Add 'execute' permission for 'config.yaml' file to the group 
- `sudo chmod u+x script.sh` = Add 'execute' permission for 'script.sh' file to the user 
- `sudo chmod o+x script.sh` = Add 'execute' permission for 'script.sh' file to other 

Change multiple permissions for an owner
- `sudo chmod g=rwx config.yaml` = Assign 'read write execute' permissions to the group
- `sudo chmod g=r-- config.yaml` = Assign only 'read' permission to the group

Changing permissions with numeric values

_Set permissions for all owners with 3 digits, 1 digit for each owner_ [Absolute vs Symbolic Mode](https://docs.oracle.com/cd/E19455-01/805-7229/6j6q8svd8/)

- 0 = No permission
- 1 = Execute
- 2 = Write
- 3 = Execute + Write
- 4 = Read
- 5 = Read + Execute
- 6 = Read + Write
- 7 = Read + Write + Execute
<!-- -->
- `sudo chmod 777 script.sh` = rwx (Read, Write and Execute) permission for everyone for file 'script.sh'
- `sudo chmod 740 script.sh` = Give user all permissions (7), give group only read permission (4), give other no permission (0)


</details>

******