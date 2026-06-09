## Linux Environment Variables & PATH Configuration

- **_What are environment variables:_**
  - Key-value pairs : store system and user configuration
  - Available to all programs : Running in your session
  - Common examples : Home, User, Shell, Path
  - View all variables : env or printenv command : View specific variable _echo $VARIABLE_NAME_
  - Case-sensitive : PATH!=path

- **_IMPORTANT SYSTEM ENVIRONMENT VARIABLE_**
  - HOME : your home directiry path (/home/username)
  - USER : Your current username
  - PATH : Directories to search for commands
  - SHELL : Your default shell (/bin/bash)
  - PWD : Present working directory (Current location)
  - LANG : System language and locale settings

- **_SETTING ENVIRONMENT VARIABLES_**
  - Set temporary variable VARIABLE=value (Current shell only)
  - Export for subprocess : export VARIABLE=value
  - View variable value : echo $VARIABLE
  - Unset variable : unset VARIABLE
  - Make permanent : Add to ~/.bashrc or ~/.profile
  - Reload config : source ~/ .bashrc

- **_Understanding the path variable_**
  - PATH contains directories separated by colons (:)
  - Linux search left to right for executable commands
  - View PATH : echo $PATH
  - EXAMPLE : /usr/local/bin:/usr/bin:/bin
  - When you type "ls" : linux check each path directory
  - First match wins : order matters.

- **_Modifying the path variable_**
  - Temporarily add : _export PATH=$PATH:/new/directory_
  - Add to beginning export PATH = /new/directory:$PATH
  - Permanently add Edit ~/.bashrc
  - Example : export PATH=$PATH:$HOME/bin
  - Check if command found : which command

- Shell configuration files
  - ~/ .bashrc : user-specific bash settings (recommended)
  - ~/ .bash_profile : Login shell configuration
  - ~/ .profile : Generic shell profile (sh compatible)
  - /etc/environment : System-wide variables (all users)
  - /etc/profile : System-wide shell settings

- Difference : bashrc for interactive, profile for login shells

---

## Linux Process Monitoring: top, ps, df Commands | System Resources & Log Management for devops

- Understanding Linux Processes :
  - Process : Running instance of a program
  - PID : Every process has a PID (Process ID) - unique number
  - Hierarchy : Parent and child processes - hierarchical structure
  - Process States : Running , Sleeping, Stopped, Zombie
- Process Types :
  - Foreground vs Background processes
  - Init/Systemd (PID 1) : First process, parent of all

- Viewing Processes with PS COMMAND
  - ps : show process in current terminal (Process Status)
  - ps aux : show all process with details (A = All user, U = User oriented Format, X = Include Not terminal)
  - ps -ef : Alternative format, shows parent PIDS
  - ps aux | grep process name
  - key columns : PID, USER, %CPU, %MEM, COMMAND
  - Common usage : Ps aux | grep nginx

- Interactive process monitoring with TOP
  - Real-time Process Viewer : Interactive and continuously updating process information
  - Updates Every 3 Seconds
  - key System Metrics : Display CPU, memory, uptime, and load.
  - Shot by CPU : Press Shift + P
  - Shot by Memory Press Shift + M
  - Kill process Press k, enter PID
  - Exit, Press q
  - Managing processes - Signals
    - Kill PID : Terminate process (Sigterm)
    - Kill - PID : Force Kill (Sigkill)

- Managing processes - Signals
  - Kill PID : Terminate process (Sigterm)
  - Kill - PID : Force Kill (Sigkill)
  - Killall processname : Kill al instance by name
  - pkill pattern : Kill by pattern maching
  - Commmon signals : SIGTERM (15), SIGKILL (9), SIGHUP (1)
  - View Signals: Kill -l

- Background and Foreground jobs
  - Command & : Run in background . e.x. : touch file{1..3}.txt & mkdir folder
  - Ctrl + Z : Suspend current foreground process
  - bg : Resume suspended process in background
  - fg : Bring background process to foreground.
  - jobs : List in background jobs
  - nohup command & : Run immune to hangups

- System Resources Monitoring:
  - free -h : Memory usage (human-readable)
  - df -h : Disk space usage
  - du -sh directory : Directory size
  - uptime : System uptime and load average
  - vmstat : Virtual memory statistics
  - iostat : CPU and I/O statistics (install sysstat)
