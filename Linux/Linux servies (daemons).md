**Daemons**
Designed as a background process
	Equiv to windows services
	Startd by init system PID1

**Find Daemons - SysV**
- ls /etc/init.d/rc - view startup daemons
- service --status-all - view running daemons
- ps aux - check process for ParentPID of 1

**Control Daemons - SysV**
- service < name > < start | stop | restart | status >
- Daemons typically end in D
	- SSH daemon is SSHD
****

**Find daemons - SystemD**
- systemctl list-unit-files --state=enabled : view start upddaemons
- systemctl -l --type=service --all : view all daemons
- systemctl < command > < name > : run the command with the demon name
	- start, stop, enable, disable, restart, status
- SystemD provides a SysV like service command
	- Translates the old format to the new for compatability
	- 
****
Common
- cron /anacron : starts processes at set schedules (good backdoors for forsenic artifacts)
- Syslog : provides logging for services
- inetd : listens on ports nad starts services
- udev - detects attached hardware
- portmap - rpc endpoints
- sshd : allows inbound sh connections
- httpd - apaache
