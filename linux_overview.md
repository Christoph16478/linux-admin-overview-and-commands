# what is [linux](https://en.wikipedia.org/wiki/Linux)

* founded 1992 by Linux Torvalds based on [minix](https://en.wikipedia.org/wiki/Minix)
* strongly oriented at the [unix-architecture](https://en.wikipedia.org/wiki/Unix_architecture) and is called a [unix-derivat](https://en.wikipedia.org/wiki/Unix)
* linux is a fre rela multi-user os
    * simlutaneously multiple users at the same system
* most components or under the [gnu public license](https://en.wikipedia.org/wiki/GNU_General_Public_License)
* linux is running as a so called [embedded system](https://en.wikipedia.org/wiki/Linux_on_embedded_systems) on routers, firewalls, smartphones, tablets, etc.
* [linux kernel](https://en.wikipedia.org/wiki/Linux_kernel) is written in [c programming language](https://en.wikipedia.org/wiki/the_C_Programming_Language)

# open source licensing

* gnu gpl allows to change, execute, change, distribute and study the software
* changes, development and further development must be licensed again under gnu
* gpl does not forbid commercial usage
* there are fre community editions and commercial enterprise editions
* there are a lot of optional componentes, with different license
    * e.g. driver for graphic cards
* [bsd licenses](https://en.wikipedia.org/wiki/BSD_licenses) are 'permissive' open source licenses
    * Derivations and extensions may be placed under more restrictive licenses
    * product developed on the BSD license may also be [closed source](https://en.wikipedia.org/wiki/Proprietary_software)

# [linux distributions - overview](https://en.wikipedia.org/wiki/List_of_Linux_distributions)

* distribution consists of linux kernel and collection of other software
* distributions can be administrated by communities, foundations of companies
* many distributions are not compatible with each other
    * file system hierarchy standard
        * provides standards for binary interfaces and program libraries
    * [linux standard base](https://en.wikipedia.org/wiki/Linux_Standard_Base)
* successor of [red hat](https://en.wikipedia.org/wiki/Red_Hat) is [fedora](https://en.wikipedia.org/wiki/Fedora), fedora is a community version
* commercial product is [red hat enterprise](https://en.wikipedia.org/wiki/Red_Hat_enterprise_Linux)
* centos is a fre RHeLL binary-compatible distribution
* [suse](https://en.wikipedia.org/wiki/SUSe) stands for software and system development, was called suse linux enterprise server, short: [sles](https://en.wikipedia.org/wiki/SUSe_Linux_enterprise#SUSe_Linux_enterprise_Server) and [opensuse](https://en.wikipedia.org/wiki/OpenSUSe) divided form debian gnu/linux developed [knoppix](https://en.wikipedia.org/wiki/Knoppix)
* [ubuntu]() is very popular debian derivative, offered as desktop and server edition
* [kali linux]() is a linux version based on debian and optimized fir security

# hyperlinks

* [https://w.kernel.org/](https://w.kernel.org/)

# lab with virtualbox

* virtualization software with [virtualbox](https://de.wikipedia.org/wiki/VirtualBox), [vmware](https://de.wikipedia.org/wiki/VMware), [workstation](https://de.wikipedia.org/wiki/workstation), [hyper-v](https://de.wikipedia.org/wiki/Hyper-V) and [xen](https://de.wikipedia.org/wiki/Xen)
* offers flexibility and independency of os on personal computer/workstation
* advantages: quickly set back to original state and no influence on working computer

# install ubuntu and [guest extension](https://en.wikipedia.org/wiki/VirtualBox#Guests)

* developed by [canonical](https://de.wikipedia.org/wiki/Canonical)
* differentiated in server and desktop
* [lts (long term support)](https://en.wikipedia.org/wiki/Long-term_support) is sometimes older but updates on regular bases
* memory is dynamically allocated, it is as macuh memory used as neded by the virtual harddisk
* network settings meansm that the virtual machine communicates directly via the physical interface of the host, therefor the vm looks like normal host in network
* for installation, installation dvd is inserted in form of an iso image in the virtual machine, happens over the settings of the mass storage
* the [lvm (logical volume manager)](https://en.wikipedia.org/wiki/Logical_volume_management)
* through installation of guest extension, graphical resolutions are optimized
* gren entry of the fiel after a
```bash
:~$ ls
```
command, shows that the file is runnable
* with <kbd>Tab</kbd> the command is auto-completed

# create a secure point

* vm saved in current state and ca be reset to this point at any time be reset
* create a backup point when the vm is switched off so that the memory does not have to be packed up unnecessarily
* creating a backup is recommended

# centos / red hat enterprise linux – installation

* In the settings of the VM under System select the pointer device USB-Tablet, because PS/2-Mouse is not recognized correctly by CentOS
* During installation, first leave default settings and select minimal installation
    * This approach is often the best for a server environment for comprehensive
Control which components are installed and active on the system
    * This reduces the attack surface (what is not there cannot be attacked) and increases
attack) and also increases performance, since unnecessary components do not require
take up resources
    * anything additional functionality we ned, we can install later if necessary
* the package collection system administration tools can be installed at the same time
* Root is the system administrator of a Unix or Linux system
* Set the password of root during installation and choose it wisely
* Create an additional user during installation and assign a password
* the system boots without a graphical user interface and offers us a text-based login on the
the console

# local login and logout on system

* centos
    * login with [root](https://en.wikipedia.org/wiki/Superuser#Unix_and_Unix-like) oder self-created user possible
    * the <code>~</code> symbol stands for home directory
    * the <code>$</code> symbol stands for end of the [prompt](https://en.wikipedia.org/wiki/Command-line_interface#Command_prompt) and shows that it is worked now without root priviliges
    * the <code>#</code> symbol shows that working as an admin is present
    * if command is going to be executed as a root, pwd is eneded
    * via <kbd>alt</kbd> + <kbd>F2</kbd> a second [console](https://en.wikipedia.org/wiki/Console) is opened and a new [session](https://en.wikipedia.org/wiki/Session_(computer_science)) can be started
    * via <kbd>alt</kbd> + <kbd>F1-6</kbd> can be switched betwen the sessions 
* ubuntu
    * gui proposes created user as a login
    * display name is not username
    * root does not exist per default on ubunut system
    * ubuntu instead uses [sudo](https://en.wikipedia.org/wiki/Sudo)
    * a [shell](https://en.wikipedia.org/wiki/Shell_(computing)) is the env in a [terminal](https://en.wikipedia.org/wiki/GNOMe_Terminal)

# root and su * working as super-user

* linux allows to open another session during the existing terminal-session to get temporarily root without leaving terminal session
* command for the aboce is called 

```bash
:~$ su
```
and means substitute user
* with no further options, the system thinks user wants to become root
* user is still in home directory. it is shown with

```bash
:~# pwd
```

* tilde is not shown anymore (so the home directory), instead the actual directory is shown
* behind the scenes, a new shell was started and the original shell still exists
* for each shell, certain env parameter are set. can differ dependeing on the user
* with

```bash
:~# su
```
or
```bash
:~# su -l
```
a new login-shell with new all env parameters will be created
* a part of it is the PaTH variable, the variable consists of all directories, that are searched through . so a user does not have to move to path to executable file

# sudo - if there is no root

* modified principle to su- [su"do"](https://ubuntu.com/server/docs/security-users)
* possibility to delegate admin tasks to normal user or user groups
* sudo primarily accesses a file called <code>/etc/sudoers</code> - all users are listed with respective privileges
* root is asigend to admin and group sudo, all privileges granted to him
* <code>%</code> in front of the name indicates a group
* all memebers of groups admin and sudo are de fact admins

# basic network configuration

* [Dynamic Host Configuration Protocol](https://en.wikipedia.org/wiki/Dynamic_Host_Configuration_Protocol) assigns a dynamic IP configuration
* [local are network](https://en.wikipedia.org/wiki/Local_area_network) refers to local network in office location
* [MaC address](https://en.wikipedia.org/wiki/MaC_address) is called [device address]() in ubuntu and is the hardware address
* [default gateway] is called [default route]() under ubuntu and denoes the [router]() through which the internet is accessed
* [dns server]() is responisble for the resolution of [ip addresses]()
* [subnet mask]() describes network and host part of ip address in ubuntu
* [ubuntu](https://en.wikipedia.org/wiki/Ubuntu)
    * a component called [network manager](https://en.wikipedia.org/wiki/NetworkManager) (GUI, but cmdl is also possible) controls network interface management. multifunction button in upper right corner * interface configuration: select lan settings to set ip parameters
* [centos](https://en.wikipedia.org/wiki/CentOS)
    * in dir <code>/etc/sysconfig/network-scripts</code> are network-related settings in form of configuration files and scripts.
    * relevant configuration is located in <code>ifcfg-enp0s3</code>
        * create backup copy before making changes
        * <code>bootproto=dhcp</code> sets the interface to DHCP
        * <code>bootproto=static</code> for a static IP configuration - set <code>IPaDDR=</code>, <code>NeTMaSK=</code> and <code>GaTewaY=</code>
        * <code>onboot=no</code> prevents interface from making a DHCP request at startup. at startup hash represents comments, so lines can be commented out
    * with service network restart the network interface is reinitialized with new configs
    * DNS servers specified in <code>/etc/resolv.conf</code>

# enter system via ssh

* [remote access](https://en.wiktionary.org/wiki/remote_access) - first configuration steps in the course of installing of [server](https://en.wikipedia.org/wiki/Server_(computing))
* mostly [SSH](https://en.wikipedia.org/wiki/Secure_Shell) used
* centos already in the minimal version a [SSH server](https://en.wikipedia.org/wiki/Comparison_of_SSH_servers) service is integrated, se <code>/usr/sbin/sshd</code>
* <code>-D</code> stands for [daemon](https://en.wikipedia.org/wiki/Daemon_(computing)), so started as a [service](https://en.wikipedia.org/wiki/Daemon_(computing))
* with SSH client a corresponding connection can be established
* under [windows](https://en.wikipedia.org/wiki/Microsoft_windows) for example [PuTTY](https://en.wikipedia.org/wiki/PuTTY) can be used to do this and open the connection (connection type = SSH). the SSH key of the server is not yet trusted. we confirm this and thus get to the login
* while in many default settings for SSH no root login via SSH is allowed, under centos we can also log in with root, otherwise with a normal user and then with normal user and then become root with su
* the SSH session behaves visually and contentwise like a normal console session, but we can change the display granularly in the PuTTY settings
* the SSH session can then be terminated by entering exit or simply by closing the window. be terminated

# ubuntu desktop * first round

* ubuntu first used [GNOMe](https://en.wikipedia.org/wiki/GNOMe) and then for many years its own default interface called [unity](https://en.wikipedia.org/wiki/Unity_(user_interface))
* however, since Ubuntu 17.10 Canonical has returned to the GNOMe desktop
* [nautilus](https://en.wikipedia.org/wiki/File_manager) filemanager
* most of the functions of the windows explorer are also present
* your ubuntu system has hundreds of other [linux programs and -tools](https://en.wikipedia.org/wiki/List_of_proprietary_software_for_Linux) that you can only start by calling them directly from the terminal

# hyperlinks

[https://w.virtualbox.org/](https://w.virtualbox.org/)

[https://ubuntu.com/download](https://ubuntu.com/download)

[https://w.centos.org/](https://w.centos.org/)

[https://w.putty.org/](https://w.putty.org/)

# the shell

* user interface betwen the user and the (Unix) system program to process commands, to access files or to execute other programs
* the [bash shell (Bourne-again shell)](https://en.wikipedia.org/wiki/Bash_(Unix_shell)) is standard shell in Linux, run it with terminal
* distinguish: login shells with pwd and non-login shells as well as interactive and non-interactive shells
* [shell scripting tutorial](https://w.tutorialspoint.com/unix/shell_scripting.htm)
* hidden files in linux * names start with a dot e.g. .bashrc

# pkg management

* resolving dependencies
    * e.g. firefox requires "[fretype](https://en.wikipedia.org/wiki/FreType)" and "[GTK2](https://en.wikipedia.org/wiki/GTK)", among others, in order to function: through the dependencies, these tw  * packages are installed in the correct version
installed as well
* different pkg mgmt depending on the distribution
    * ubuntu / debian uses apt / [dpkg](https://en.wikipedia.org/wiki/Dpkg) (program package: .deb)
    * red hat / centos uses [yum](https://en.wikipedia.org/wiki/Yum_(software)) (program package: .rpm)
    * converting program package possible but leads to problems

# pkg management with the ubuntu ui

* [synaptic package manager](https://en.wikipedia.org/wiki/Synaptic_(software)) * is used to install packages by means of a graphical interface

# install pkgs via terminal

* no graphical ui.
* command for pkg mgmt: [apt](https://en.wikipedia.org/wiki/aPT_(software)) (depending on the system also: apt-get or aptitude)
* sudo is neded when installing/updating packages
* ubuntu package list check/update
* install Ubuntu package list sudo apt upgrade
* sudo apt dist-upgrade adds additional new dependencies if neded * updates then also packages which ned a new dependency
* install Ubuntu package: sudo apt install paketname
* sudo apt install htop

# search for pkgs and sources (ubunut)

* [packages.ubuntu.com](https://packages.ubuntu.com/) / [packages.debian.com](https://w.debian.org/distrib/packages) * website with graphical interface for searching packages
* sudo apt search package name * terminal command for searching packages.
* path to file with package sources: /etc/apt/sources.list
* path to folder for own package sources: /etc/apt/sources.list.d

# additional package sources (ubuntu)

* Install downloaded package with:

```bash
# after installation, the package will also appear under /etc/apt/sources.list.d
:~$ sudo dpkg -i /path/toPackage/
```

# ubuntu and ppa

* [ppa (Personal Package archives)](https://en.wikipedia.org/wiki/Ubuntu#Package_archives)
    * make your own packages available
    * download packages from other users on your own risk

# compile packages manually (ubuntu)

```bash
# is neded to compile a package
:~$ sudo apt install make gcc g++ automake
```

* source code is neded
* on the website of the program is usually also a tutorial available how to compile this correctly
* after compiling the program can be started from the program folder

```bash
# also adds the program to the package management
:~$ su root make install
```

# pkg management under centos

```bash
# installation of a package
:~$ yum install paketname
```

```bash
# uninstalling a package
:~$ yum remove paketname
```

```bash
# bring installed package to older version
:~$ yum downgrade paketname
```

```bash
# search for a package
:~$ yum search paketname
```

* It is also possible to install packages via urls:

```bash
# important is the .rpm at the end
:~$ yum install https://LinkzumPaket.com/test.rpm
```

```bash
:~$ yum install repositoryname
```
* [epel (extra packages for enterprise linux)](https://en.wikipedia.org/wiki/Fedora_Project#extra_Packages_for_enterprise_Linux_(ePeL))
* when downloading a package for the first time, you confirm that you trust therepository. (Verify fingerprint)

# commandline  editors

[nano](https://en.wikipedia.org/wiki/GNU_nano)

[vi and vim](https://en.wikipedia.org/wiki/Vim_(text_editor))

[emacs](https://en.wikipedia.org/wiki/emacs)

# graphical editors

[gedit](https://en.wikipedia.org/wiki/Gedit)

[kate](https://en.wikipedia.org/wiki/Kate_(text_editor))

[notepad++ (exec with wine)](https://en.wikipedia.org/wiki/Notepad%2B%2B)

# user management

linux is a multiuser system: Several users can use the system, even simultaneously. each user usually has his own user account. mandatory is a user name with which the user logs on to the system. this name must be unique on the system. linux generally distinguishes betwen upper and lower case, this also applies to the
user names. the UID, i.e. the user ID, must also be unique and is normally assigned automatically by the system.
automatically
* special users have IDs below 1000, root e.g. always has ID 0
* normal users get an ID from 1000 upwards.
Users are given a login shell. this is the environment that is provided for them, when they log in to the console. dash stands for Debian almquist Shell and is used as the default shell for Debian derivatives.
* a user is assigned a home directory
    * root has his home directory under /root
    * normal user usually under /home/username
* Settings related to useradd and userdel are defined in the file /etc/login.defs file
* In the file /etc/default/useradd further defaults can be made
(e.g. setting the login shell as default when creating a new user)
* Groups are used to assign access rights to a resource to multiple accounts.
resource
* each user is assigned a main group. By default, a group with the same name and
group with the same name and ID as the user's group.
* alternatively, all users are assigned the same main group called users. It usually has
ID 100, but this is not as flexible, so on most systems users get their own group by default.
systems users get their own group by default
* Users can be members of more than one group and are sometimes automatically
assigned to certain additional groups
* the command usermod supports almost all options that are also provided by useradd. Unfortunately
the option -m does not work like with useradd. therefore the home directory
must be copied manually, and the access rights must be set accordingly.
* there are several system users. Because for security reasons many services of the
system are operated in the context of their own user, whose access rights can be set accordingly.
can be configured accordingly
* "Pseudo shells" like bin/false or /sbin/nologin do not provide an environment, respectively
prevent a user from logging in interactively. This is used as a security feature
to restrict system users to the system itself.
* Change age (chage) displays information from /etc/shadow in a more readable way in the terminal, and can adjust
(also dialog-guided) adjust parameters
* the main group of a user is recorded in /etc/passwd, therefore the user does not appear in
/etc/group again
* If a new group is created, the GID automatically continues counting from the last created ID high
* the program adduser provides a dialog-guided creation of users incl. password is provided
* the deluser program can use the --remove-all-files option to provide the user with delete all files of the user on the whole system
* the behavior of adduser and deluser can be controlled by the tw  * files /etc/adduser.conf and /etc/deluser.conf to customize the behavior of adduser and deluser.

# user management files

* user information is managed in thre files:
    * /etc/passwd
        * Login name
        * UID (user ID)
        * GID (main group ID)
        * GeCOS field (Comment field)
        * Home directory
        * Login shell
    * /etc/shadow
        * Login name
        * Password (as hash)
        * Date of the last password change (days since 1/1/1970)
        * Minimum number of days betwen tw  * password changes
        * Number of days on which a warning is issued about password expiration
        * Number of days until deactivation after the password has expired.
        * Date on which account is automatically deactivated
    * /etc/group
        * Group name
        * Group ID
        * Group members

# working with paths

* the cd command takes paths as parameters. these can be absolute or relative
    * absolute paths
        * Start with a / and describe the path to the desired directory starting from the topmost point in the file system
    * Relative paths

Describe the path to the destination starting from the current location
* the $OLDPwD variable contains the previous directory in which you were located
* to run a program, we have tw  * options:
    * we specify the absolute path in front of it
    * we write ./ in front of it, this stands for the current directory
* If we want to open files, e.g. with an editor, we can directly specify the file if it is located in the same directory

# Create and delete directories

* Under Ubuntu, the .profile file in the home directory specifies which paths are included in the the $PaTH variable
* Under CentOS, the .bash_profile file in the home directory determines which paths are are included in the $PaTH variable
* with mkdir directories are created, with rmdir directories are deleted (only empty directories without subfolders). with the option -p also with subfolders
* the command rm deletes files as well as directories. Be careful when using this command!

# understanding directories listings

* Output of the ls -l command (long format)
  * each file or subdirectory is on a separate line
  * the dot stands for the current directory and the colon for the
parent directory
  * the first column contains the file type
    * d stands for directory, i.e. a directory
    * * stands for normal files
    * l stands for Link, which are symbolic or soft links
    * c for Character Device, these are character-oriented devices (modems)
    * b for Block Device, these are block-oriented devices (storage media)
  * executable files are displayed in gren (based on the rights).
  * the rights are displayed accordingly
  * the number of links to this entry
  * the owner of the entry and the group the entry is assigned to
  * the size of the file is shown in bytes
  * Date of the last modification
* the command ls -F can use appended characters to indicate what type of entry it is
is concerned:
  * / directories
  * * executable files
  * @ symbolic links
* the command ls supports many options which can be combined flexibly.
with each other. Se man page of ls and command overview of this course
* the program tre shows very clearly the directory tre starting at a certain point.
point

# Create, copy, move and delete files

* there are thre common ways to create a file:
  * Create a file with touch
  * Open and save a non-existing file with an editor
  * Create and describe a file with ech  * and the redirect character
* with the command cp (copy) files can be copied (also under another name) with the option
the option -r even complete directories
* with the command mv (move) files can be moved and renamed.
Caution: If the destination is not a directory, but an existing file, this file will be overwritten with the contents of the source file.
the contents of the source file

# Creating hard links and softlinks

* a link is a reference to another file or directory
* Hard links
  * It is one and the same file that is referenced by means of an inode.
is referenced. This is a reference to a file, but in the file system table * quasi the ID of the file.
  * Hardlinks can exist only within a partition.
  * Hardlinks can be applied only to files, not to directories
  * If a Hardlink is deleted, then the original file still continues to exist
* Softlinks / Symbolic Links, short: Symlinks
  * with Symlinks references, thus links can be created partition-spreading.
  * This applies equally to files and directories
  * they are clearly easier to recognize, since they work with paths
  * If the original file is deleted, no copy exists any more

# archiving and compressing files

* In order to save data and files or to make them available, it is a good idea to pack them in an
archive file as a whole and compress it
* Saves space on the storage medium or bandwidth during transfer
* the most commonly used program for archiving is tar
* a tarball is an archive file created with tar and compressed with gzip or bzip2
* Bzip2(.bz2) and gzip(.gz) are compression methods
* Bzip2 is the newer and more effective variant
* Files with the extension tar are uncompressed archives which can be unpacked with tar -xf.
can be unpacked. after unpacking, the archive file still exists.
* archives usually contain several files and often directories. these can be displayed with
tar -tf to display them
* Several files and directories can be combined into one archive with tar -cf.
to an archive
* alternative to tar is cpio
* alternative to gzip and bzip2 is xz

# Understanding access rights to files and directories

* access rights to files and directories are represented with ls -l:
[https://en.wikipedia.org/wiki/File-system_permissions](https://en.wikipedia.org/wiki/File-system_permissions)
* This is what the access rights mean:
[https://linuxcommand.org/lc3_lts0090.php#:~:text=On%20a%20Linux%20system%2C%20eachthe%20file%20as%20a%20program](https://linuxcommand.org/lc3_lts0090.php#:~:text=On%20a%20Linux%20system%2C%20eachthe%20file%20as%20a%20program)
* Set access rights with chmod:
* User and groups can be set with chown, the command assumes by colon
separates user and group:
  * chown <user>:<group> <file>
* the second way is to use chown to set the user and chgrp to set the group
with chgrp:
  * chown <user> <file>
  * chgrp <group> <file>
* Set access rights with the Octal method: [https://docs.oracle.com/cd/e19455-01/805-7229/6j6q8svd8/](https://docs.oracle.com/cd/e19455-01/805-7229/6j6q8svd8/)

# Special rights * SUID bit, SGID bit and sticky bit

* If the user rights of a file are displayed with an S instead of an X, this is the
the Set UID bit or short: SUID bit. It ensures that the program is always executed with the
rights of the file owner
* the SUID bit can be set with chmod u=rwxs <file> or chmod 4755 <file>.
* the SGID bit ensures that a file with execute privileges always runs in the context of the
of the group. For a directory, the set GID bit ensures that the group specified for the
directory is inherited by all newly created subdirectories and files.
are inherited
* we can set the SGID bit with chmod g=rwxs <file> or chmod 2755 <file>.
* the sticky bit is set by a t instead of the x for Others, i.e. at the very end of the
rights list and is used e.g. for the /tmp directory.
* If the sticky bit is applied to a folder * and this is the only purpose * then
files and directories created in it can only be deleted or renamed by the file owner.
renamed
* It is set via the letter t or octal via the 1 in the fourth, preceding
digit

# Umask and the default permissions

* If a directory is created, then certain permissions are set by default:
  * rwx for the user,
  * rx for the group
  * rx for Others
* If a file is created, then certain permissions are set by default:
  * rw for the user,
  * r for the group
  * r for Others
* these default permissions are set with umask
* Since it is a mask, what is hidden, i.e. not set, is displayed
is set:
  * For directories, we subtract the umask from 7 each to get the set values.
are obtained. the first digit is ignored, since it concerns special rights that are not set in the
umask are not set anyway
  * For files the 6 is the initial value
* set umask:
  * For CentOS, system-wide: /etc/profile, for users: .bash_profile
  * For Ubuntu, system-wide: /etc/login.defs, for users: .profile

# Other functions of ls

* Downloading the course materials with wget
  * if not available sudo apt install wget / sudo yum install wget
* Unzip .zip with unzip filename.zip
  * unzip course materials.zip
* change to another folder/path with cd(change directory)
  * use backslash or quotation marks if there is a space in the folder name is present
    * cd 02\ -\ First Steps/ or cd "02 * First steps"/
* ls
  * Show files and folders in the current path
* ls "02 * First steps"/
  * output the contents of the path
* ls*
  * outputs all files/folders and subfolders
* ls 0*
  * outputs all files/folders that start with a 0
* ls */*.js
  * outputs all .js files in all folders

# find command 

* find
  * to search for files. More possibilities than ls
* find /work
  * Searches in the directory "/work".
* find /work /leisure
  * Searches in the directories "/work" and "/Leisure".
* find /
  * searches everywhere
* find /course materials -name "test"
  * searches in course materials for test
* find /coursematerials -name "*test*"
  * searches course materials for anything where the filename includes test.
* find . -size +1M -and -name "*skype*"
  * searches the current folder + all subfolders for files larger than 1Mb
and the file name contains skype.
* find / -size -1M -and -name "*skype*"
  * searches everywhere for files that are smaller than 1Mb and the filename contains skype.
* find . -name "*.JPG" -delete
  * searches in the current folder + all subfolders for all files with the extension .JPG and
deletes them. (case sensitive)
* find /Desktop name "*.JPG" -or -name "*.CR3"
  * searches the desktop for files with the extension JPG and CR3.
* man find
  * Calls the manual of find and displays all parameters

# locate command

* locate creates a database with all files and searches them.
  *find searches the files on the hard disk (Takes longer).
* Database must be kept up to date
If the name of a file has ben changed, it is not automatically in the database and cannot yet be found.
Database and cannot yet be found.
  *By default, the database is updated once a day under Ubuntu.
  *sudo updatedb
    * Command to update the database
* locate "filename"
  *searches for the corresponding file
* locate -i "filename"
  *searches for the corresponding file, upper and lower case is ignored
* locate -i -regex "ubuntu(.*)\.ISO"
  *searches for files that have Ubuntu in the name (or in the path) and end with ISO
* locate -i --regex * basename "ubuntu(.*)\.ISO"
  *searches for files that have Ubuntu in the name(path is ignored here) and end in ISO
end

# Grep, first steps with regular expressions
* with Grep you can search the contents of files grep "money"
  * searches all files in the current folder for money
* grep --count "money" *
  * searches all files in the current folder for money and returns the frequency of the word of the word
* grep -e -i 'Subject:(.*)money' *
  * searches all files in the current folder for Subject: ......money......(ignores upper and upper and lower case)
  * the word to be searched in single quotes because a regular expression is used!
  * (.*) means it doesn't matter how many and which characters come.

# the stream editor (sed)

[https://en.wikipedia.org/wiki/Sed](https://en.wikipedia.org/wiki/Sed)

[stream editor (sed) * overview](https://w.gnu.org/software/sed/manual/sed.html)

[sed commands](https://w.gnu.org/software/sed/manual/html_node/sed-commands-list.html)

# BIOS, UeFI, MBR

[https://de.wikipedia.org/wiki/BIOS](https://de.wikipedia.org/wiki/BIOS)

[https://de.wikipedia.org/wiki/Unified_extensible_Firmware_Interface](https://de.wikipedia.org/wiki/Unified_extensible_Firmware_Interface)

[https://de.wikipedia.org/wiki/Master_Boot_Record](https://de.wikipedia.org/wiki/Master_Boot_Record)

# GRUB2 * boot manager

[https://de.wikipedia.org/wiki/Grand_Unified_Bootloader](https://de.wikipedia.org/wiki/Grand_Unified_Bootloader)

[https://wiki.ubuntuusers.de/GRUB_2/](https://wiki.ubuntuusers.de/GRUB_2/)

# partitioning

* a partition is a logical volume on a physical or virtual hard drive
* advantage: logical partitioning of data, os backed up and restored independently of rest of the data on the disk
* each partition the file system can be defined separately - optimizes performance, so partitions can be administered separately encryption exchange or change of the medium

# file system repairs

* with the classical MBR partitioning a maximum of 4 partitions may be created extended partitions are not managed by the MBR. they can take up arbitrary logical partitions, which makes the limit disappear with the more modern GUID partition table a maximum of 128 partitions are allowed and there are n-differences in the kind of the partitions a swap partition holds data that should be swapped out of the main memory if it becomes tight there
* in the directory /dev are all device files, these refer to the hardware IDe hard disks are named hda, hdb, hdc etc.
* SCSI and SaTa hard disks are designated with sda, sdb, sdc etc.
* the number behind the designation indicates the partition
* the bootflag, recognizable by the asterisk, shows the BIOS or UeFI that it is possible to boot from this harddisk can be booted
* bootflag must be set explicitly during partitioning
* ubuntu does not create a swap partition by default
* MBR-based partitions can be managed with fdisk
* by default fdisk assigns the label 83 to every created partition, change to 82 linux swap

# File systems

* partitions are not yet usable for the operating system in the raw state
* partitions must be formatted with a file system
* journaling captures changes to the file system and can help to bring the file system file system back into a consistent state [https://en.wikipedia.org/wiki/File_system#Linux](https://en.wikipedia.org/wiki/File_system#Linux)
* to install XFS filesystem, first of all xfsprogs must be isntalled
* fomrating of file goes hand in hand with total loss of data

```bash
# check filesystem
:~$ fsck
```

```bash
# check filesystem
:~$ fsck
```

* after a certain time, the systems executes a check on the filesystem
* filesystems must be mounted to be used

[https://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard](https://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard)


```bash
# mountpoint can be created
:~$ mount
```

```bash
# mountpoint can be created
:~$ mount
```

* mounting must be done before the bootin of the system
* <code>/etc/fstab</code> provides a list of file systems, mount points, parameters, and options

```bash
# show all mounted filesystems
:~$ df
```

# Logical Volume Manager (LVM)

[https://en.wikipedia.org/wiki/Logical_Volume_Manager_(Linux)](https://en.wikipedia.org/wiki/Logical_Volume_Manager_(Linux))

[https://w.redhat.com/sysadmin/lvm-vs-partitioning](https://w.redhat.com/sysadmin/lvm-vs-partitioning)

# the Linux system boot at a glance

[https://en.wikipedia.org/wiki/Booting_process_of_Linux](https://en.wikipedia.org/wiki/Booting_process_of_Linux)

# Passing kernel options and boot parameters at system startup

[https://linuxconfig.org/how-to-set-kernel-boot-parameters-on-linux](https://linuxconfig.org/how-to-set-kernel-boot-parameters-on-linux)

[https://wiki.archlinux.org/title/kernel_parameters](https://wiki.archlinux.org/title/kernel_parameters)

[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters)

# Overview of SysVinit

[https://de.wikipedia.org/wiki/SysVinit#:~:text=SysVinit%20ist%20das%20init%2DSystem,die%20Prozess%2DID%201%20bekommt.](https://de.wikipedia.org/wiki/SysVinit#:~:text=SysVinit%20ist%20das%20init%2DSystem,die%20Prozess%2DID%201%20bekommt.)

# Introduction to Systemd

[https://de.wikipedia.org/wiki/Systemd#:~:text=systemd%20ist%20eine%20Sammlung%20von,und%20Beenden%20weiterer%20Prozesse%20dient.](https://de.wikipedia.org/wiki/Systemd#:~:text=systemd%20ist%20eine%20Sammlung%20von,und%20Beenden%20weiterer%20Prozesse%20dient.)

* SysVinit:
  * poweroff.target (symlink: runlevel0.target)
  * rescure.target (symlink: runlevel1.target)
  * multi-user.target (symlink: runlevel[2-4].target)
  * graphical.target (symlink: runlevel5.target)
  * reboot.target (symlink: runlevel6.target)

# Display processes and resource consumption

```bash
# Linux notation: options are prefixed with minus (-).
# BSD notation: Options are written without a minus sign
# GNU notation: double minus as introduction, then complete words
:~$ ps
```

# Running and managing programs in the foreground and background

```bash
# job in background
:~$ bg
```

```bash
# job in foreground
:~$ fg
```

# end processes

[https://www.linuxfoundation.org/blog/blog/classic-sysadmin-how-to-kill-a-process-from-the-command-line](https://www.linuxfoundation.org/blog/blog/classic-sysadmin-how-to-kill-a-process-from-the-command-line)

# Introduction to shared libraries

[https://tldp.org/HOWTO/Program-Library-HOWTO/shared-libraries.html](https://tldp.org/HOWTO/Program-Library-HOWTO/shared-libraries.html)

[https://www.tecmint.com/understanding-shared-libraries-in-linux/](https://www.tecmint.com/understanding-shared-libraries-in-linux/)

[https://opensource.com/article/20/6/linux-libraries#:~:text=Shared%20libraries%20are%20the%20most,memory%20usage%20by%20the%20application.](https://opensource.com/article/20/6/linux-libraries#:~:text=Shared%20libraries%20are%20the%20most,memory%20usage%20by%20the%20application.)

* shared libraries (program libraries) are routine functions that are required again and again and are and can be used by different programs on the system. can
  * advantage: It must not always all functions into each program be compiled in
  * disadvantage: the Shared Libraries must be available, otherwise the program does not run (dependencies)

[https://opensource.com/article/20/6/linux-libraries#:~:text=Shared%20libraries%20are%20the%20most,memory%20usage%20by%20the%20application.](https://opensource.com/article/20/6/linux-libraries#:~:text=Shared%20libraries%20are%20the%20most,memory%20usage%20by%20the%20application.)

* <code>/etc/ld.so.cache</code> contains all known shared libraries in binary form

# introduction, etc profile, etc bashrc

* 2 configuration files for shell
  * login shell is started e.g. via ssh <code>/etc/profile/</code> and <code>/etc/bash.bashrc</code>
  * non-login shell is used locally <code>/etc/bash.bashrc</code>
* code that should always be executed is then written to <code>bash.bashrc</code>
* NOTE: centos
  * cofiguration file here is called /etc/bashrc

# files bash_login und bash_logout

* when starting a login shell etc/profile is loaded
  * checks if ~/.bash_profile exists
    * if file exists it will be loaded
* if it does not exist
  * checks if ~/.bash_login exists
    * if file exists it will be loaded
* if it does not exist
  * checks if ~/.profile exists
    * if file exists it will be loaded
* at logout
  * ~/.bash_logout is loaded

# bash scripting

[https://wiki.ubuntuusers.de/Shell/Bash-Skripting-Guide_f%C3%BCr_Anf%C3%A4nger/](https://wiki.ubuntuusers.de/Shell/Bash-Skripting-Guide_f%C3%BCr_Anf%C3%A4nger/)

[https://de.wikipedia.org/wiki/Z_shell#:~:text=Die%20Z%20shell%20(zsh)%20ist,bash%2C%20ksh%20und%20tcsh%20vereint.](https://de.wikipedia.org/wiki/Z_shell#:~:text=Die%20Z%20shell%20(zsh)%20ist,bash%2C%20ksh%20und%20tcsh%20vereint.)

[Bash Scripting Tutorial](https://linuxconfig.org/bash-scripting-tutorial)

# Internationalization

[https://www.debian.org/doc/manuals/intro-i18n/](https://www.debian.org/doc/manuals/intro-i18n/)

[https://linuxwiki.de/i18n](https://linuxwiki.de/i18n)

[https://www.cyberciti.biz/faq/how-to-set-locales-i18n-on-a-linux-unix/](https://www.cyberciti.biz/faq/how-to-set-locales-i18n-on-a-linux-unix/)

[https://wiki.archlinux.org/title/locale](https://wiki.archlinux.org/title/locale)

## how to set locals by default (Ubuntu)
* file for environment variable <code>/locals</code>
  * <code>/etc/enviroment</code>
  * <code>/etc/locale</code>
  * <code>/etc/default/locale</code>

```bash
# updates the environment variable of LC_TIME
:~$ sudo update-locale LC_TIMe="bg_BG.utf-8"
```

## how to set locale by default (CentOS)

```bash
# sets the LC_TIMe temporarily to en_US
:~$ LC_TIMe="en_US.utf-8" date
```

```bash
# set the environment variables to the appropriate values
:~$ localectl set-locale LaNG=en_De.utf8 LC_TIMe=bg_BG.utf8 LC_NUMeRIC=en_US.utf8
```

* <code>/etc/locale.conf</code>
  * locals are stored here
  * at login /etc/profile.d/lang.sh is executed

# change time zones (CentOS)
* timedatectl status
  * outputs all information about the time. (time zones etc)
* timedatectl list-timezones
  * prints a list of all time zones
* tzselect
  * programme for easy selection of time zones
* timedatectl set-timezone europe/Berlin * changes the time zone to Berlin
  * changes the timezone to Berlin
* /usr/share/zoneinfo/
  * here you can find information about the time zones

## change time zones (Ubuntu)
* /usr/share/zoneinfo/
  * here you can find information about the time zones
* /etc/timezone and /etc/localtime need to be changed.
* sud * dpkg-reconfigure tzdata
  * command to reconfigure tzdata
  * simple menu to select timezone

## TZ and tzselect
* environment variable TZ
  * a timezone for a user can be written in here
* export TZ="asia/Bangkok"
  * sets the environment variable TZ

# encodings

## part1 - ascii, iso-8859

[https://wiki.ubuntuusers.de/Zeichensatz-Konverter/](https://wiki.ubuntuusers.de/Zeichensatz-Konverter/)

[https://man7.org/linux/man-pages/man7/ascii.7.html](https://man7.org/linux/man-pages/man7/ascii.7.html)

[https://wiki.ubuntuusers.de/ASCII-Art/](https://wiki.ubuntuusers.de/ASCII-Art/)

## part2 - unicode, utf-8

[https://en.wikipedia.org/wiki/Unicode_input](https://en.wikipedia.org/wiki/Unicode_input)

[https://linuxwiki.de/UniCode](https://linuxwiki.de/UniCode)

[https://wiki.ubuntuusers.de/Sonderzeichen/](https://wiki.ubuntuusers.de/Sonderzeichen/)

[https://en.wikipedia.org/wiki/UTF-8](https://en.wikipedia.org/wiki/UTF-8)

[https://tldp.org/HOWTO/Unicode-HOWTO.html](https://tldp.org/HOWTO/Unicode-HOWTO.html)

# Convert encodings (ivonc)

[https://en.wikipedia.org/wiki/Iconv](https://en.wikipedia.org/wiki/Iconv)

[https://man7.org/linux/man-pages/man1/iconv.1.html](https://man7.org/linux/man-pages/man1/iconv.1.html)

# the other cron folders

[https://www.cyberciti.biz/faq/where-is-the-crontab-file/#:~:text=By%20default%20cron%20service%20(also,in%20%2Fetc%2Fpasswd%20file.](https://www.cyberciti.biz/faq/where-is-the-crontab-file/#:~:text=By%20default%20cron%20service%20(also,in%20%2Fetc%2Fpasswd%20file.)

[https://wiki.ubuntuusers.de/Cron/](https://wiki.ubuntuusers.de/Cron/)

[https://de.wikipedia.org/wiki/Cron](https://de.wikipedia.org/wiki/Cron)

* <code>/etc/crontab</code>
  * here is specified when the other folders are executed
  * own cronjobs can be overwritten by updates if necessary
* In the following folders, scripts can be created that are to be executed daily, hourly, etc. (will not be overwritten in case of an update)
  * <code>/etc/cron.d</code>
  * <code>/etc/cron.daily</code>
  * <code>/etc/cron.hourly</code>
  * <code>/etc/cron.monthly</code>
  * <code>/etc/cron.wekly</code>



# Cronjobs for users
* by default all users are forbidden to create their own cronjobs if <code>cron.allow</code> or <code>cron.deny</code> do not exist
  * exception: under Ubuntu it is allowed if both files do not exist
* <code>/etc/cron.allow</code> (whitelist)
  * here you can simply write the usernames that are allowed to create cronjobs are allowed
* <code>/etc/cron.deny</code> (blacklist)
  * if this file exists all users are allowed to use cronjobs except those in this file

```bash
# create cronjobs as a user
:~$ crontab -e
```

* <code>/var/spool/cron/crontabs</code>
  * Location of the user cronjobs

# check log files

* centos
  * <code>/var/log/cron</code>
* ubuntu
  * <code>/var/log/syslog</code>
  * syslog konfigurieren
    * <code>etc/rsyslog.c/50-default.conf</code>
      oder
    * <code>/etc/rsyslog.conf</code>

# the tool at

[https://wiki.ubuntuusers.de/at/](https://wiki.ubuntuusers.de/at/)

# anacron and anacrontab

[https://de.wikipedia.org/wiki/Anacron](https://de.wikipedia.org/wiki/Anacron)

[https://man7.org/linux/man-pages/man5/anacrontab.5.html](https://man7.org/linux/man-pages/man5/anacrontab.5.html)

# let programs run in the background

```bash
# with the & at the end the program is executed in the background
:~$ wget https://Linkzumdownload.de/test.zip &
```

* output of the programme is redirected to a log which is created automatically.

```bash
# shows the currently active commands
:~$ jobs
```

```bash
# brings the last used programme back to the foreground
:~$ fg
```

* <kbd>CTRL</kbd> + <kbd>Z</kbd>
  * brings the programme back to the background, but is paused

```bash
# the programme is executed again
:~$ bg
```

```bash
# shows active processes in the system
:~$ ps
```

```bash
# kills the programme with the processID
:~$ kill processid
```

```bash
# kills the programme directly
:~$ kill -9 processid
```

```bash
# program continues to run in the background even if the shell is closed
:~$ nohup wget https://Linkzumdownload.de/test.zip &
```

# bonus

```bash
# tree structure of processes
:~$ pstre
```

```bash
# tree structure of a certain process
:~$ pstre prozessid
```

# share terminal with others - scren command

```bash
# installs scren
:~$ sudo apt-get install scren
```

```bash
# start program
:~$ scren
```

```bash
# connects with active scren instance
:~$ scren -x
```

* set the size of the shell
  * <kbd>STRG</kbd> + <kbd>a</kbd> + <kbd>F</kbd>
leave scren but it continues running in background
* <kbd>STRG</kbd> + <kbd>a</kbd> + <kbd>cD</kbd>

```bash
# in case more scren processes are active
# ID has to be passed to process 
:~$ scren -x -r ID
```

# command substitution

* currentDate=$(date +"%Y-%m-%d")
  * writes the command date into the variable currentDate
* cp hallo.txt hallo.txt.$currentDate
  * copies hallo.txt and creates the file hallo.txt.2019-07-30
    * command in the variable is executed
and the output is written into the name of the new file
* contents=$(cat hello.txt)
  * ech * "$contents"
    * outputs the contents of the file hello.txt

# Bundle commands in one function

```bash
# creates the function hall * with the code: ech * "Hall * world"
# if you now enter a hall * in the console the function will be executed
:~$ hallo() { ech * "Hall * world";};
```

```bash
# creates the function with a passing parameter
# hello(test) then outputs test
:~$  hallo() { ech * $1}
```

# standard output, standard error

* write programme output to a file
  * via <code>></code> output of a programme can be written to a file
    * <code>date > output.txt</code>
* creates the file output.txt in the current folder
and writes the output of date into it
* If something is already written in the file, it will be overwritten.
  * <code>>></code> can be used to append the output of a programme to a file.
    * <code>date >> output.txt</code>
* the output of date is written to the file output.txt without deleting the existing content is deleted
  * <code>></code> or <code>>></code> (shorthand) can also be written 1> or 1>>.
* write error output to a file
  * via 2> errors can be written to a file
    * <code>cat fileexistsnot.txt 2> output.txt</code>
* the error that a file was not found is written to output.txt
* programme output and error output can also be linked
  * <code>cat asdafasd.txt 1> programme-out.txt 2> programme-err.txt</code>
    * writes the output of the programme to program-out.txt and if an error occurs it is written to program-err.txt
* <code>1></code> stands for the first "channel" of the programme output
* <code>2></code> stands for the second "channel" the error output

# redirect stderr to stdout

## part 1

* <code>(date +"%Y" && cat s.txt) 1> output.txt 2> output.txt</code>
  * writes the output of the programme to the file output.txt, but this is overwritten
which is overwritten because an error occurs.
  * This could be avoided as follows:
(but is s * not used as there are better ways).
  * <code>(date +"%Y" && cat s.txt) 1>> output.txt 2>> output.txt</code>
* with 2>&1 the error output can be redirected to the programme output
* <code>(date +"%Y" && cat s.txt) > output.txt 2>&1</code>
  * writes the programme output and the error to the file output.txt

## part 2

* Order is important
  * Correct:
<code>(date +"%Y" && cat s.txt) > output.txt 2>&1</code>
  * Incorrect:
~~(date +"%Y" && cat s.txt) 2>&1 > output.txt~~
* otherwise the programme output is overwritten and only the error is written in output.txt.

# the device dev null
* <code>/dev/null</code>
  * for Linux a device
  * output of a command is discarded
    * <code>echo "Test" > /dev/null</code>
* <code>cat /dev/random</code>
  * outputs random data (binary)
* <code>cat /dev/urandom</code>
  * outputs infinite pseud * random data(binary)

# the exit code of programs

* <code>$?</code>
  * exit variable
  * 0 - program was executed correctly
  * 1 - (rarely also 2 or 3) means an error has occurred
  * variable is overwritten after each executed command
* <code>echo $?</code>
  * outputs the exit variable
  * it can be checked whether the last command was successfully executed

# stdin
* <code>sort</code>
  * entries can be made which are then sorted
  * CTRL + D terminates the input
* <code>sort < name.txt</code>
  * sends the file name.txt to the sort programme
  * name.txt is used as standard input for sort
sort gets name.txt not as a file but as normal input
* <code>sort < name.txt > name-sorted.txt</code>
  * passes the name.txt file to sort and writes the output of the program to name-sorted.txt
* < allows chaining of commands with passing

# | - operator (pipe operator)

* the pipe operator |<
  * <code>ls | sort</code>
passes the output of ls directly to sort
* <code>ls | sort -r</code>
  * passes the output of ls to sort
  * sort reverses the sorting by -r
* | can also be used to pass the output of programs
  * < takes only the contents of a file
  * <code>sort < script.sh</code>
    * sricpt.sh is considered a file
  * <code>./scipt.sh | sort</code>
    * the output of sricpt.sh is passed on
*<code> cat /proc/cpuinf * | grep "model name"</code>
  * the output of cat is passed to grep and searched for model name

# te

* <code>ls | xargs echo</code>
  * xargs converts the standard input from ls into parameters so that ech * can use them. can use them
  * <code>ls | ech *</code> would output nothing
* <code>ls /etc | te output.txt | grep "cron"</code>
  * output of ls is passed to te which then saves it to a file this output is then passed on to grep which searches it for cron
* <code>te -a output.xt</code>
  * output is appended to the file by the parameter -a

# set system time and date
* time is important for several reasons:
  * log entries are dated by means of time stamps
  * authentication processes are partly carried out using time stamps (e.g. Kerberos, certificates)
* Coordinated universal time is called UTC (Universal Time Coordinated), formerly GMT.
* Summer time in Europe is called CeST (Central european Summer Time).
* the date command displays the time and allows you to set the system time stamp
* there is a system time and a hardware time (mainboard)
* <code>hwclock</code> displays the hardware time
* <code>cat /etc/adjtime</code> shows in which time form the hardware time is set, usually UTC
* hardware time and system time can be set and synchronised manually

# time synchronisation with NTP

* ntp (Network Time Protocol) enables automatic time synchronisation with time servers
* ntp distinguishes between stratum values:
  * stratum 0: the time source itself (e.g. atom* or radio clock).
  * stratum 1: Systems that get the time directly from the time source.
  * stratum 2: systems that get the time from stratum 1 servers
  * etc
  * [https://w.ntppool.org/en/](https://w.ntppool.org/en/)

* ubuntu uses a daemon called timesyncd from Systemd to synchronise the time.
* ntpdate can be used to set a time server for NTP, ntpdate is deprecated.
* ntpd is the more modern command, it is configured via /etc/ntp.conf
* ntpd is a daemon that binds to port 123/udp and listens for NTP requests.
* various time servers can be specified via the configuration of NTP server pools.
* if the time deviates, NTP can adjust the time value smoothly - the time then runs faster or slower for a while time runs faster or slower, as the case may be (this avoids errors and time jumps)
* on shutdown, the time daemon overwrites the value of the hardware clock

# system logging

* linux logs mainly to /var/log
* main log files are <code>/var/log/messages</code> (CentOS, SuSe, etc.) or <code>/var/log/syslog</code> (DebianDerivate)
* there are dedicated logfiles for many special events (auth.log, kern.log, btmp and wtmp).
* by default, a ring buffer is used, i.e. the oldest messages are overwritten at some point overwritten
* other components, such as server services, sometimes create their own subdirectories for logging under /var/log their logging under <code>/var/log</code>
* log entries are usually in plain text (btmp and wtmp as well as the systemd journal are exceptions). are exceptions)
* the ccze programme allows log entries to be coloured.

# understanding the syslog concept

* [syslog](https://en.wikipedia.org/wiki/Syslog) is an old standard supported by many systems
* syslog messages have a specific structure:
  * origin(facility)
  * severity
  * event
* the syslog daemon [rsyslogd](https://en.wikipedia.org/wiki/Rsyslog) is the most common under Linux, it is configured in <code>/etc/rsyslog.conf.</code> configured

https://en.wikipedia.org/wiki/Syslog

# Configure the syslog daemon

* rsyslogd runs as a daemon in the context of the syslog user
* <code>/etc/rsyslog.conf</code> is the main configuration file, which mainly includes files under <code>/etc/rsyslog.d</code>
* under Ubuntu, the file /etc/rsyslog.d/50-default.conf is included, which contains the main entries.
* this may be regulated differently on other distributions
* on CentOS, these rules are contained directly in <code>/etc/rsyslog.conf.</code>

# Configure remote logging

* in rsyslog.conf the module imudp or imtcp must be activated
* by default port 514/udp is used
* on the syslog client, an entry is created in the rules in /etc/rsyslog.conf whose action contains @<server-address>

# use logrotate

* the logrotate programme can be used to rotate log files.
* logrotate does not run as a service, but is started by Systemd (Ubuntu) or crond (CentOS). started
* the configuration of logrotate can be found in <code>/etc/logrotate.conf.</code>
* It contains settings for the rotation cycle, the number of backlogs to be cancelled, and so on.
<code>/etc/logrotate.d/</code> may contain further files for configuring certain components of the system, e.g. the components of the system, e.g. CUPS or apache2

# the systemd journal

* the [systemd](https://en.wikipedia.org/wiki/Systemd) journal is a second log level, Systemd logs in parallel to Syslog.
* the service responsible for this is journald
* the journal can be displayed via the command journalctl
* the command supports numerous options for formatting, filtering and displaying old journals

# guis under linux

[x window system](https://en.wikipedia.org/wiki/X_Window_System) ([x11](https://en.wikipedia.org/wiki/X11_(disambiguation)))

# Grundlegende Netzwerkeinstellungen abfragen

[networkmanager](https://wiki.ubuntuusers.de/NetworkManager/)

[network configurations](https://wiki.debian.org/NetworkConfiguration)

[tool ss](https://man7.org/linux/man-pages/man8/ss.8.html)

[ifconfig](https://de.wikipedia.org/wiki/Ifconfig)

[netstat](https://de.wikipedia.org/wiki/Netstat)

[net-tools](https://wiki.linuxfoundation.org/networking/net-tools)

# basic IP configuration on the command line

[https://www.tecmint.com/ifconfig-command-examples/](https://www.tecmint.com/ifconfig-command-examples/)

# DNS with dig & Co. Testing

* linux implements the nameservice switch, or nsswitch for short, a concept which the basic resolution of names into numerical values: configuration file: <code>/etc/nsswitch.conf</code>
* there are various components, such as <code>passwd</code>, <code>group</code>, <code>shadow</code>, <code>hosts</code> or <code>protocols</code>, that require resolution to numeric values
* for user administration using passwd, group, etc., the corresponding files are first corresponding files are consulted first, as * e.g. <code>/etc/passwd</code>, <code>/etc/group</code> or <code>/etc/shadow</code>
* if no resolution can be made there, a systemd mechanism may be asked for shared libraries regulate how this is addressed.
* for host names, the <code>/etc/hosts</code> file is queried first.
* as a rule, the hosts file is always queried before the DNS mechanism, entries can be made here, the name resolution of which can be freely selected.
* after this comes mdns4_minimal, mDNS stands for Multicast DNS and is a special, newer service which
service that attempts to resolve DNS names via multicast in the local network.

```bash
# Get entity and enables the targeted reading of an entry from one of the
# from one of the administrative database files, such as passwd, hosts, etc.
:~$ getent
```

[https://en.wikipedia.org/wiki/Nslookup](https://en.wikipedia.org/wiki/Nslookup)

```bash
# change the query type and ask for mailserver (mx) or the name server (ns)
:~$ host -t
```

```bash
# queries for a records by default
:~$ dig
```

```bash
# dig does not automatically reverse-resolve, you need to set the -x option
:~$ dig @192.168.1.254 -x 8.8.8.8
```

# set the hostname

```bash
# show hostname
:~$ hostname or uname -u
```

```bash
# complete hostname with domain and toplevel domain
:~$ hostname -f
```

```bash
# set hostname
:~$ systemctl set-hostname "Name"
```

* even if an entry has been created in the /etc/hosts file, other systems in the network can use this name network can use this name

# static routes

[https://en.wikipedia.org/wiki/Routing](https://en.wikipedia.org/wiki/Routing)

[https://en.wikipedia.org/wiki/Static_routing](https://en.wikipedia.org/wiki/Static_routing)

[https://en.wikipedia.org/wiki/Dynamic_routing](https://en.wikipedia.org/wiki/Dynamic_routing)

# Network troubleshooting

[https://en.wikipedia.org/wiki/Troubleshooting](https://en.wikipedia.org/wiki/Troubleshooting)

[https://www.tecmint.com/linux-network-configuration-and-troubleshooting-commands/](https://www.tecmint.com/linux-network-configuration-and-troubleshooting-commands/)

# cups & c - the printing system standards

[v printing system](https://en.wikipedia.org/wiki/System_V_printing_system)

[berkeley printing system](https://en.wikipedia.org/wiki/Berkeley_printing_system)

# Set up printer in CUPS

* [cups](https://wiki.ubuntuusers.de/CUPS/) is pre-installed on many Linux systems.
* printer management is web-based via browser with <code>localhost:631</code>
* the cups configuration is located in <code>/etc/cups</code>
* In the <code>printers.conf</code> file, which we can only open as admin, we can see the configured printers with their settings.
* main configuration file for this process is <code>/etc/cups/cupsd.conf</code>

# printer management on cmdl

```bash
# printing from the command line
# -d (for Destination) allows you to specify the desired printer
# without -d, the document is sent to the queue of the default printer
:~$ lp -d MyPrinter textfile.txt
```

```bash
# -P (for Printer) allows you to specify the desired printer
# Without -P, the document is sent to the queue of the default printer
# 
:~$ lpr -P MyPrinter textfile.txt
```

```bash
# all jobs are displayed
:~$ lpq -a
```

```bash
# deletes all print jobs for the specified printer at once
:~$ lprm -P MyPrinter
```

# manage apache2 installation and server service

[apache http server](https://en.wikipedia.org/wiki/Apache_HTTP_Server)

[apache in debian](https://wiki.debian.org/Apache)

[Install and Configure Apache in Ubuntu](https://ubuntu.com/tutorials/install-and-configure-apache#1-overview)

# create virtual hosts

* possibility to host several web presences on one webserver
* concept based on [HTTP 1.1](https://en.wikipedia.org/wiki/HTTP)
* http header contains the dns name
* name resolution must be set up
* vonfiguration of a VirtualHost under Ubuntu:
* In the directory /etc/apache2/sites-available, a new file is created for webpresence´create:
  * e.g. 001-gulugulu.conf:
  * <VirtualHost *:80> * creates a VirtualHost section.
  * ServerName w.gulugulu.local * defines the DNS name that must be in the must be in the host header
  * Serveralias gulugulu.local * defines further aliases on which the server should respond to
  * DocumentRoot /var/w/gulugulu * Directory for content of the web presence set
  * Settings for the DocumentRoot directory:
    * <Directory /var/w/gulugulu> * creates a directory section for the directory
    * options FollowSymLinks * server symlink in directory follows to origin
    * allowOverride None * globally valid settings cannot be overridden. be overridden. In principle, a file called .htaccess can be used in a separate settings can be made in a publishing directory via a file called .htaccess. in a publishing directory
  * Require all granted * all users have access to this website. Here access could also be restricted to certain users or IP addresses. to certain users or IP addresses
  * </Directory> - closes the section and the settings for the directory
  * </VirtualHost> - terminates the VirtualHost configuration
  * A symlink must then be created for this configuration file in the sites-enabled directory. directory
  * Alternatively, the command a2ensite 001-gulugulu.conf can be used to activate the VirtualHost. is also activated Configuration of a VirtualHost under CentOS:
  * Either a separate file can be created under /etc/httpd/conf.d, which has the extension conf and fill it accordingly, or the VirtualHost definition can be written directly into httpd.conf.
  * Preferably external files should be used for a better overview.
  * If the IP is entered directly, the specific VirtualHost is also displayed. Better is to create another VirtualHost configuration without ServerName directive, to create a default web presence here

# prepare [mysql](https://en.wikipedia.org/wiki/MySQL) for [lamp](https://en.wikipedia.org/wiki/LAMP_(software_bundle))

* checkout further education to get into that subject

# basics of mail communication

[Email](https://en.wikipedia.org/wiki/Email)

# setup mailserver postfix

* Mail server systems usually consist of various components and are comparable to web platforms
* all linux systems used sendmail, one of its successor is [postfix](https://en.wikipedia.org/wiki/Postfix_(software)) (others are [qmail](https://en.wikipedia.org/wiki/Qmail) or [exim](https://en.wikipedia.org/wiki/Exim))
* nowadays, the Internet often only accepts mail from mail servers with an appropriate reputation reputation. the sending of mails by a self-created mail server is therefore often rejected
  * For this reason, many internal mail servers send their mails to a mail server of the provider (smarthost), which has a corresponding reputation and sends the mails to the addressee.

```bash
# list of all available configuration options of postfix
:~$ postconf
```

* the configuration files for Postfix are located in <code>/etc/postfix</code>
* most important config file = <code>main.cf</code>
* smtpd_relay_restrictions directive determines from which clients mails are forwarded - to prevent unauthorised systems from routing mails through the mail server and turning the mail server into an open relay
* permit_mynetworks option means that all ip addresses and subnetworks contained in the variable <code>mynetworks</code> are allowed to send mails via this mail server

```bash
# lists all domains for which this mail server is responsible
:~$ mydestination
```

```bash
# mail server is restarted
:~$ systemctl restart postfix
```

```bash
# check that postfix is running
:~$ systemctl status postfix
```

# smtp communication via telnet

* perform an SMTP session manually via telnet

```bash
# establishes a connection with the help of Telnet via port 25 (SMTP) with the mail server
:~$ telnet <IP-Mailserver> 25
```

* compose  mail within telnet communication:

> mail from: absender@domian.de
> 
> rcpt to: empfaenger@domain.de
>
> data
> 
> subject: Subject
> 
> text content of the mail, concluded with a dot ("."), composition of mail is a single line

* users' mailboxes are located under <code>/cvar/mail</code>. created as soon as a user receives first e-mail

# configure mail-aliases and redirections

* in <code>/etc/aliases</code>, aliases and forwardings are set up.
* after each change to the aliases file, the command newaliases must be executed.
* mail server must be restarted for the changes to take effect.
* mail program can be installed with

```bash
# (for centos package 'mailx')
:~$ sudo apt-get install mailutils
```

```bash
# initiates creation of a mail by the tool mail
:~$ sudo apt-get install mailutils
```

```bash
# display the current mail queue
:~$ mailq
```
