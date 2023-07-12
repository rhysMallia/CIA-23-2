open source unix based operating system.

**File system**
	Everything is a file, extensions not *as* important as on windows.

- EXT4
	- Tracks file metadata inviduallly, similar to NTFS or FAT.
		- Journelling with checksums (log of changes)
		- Inode table (file perms + meta data)

- Inode
	- index that maps files to data blocks, as they are not always stored in sequence, they are tracked wtih block addresses
	- Holds metadata (MACB, size, UID, GID), but differs from MFT
		- Can be used to detect TIME STOMPING

Hardlinks
- every file must have one hard link (location), basically a copy of the file 
- Referneces the inode as does the file
- Deleting additional hardlinks does not delete 

Softlinks
- Points to a hardlink which points to a inode
- Similar to windows shortcut, not a full copy like hardlink

Commands
- Touch filename: create a file or update timestamps. Update access and modification times, Birth time cannot be changed and may represent modification.
- ln : create hard or soft links between two files
	- ex : ln /etc/file /home/paul/file
	- ex: ln -s /etc/file /home/file
- pwd: prints the absolute file path of current location
- cd : cd - last spot
- ls : 
	- -l : list
	- -a : all files
	- - lh : human readable + list
- rmdir -p /yes/pleaes
- rm 
	- rm -r directory : recursively delete
	- rm -rf directory: recursive no prompt
- cp 
	- cp file1 file2
	- cp -r /directory1 /directory2
	- cp file1 file2 file3 directory
	- cp -i file fille : prevent overwriting
	- cp -p : preseve perms and timestamps
- mv - move or rename file / directory
- Remote server files
	- Pull : scp user@server:/home/user/test.txt
	- Push : scp file usr@server:/home/user
	- rsync -a source dest : get large files or retain perms
	- wget address : download from the internet
- cat
	- cat part1 : print file to screen
	- cat part1 part2 part3 : print multiple files
- head 
	- head file - view first 10 lines
	- head -4 file : view first 4 lines
	- head -c4 file : view first n bytes
- tail
	- ""
	- fail -f /var/log/aparch2/access.log : running updates as lines are added
- file
	- file filename : looks at the magic bytes of a file to determine it's file type
- less : prints a vertain amount of lines at a time, pressing return sends more lines
- more: better version of less
- echo string : echos the string to either console or file
- history : entire command history (history x for last x)
	- !n : runs the nth command from history
	- Ctrl+R : page trhough search results
	- CTRL+R == search string : search history from string
	- **adding a space prior to command will prevent command from going into history**

Special characters
These include ..
	* ! # < > | " ' $ \ = [ ] ; ( ) * ? ~ &
	- Using these charcters unescaped may result in bash not performing as intended
- Escape with backslash
	- prevents other characters special meaning
- wrap in single quotes

	- Ex: echo $path - $ is repalced with contents
		- echo \$path - interpreted as $path (variable)

Command operations (;)
semicolpon allows for multiple commands on a line
- Interepted left to right, first does not rely on second
	- Ex: echo hello; echol world

Command operators (&)
ampersand allows for multiple commands on a line
- Execued both at the same time, second does not rely on first
	- starts as background jobs, first to return prints firs
	- ex: ls -la /bin/ & cat /etc/password

Command operators (&&)
allows for multiple commands, exeuctes first then second
- First must execute successfully to run the second
	- some commands don't give the expected exit codes
	- ex: cat idontexist && echo neversee

Pipe ( | )
Allows you to redirect output to command
- ex : ls /etc/ | tail 4
- ex: ip a show dev ens33 | grep inet | head -l | cut =d/ -f1 | awk '{print $2}'

Double pipe ( || )
a logical or operator
- Executes first and then second if first is successful
- ex: echo hello || echo neverseen

Bang bang (!!)
repeat the last command
	- Add sudo to run as root
	- !xxx : repeat previous that starts with xxx

Redirection ( > )
redirects outputs into other commands, overrides what was there before
	- Ex: echo textintofile > file.txt
- Can redirect stderr to the void via ...
	- ex: cat idontexist 2> /dev/null : removes no such file error

Redirection + append (>>)
appeands to an existing or new file
	- ex: echo text >> file.txt

You can also redirect the opposite way by using (< , <<, <<<)
	Standard in on the left and standard out to the right


Related
[[Linux Filesystem]]

