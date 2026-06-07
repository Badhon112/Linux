## Linux File System & Directory Structure

- **_Linux file system - The Big Picture_**
  - Everything starts from root (/) (Single Forward Slash) - the top of the tree
  - No C: or D: drivers like Windows
  - Single unified directory tree
  - Everything is a file in linux (even hardware)
  - Case-sensitive : File.txt != file.txt
  - Uses forward slash (/) not backslash (\)

- **_The Root Directory (/) and key folders_**
  - **/ (root)** : Top-level directory, everything starts here
  - **/home**: User personal Directories (/home/username)
  - **/root** : Home Directory for root user (superuser)
  - **/bin** : Essential command binaries (ls, cp, mv)
  - **/sbin** : System binaries (for Administrators)
  - **/usr (Unique System Resources)** : User programs and data

- **_Configuration, Logs, and Temporary Files_**
  - **/etc** : Configuration files for system and application. So every configuration file for your system and install are going to lived here. like web server /etc/nginx/html
  - **/var (Variable)** : Variable data (logs, Databases, websites)
    - _/var/logs_ : System and application log files
  - **/tmp** : Temporary files (cleared on reboot)
  - **/opt** : Optional third-party software
  - **/proc** : Virtual directory with system information

- **_Device and Boot Directories_**
  - **/dev** : Device files (hard disks, USB, terminals)
  - **/media** : Mount point for removable media
  - **/mnt** : mount point for temporary file systems
  - **/boot** : Boot loader files and kernel
  - **/lib** : Shared libraries (like DLLs in Windows)

- **_Absolute VS Relative Paths_**
  - **Absolute Path** : Starts from root (/) -e.g., /home/badhon/documents
  - **Relative Path** : Starts from current location - e.g. , documents/file.txt
  - **.(dot)** : Current Directory
    - E.x.: You are in /home/badhon. Now when we run sh ./shell.sh . linux will auto locate /home/badhon/shell.sh .
  - **..(dot dot)** : Parent Directory
    - E.x.: You are in /home/badhon. Now when we run sh ../shell.sh . linux will auto locate /home/shell.sh .
  - **~(Tilda)** : Your home directory shortcut

- **_Lab_**
  - _*hostname -I*_ : It will give the Ip where the vm is running.
  - _*pwd*_ : Show current directory path
- _*cd /path*_ : Change to specific directory
- _*cd ~*_ : Go to home directory
- _*cd ..*_ : Go to one level
- _*ls*_ : List files in current directory
- _*ls -la*_ : List all files with details (including hidden)
- _*tree*_ : Visual directory structure (may need to install)
