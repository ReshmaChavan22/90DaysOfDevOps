# Linux Commands Cheat Sheet

## Process Management
Command: Usage
- 'ps aux' -	Display all running processes with detailed information.
- 'top' -	Monitor running processes and system resource usage in real time.
- 'htop' -	Interactive and user-friendly process monitoring.
- 'pgrep <name>' -	Find the process ID of a process by name.
- 'kill <PID>' -	Send a signal to a process using its process ID.
- 'pkill <name>' -	Terminate processes by their name.
- 'jobs' -	Display jobs running in the current shell.
- 'bg' -	Resume a stopped job in the background.
- 'fg' -	Bring a background job to the foreground.
- 'systemctl status <service>' -	Check the current status of a system service.


## File System
Command:	Usage
- 'pwd' -	Display the current working directory.
- 'ls -la' -	List all files, including hidden files, with detailed information.
- 'cd <directory>' -	Change the current working directory.
- 'mkdir <directory>' -	Create a new directory.
- 'touch <file>' -	Create an empty file or update its timestamp.
- 'cp <source> <destination>' -	Copy files or directories.
- 'mv <source> <destination>' -	Move or rename files and directories.
- 'rm <file>' -	Remove a file.
- 'find <path> -name <name>' - Search for files and directories by name.
- 'du -sh <directory>' -	Display the total disk usage of a directory.

## Networking Troubleshooting
Command	Usage
ping <host>	Test network connectivity to a host.
ip addr	Display network interfaces and IP addresses.
ip route	Display the system's routing table.
curl <URL>	Make HTTP requests and test web endpoints.
dig <domain>	Query DNS records for a domain.
ss -tuln	Display listening TCP and UDP network ports.
traceroute <host>	Trace the network path to a remote host.
hostname -I	Display the system's assigned IP addresses.

## Log and System Troubleshooting
Command	Usage
journalctl	View logs collected by the systemd journal.
journalctl -u <service>	View logs for a specific systemd service.
dmesg	Display messages from the Linux kernel ring buffer.
free -h	Display memory usage in a human-readable format.
df -h	Display filesystem disk space usage.
uptime	Show how long the system has been running and its load average.

## Useful Command Combinations

Find a Running Process
ps aux | grep nginx
Finds processes related to nginx.

Monitor a Log File
tail -f /var/log/syslog
Continuously displays new entries added to a log file.

Check Disk Usage
df -h
Shows available and used disk space in a human-readable format.

Check Listening Ports
ss -tuln
Displays services currently listening for network connections.

Test an HTTP Endpoint
curl -I https://example.com
Fetches HTTP headers to quickly check whether a web endpoint is responding.
