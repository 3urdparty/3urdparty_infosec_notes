## Grouping
Among other things, regex offers us the possibility to group the desired search patterns. Basically, regex follows three different concepts, which are distinguished by the three different brackets:
Grouping Operators
	Operators 	Description
1 	(a) 	The round brackets are used to group parts of a regex. Within the brackets, you can define further patterns which should be processed together.
2 	[a-z] 	The square brackets are used to define character classes. Inside the brackets, you can specify a list of characters to search for.
3 	{1,10} 	The curly brackets are used to define quantifiers. Inside the brackets, you can specify a number or a range that indicates how often a previous pattern should be repeated.
4 	| 	Also called the OR operator and shows results when one of the two expressions matches
5 	.* 	Also called the AND operator and displayed results only if both expressions match

>[!INFO] To use these operators in `grep`, you need to apply the extended regex using the `-E` option in grep.


## Operators

### OR operator
```bash
cry0l1t3@htb:~$ grep -E "(my|false)" /etc/passwd
```

## Grouping Operators
| Operators | Description                                                                                                                                     |
| --------- | ----------------------------------------------------------------------------------------------------------------------------------------------- |
| (a)       | The round brackets are used to group parts of a regex. Within the brackets, you can define further patterns which should be processed together. |
2 	[a-z] 	The square brackets are used to define character classes. Inside the brackets, you can specify a list of characters to search for.
3 	{1,10} 	The curly brackets are used to define quantifiers. Inside the brackets, you can specify a number or a range that indicates how often a previous pattern should be repeated.
4 	| 	Also called the OR operator and shows results when one of the two expressions matches
5 	.* 	Also called the AND operator and displayed results only if both expressions match
lxd:x:105:65534::/var/lib/lxd/:/bin/false
pollinate:x:109:1::/var/cache/pollinate:/bin/false
mysql:x:116:120:MySQL Server,,:/nonexistent:/bin/false


## Permission Management
Let us look at all the representations associated with it to understand better how the permission assignment is calculated.

```bash
Binary Notation:                4 2 1  |  4 2 1  |  4 2 1
----------------------------------------------------------
Binary Representation:          1 1 1  |  1 0 1  |  1 0 0
----------------------------------------------------------
Octal Value:                      7    |    5    |    4
----------------------------------------------------------
Permission Representation:      r w x  |  r - x  |  r - -
```


```bash
cry0l1t3@htb[/htb]$ chown <user>:<group> <file/directory>
```

```bash
cry0l1t3@htb[/htb]$ chown root:root shell && ls -l shell
```

## SUID & GUID
Setting `SUID` and `GUID` bits allow users/groups to run programs with the rights of another user. The letter "s" is used instead of an "x". When executing such a program, the SUID/GUID of the file owner is used.

## Sticky Bit
Sticky bits are a type of file permission in Linux that can be set on directories, prevents  deletion and renaming of files within a directory. 

Is represented by the letter `t` in the execute permission of the directory's permissions. 

```bash
drw-rw-r-t 3 cry0l1t3 cry0l1t3   4096 Jan 12 12:30 scripts
```

## User management
| Command | Description                          |
| ------- | ------------------------------------ |
| sudo    | Execute command as a different user. |
su 	The su utility requests appropriate user credentials via PAM and switches to that user ID (the default user is the superuser). A shell is then executed.
useradd 	Creates a new user or update default new user information.
userdel 	Deletes a user account and related files.
usermod 	Modifies a user account.
addgroup 	Adds a group to the system.
delgroup 	Removes a group from the system.
passwd 	Changes user password.

## Package managers
Command 	Description
dpkg 	The dpkg is a tool to install, build, remove, and manage Debian packages. The primary and more user-friendly front-end for dpkg is aptitude.
apt 	Apt provides a high-level command-line interface for the package management system.
aptitude 	Aptitude is an alternative to apt and is a high-level interface to the package manager.
snap 	Install, configure, refresh, and remove snap packages. Snaps enable the secure distribution of the latest apps and utilities for the cloud, servers, desktops, and the internet of things.
gem 	Gem is the front-end to RubyGems, the standard package manager for Ruby.
pip 	Pip is a Python package installer recommended for installing Python packages that are not available in the Debian archive. It can work with version control repositories (currently only Git, Mercurial, and Bazaar repositories), logs output extensively, and prevents partial installs by downloading all requirements before starting installation.
git 	Git is a fast, scalable, distributed revision control system with an unusually rich command set that provides both high-level operations and full access to internals.

### APT
Debian-based Linux distributions use the APT package manager. A package is an archive file containing multiple ".deb" files. The dpkg utility is used to install programs from the associated ".deb" file. APT makes updating and installing programs easier because many programs have dependencies. When installing a program from a standalone ".deb" file, we may run into dependency issues and need to download and install one or multiple additional packages. APT makes this easier and more efficient by packaging together all of the dependencies needed to install a program.

Each Linux distribution uses software repositories that are updated often. When we update a program or install a new one, the system queries these repositories for the desired package. Repositories can be labeled as stable, testing, or unstable. Most Linux distributions utilize the most stable or "main" repository. This can be checked by viewing the contents of the /etc/apt/sources.list file. The repository list for Parrot OS is at /etc/apt/sources.list.d/parrot.list.

Advanced Package Manager (APT)

theycallmemuzz@htb[/htb]$ cat /etc/apt/sources.list.d/parrot.list


```bash
# parrot repository
# this file was automatically generated by parrot-mirror-selector
deb http://htb.deb.parrot.sh/parrot/ rolling main contrib non-free
#deb-src https://deb.parrot.sh/parrot/ rolling main contrib non-free
deb http://htb.deb.parrot.sh/parrot/ rolling-security main contrib non-free
#deb-src https://deb.parrot.sh/parrot/ rolling-security main contrib non-free
```


APT uses a database called the APT cache. This is used to provide information about packages installed on our system offline. We can search the APT cache, for example, to find all Impacket related packages.
Advanced Package Manager (APT)

```bash
theycallmemuzz@htb[/htb]$ apt-cache search impacket
impacket-scripts - Links to useful impacket scripts examples
polenum - Extracts the password policy from a Windows system
python-pcapy - Python interface to the libpcap packet capture library (Python 2)
python3-impacket - Python3 module to easily build and dissect network protocols
python3-pcapy - Python interface to the libpcap packet capture library (Python 3)
```



### Git
