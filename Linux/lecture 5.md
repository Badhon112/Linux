## Master Linux Package Management: DNF Commands

- **_What are package managers_**
  - Package manager : Tool to install, update remove software
  - Handles dependencies : Automatically
  - Package : pre-compiled software with metadata
  - Different distro, different managers : DNF (CentOS/RHEL), APT (Debain/Ubuntu)
  - Safer than manual compilation : tested, verified packages

- **_DNF - Centos Package manager_**
  - DNF = Dandified YUM : Modern package manager for CentOS 10
  - sudo dnf install package : install software
  - sudo dnf remove package : Uninstall software
  - sudo dnf update : Update all packages
  - sudo dnf search keyword : Find packages
  - dnf list installed : Show installed packages

- **_Managing Repositories_** :
  - Repositories : Sources where packages are stored.
  - dnf repolist : Show enabled repositories
  - Repository config : /etc/yum.repos.d/
  - Enable/disable repos : dnf config-manager
  - EPEL Repository : Extra packages for Enterprise Linux
  - Enable EPEL : Sudo dnf install epel-release

- **_Package information and queries_**:
  - _dnf info package_ : Show package details
  - _dnf list available_ : List all available packages
  - _dnf list updates_ : Show packages with updates
  - _dnf provides filename_ : Find which package provides a file
  - _dnf history_ : View installation history
  - _dnf history undo ID_ : Rollback transaction

- **_Package Groups_**
  - Package groups : Collections of related packages
  - dnf grouplist : show available groups
  - sudo dnf grouninstall "Group Name" : install entire group
  - Example groups : "Development Tools", "System Tools"
  - Faster then individualinstalls : For multiple packages
  - sudo dnf groupremove "Group Name " : Remove group

---

## Linux Services, Systemd & Cron

- **_Understanding Systemd_**
  - Systemd : Modern init system and service manager
  - PID 1 First process started at boot
  - Management : Manages services, sockets , devices, mounts
  - Replaces OLD SysV init scripts
  - Parallel service startup - faster boot times
  - systemctl : main command to control systemd

- **_Basic service Management_**
  - sudo systemctl start service : Start service now
  - sudo systemctl stop service : Stop service
  - sudo systemctl restart service : Restart service
  - sudo systemctl reload service : Reload config without restart
  - systemctl status service : check service status

- Enabling Services at Boot
  - sudo systemctl enable service : Start at boot
  - sudo systemctl disable service : Don't start at boot
  - systemctl is-enabled service : Check if enabled
  - sudo systemctl enable --now service : Enable and start immediately
  - Enabled != Running - Different states
  - systemctl list-unit-files : Show all services and states

- Checking Service Logs
  - journalctl -u service : view service logs
  - journalctl -u service -f : Follow logs in real-time
  - journalctl -u service --since today : Today's logs only
  - journalctl -u service -n 50 - Last : 50 Lines
  - journalctl -xe - Recent errors with explanations
  - logs stored in :/var/log/journal

- Viewing File Contents
  - cat filename : Display entire file
  - head -n 10 file : First 10 lines (default 10 )
  - tail -n 20 file: Last 20 lines
  - tail -f file : Follow file in real-time (logs)
  - lass filename : Paginated viewer (space/arrows to navigate)
  - more filename : Simple paginated views

- Understanding pipes:
  - Pipe symbol : | = connects commands
  - Output of first = input of second
  - Example : cat file.txt | grep error
  - Chine multiple pipes : For complex processing
  - Filters data : as it flows through pipeline
  - More efficient : than intermediate files
