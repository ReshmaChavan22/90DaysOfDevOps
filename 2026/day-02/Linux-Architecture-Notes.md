# Day 02 – Linux Architecture, Processes, and systemd

## 1. Linux Architecture
Linux can be understood as different layers working together:
+-----------------------------+
|      User Applications      |
+-----------------------------+
|        User Space           |
| Shell, Commands, Programs   |
+-----------------------------+
|        System Calls         |
+-----------------------------+
|           Kernel            |
| CPU | Memory | Files | I/O  |
| Processes | Networking      |
+-----------------------------+
|          Hardware           |
+-----------------------------+

### Kernel
The kernel is the core of the Linux operating system.
It communicates directly with hardware.
It manages: CPU, Memory, Processes, Filesystems, Networking, Devices
Applications normally interact with the kernel through system calls.

### User Space
User space is where normal applications and commands run.
Examples: bash, ssh, vim, python, nginx
Applications do not directly control hardware; they request services from the kernel.

### Init / systemd
When Linux boots, the kernel starts the first userspace process.
On most modern Linux distributions, this process is systemd.
systemd manages services, startup processes, dependencies, and system state.

## 2. Processes
A process is a running instance of a program.
For example:

python app.py

The program is the code, while the running python app.py is a process.
Every process has a PID (Process ID).

Example:

ps

may show:
PID   TTY      TIME     CMD
1234  pts/0    00:00    bash

Here 1234 is the process ID.

Parent and Child Processes
Processes can create other processes.
Parent Process
      |
      +---- Child Process
                |
                +---- Another Child

The process that creates another process is called its parent process.
The PPID represents the Parent Process ID.

## 3. Process States
Linux processes can exist in different states.
Running (R): Process is currently running or ready to run on the CPU.
Sleeping (S): Process is waiting for an event or resource. This is normal for many processes.
Uninterruptible Sleep (D): Process is usually waiting for I/O. It generally cannot be interrupted immediately. A large number of D state processes can indicate an I/O problem.
Stopped (T): Process execution has been stopped. It can usually be resumed later.
Zombie (Z): The process has finished execution. However, its parent has not yet collected its exit status.
A zombie does not actively use CPU, but it remains in the process table.

Check process states with:
ps aux

## 4. systemd
systemd is the system and service manager commonly used by modern Linux distributions.
It is responsible for starting and managing services after boot.

Examples of services:

SSH
Docker
Nginx
Cron
Networking services
Common systemd commands
Check service status:
systemctl status nginx

Start a service: sudo systemctl start nginx

Stop a service: sudo systemctl stop nginx

Restart a service: sudo systemctl restart nginx

Enable a service at boot: sudo systemctl enable nginx

Disable a service at boot: sudo systemctl disable nginx

Why systemd is important for DevOps
During production troubleshooting, systemd helps us:
Check whether a service is running.
Start or stop services.
Restart failed services.
Configure services to start automatically.
Investigate service failures.
For example: systemctl status nginx
can quickly tell us whether Nginx is running and provide useful failure information.


## 5. Five Linux Commands I Would Use Daily
1. ps: Used to view running processes.Useful for finding process IDs and checking process states. ps aux
2. top: Used for real-time CPU and memory monitoring. Useful when troubleshooting high CPU or memory usage.
3. systemctl: Used to manage systemd services. systemctl status nginx
4. journalctl: Used to view systemd/service logs. Useful for troubleshooting service failures 
journalctl -u nginx
5. df: Used to check filesystem disk usage. Useful for identifying disks that are running out of space.
df -h


## 6. DevOps Troubleshooting Flow
When a Linux service is not working, I can follow this basic flow:
Service Problem
      |
      v
systemctl status <service>
      |
      v
Check logs
journalctl -u <service>
      |
      v
Check processes
ps aux / top
      |
      v
Check resources
CPU / Memory / Disk
      |
      v
Fix the problem
      |
      v
Restart service
systemctl restart <service>

Key Takeaways
The kernel manages hardware and core system resources.
User space contains applications and commands.
A process is a running instance of a program.
Every process has a PID.
Processes can be running, sleeping, stopped, or zombie.
systemd manages services and system startup.
ps, top, systemctl, journalctl, and df are useful everyday DevOps commands.
Understanding processes and systemd is important for troubleshooting production Linux systems.
