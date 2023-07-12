Bios -> bootloader -> kernel -> init - > login prompt

**Init system**
Critical component, first process started by kernel (ID 1)
	Parent process for all system daemons, and takes the system from kernel to a usable OS

SysV init
Legacy init system, still found on old and small distros
	Utilises a series of scripts to only start and stop a system
		Levels 1 -5, each level adding functionality
	Sequential, and slow to start, fragile to update

**SystemD**
Most common init, has a cmpatibility layer between kernel and userland, and handles multithreading
	Goal to standardise components across distrios
	May be bloated and unstable (uptime), but makes admin easier
Provides a robust aemon management layer
	Hook into processes, watch for events, run jobs at intervals, perform logging, and more
	Replaces run levels with targets
Utilsies .target files
	Describe dependencies and servides required by target
	forms and editable dependency chain
	found in /usr/bin/systemd-< folder >
