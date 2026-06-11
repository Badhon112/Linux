# Linux Internals & Networking

- **What is the Linux Kernel?**
  - Linux kernel is the brain that connect hardware to application. It is act as a brain / or bridge between hardware and application.

- **Explain the Boot process: BIOS -> MBR -> GRUB -> Kernel -> Init.**
  - It is actually initial process of the system running.
  - _BIOS_ : When the computer power on . The first code execute when we turn on the computer from the motherboard firmware.
  - _MBR(Master Boot Record)_ : The MBR is a specific 512 byte sector located at the very beginning of the bootAble drive.
  - GRUB : The actual Boot Loader
  - _Kernel_ : The kernel is the core heart of the operating system and now takes complete control of the machine.
  - _Init_ : The init program is the parents of all processes on the system, and the PID is 1

- **What is the difference between /etc and /var directories**
  - /ect : Etc holds the system configuration file like nginx.
  - /var: var content variable or changing data (Database) generated during the system operation. That is actively changed.

- **How do you check the running processes in Linux (top/htop/ps)**
  - ps (Process Status) : it check all the Process that are running
  - top : It display the server resources sharing
  - htop : it is update version of top. It display more visualize then top.

- **What is a ”Zombie Process”? How to kill it?**
  - Zombie process is a dead child process that remain in the OS process table. After Killing it . Like its running on background

- **Explain the difference between ’su’ and ’sudo’.**
  - _su_ : substitue/switch user logs you completely into another user account, while (super user do) temporarily runs a specific command with administrative permissions

- **How to view the last 100 lines of a log file continuously**
  - tail -n 100 -f file.txt

- **Explain ’grep’, ’sed’, and ’awk’ with one-liner examples.**
  - _grep_ : grep scans inputs line-by-line and prints only the lines that meet a specific text pattern or regular expression. e.x. : grep "error" /var/log/syslog

- **How do you find files modified in the last 24 hours?**
  - find /path/to/search -type f -mtime -1

- **What is the difference between a shell and a terminal?**
  - A terminal a graphical interface or windows where you type commands. and a shell is the underlying program that reads your command, translate them, and executes them.

- To check open port on a server :
  - _ss -tuln_
  - _netstat -tuln_
  - _-t_ : Display TCP ports
  - _-u_ : Display UDP ports
  - _-l_ : Filter for listening sockets only
  - _-n_ : show numerical port numbers

- **What is the purpose of /etc/hosts file?**
  - The /etc/hosts file is a plain text system file used by your OS to map hostname to iP address
