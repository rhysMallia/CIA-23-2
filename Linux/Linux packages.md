self contained  archive for application installs

Executables -
man pages
Config files
Build instructions

Upgrading
uses .deb packages and the apt package manager
	list needs to be updated before installing
		Sudo apt update
	To update core packages
		Sudo apt upgrade
some require boutique methods

Commands
Sudo apt (install remove) packagename
sudo apt purge packagename ; remove a package and all files
sudo apt list --installed;
sudo apt autoremove; remove deprecated packages after 
sudo apt-mark hold packagename; hold a specific version of the package

Apt locks
checks for security updates faily, locks the process and prevents install, common when turning the machine on
- To bypass ..
	- Sudo killall apt
	- fuser -k /var/lib/apt/lists/lock

Manual install
dpkg (-i -r) packagename
dpkg --list ; manually list

**Current packages** are stored in a repoitory server (.deb /.rpm) and retrieved by a package manager (etc yay)
- Do you truest the repo?
- Do you trust the package?
- Security risks

**Old style packages** are usually tarballs
	Contained source code and make file
	Extract, ./configure; make; make install
User can examine and alter source prior to compilation
	Responsible for making dependencies

