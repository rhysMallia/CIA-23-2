Program in the act of execution, uses ELF (executable and linkable format, instead of .exe)

All processes are assigned a process ID (PID)
	The process that started it is refered to the PPID (parent process id)
	PID1 always the init system with every other service a child of this

**View processes**
- ps aux , ps -elf : view every process currently running
- ps -lfu < user name > : view processes started by a user
	- processes in square brackets are internal kernel processes and can be ignored
- pstree : view processes as a tree
- top , htop : view processes by CPU resource usage
- 

**start processes**
Start by typing the executable name
- ./insamedir
- ../../usr/bin/lscpu
- /usr/bin/lscpu
Unlike windows, the path must be provided, either absolutely or relatively
	if none are proided, the $PATH variable will be used
	ex; echo $PATH


**Kill processes**
- kill < pid> - kill gracefully (TERM signal)
- kill -9 < pid > - force kill (SIGKILL signal)
	- can have unintended consequences

**Standard file stream**
unidirectional interfaces that exist for every process
standard in : keyboard 
standard out : text file
stanard err : 