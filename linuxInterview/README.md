1. What is Linux, and How Is it Different From Unix ?

- Linux and Unix, Both Strong Operating Systems Designed for Different Purposes and Audience.
- _Linux_ :
  - Free and Open-Sources, Use by personal computer, to server even mobile Phone
  - Open Source and Accessible to EveryOne
  - Perfect for Personal and Professional Use
- _UNIX_ :
  - Proprietary System, Enterprise Environment, Not open-sources, Need License to use it Updates Tend to be Slower
  - Unix is More Exclusive
  - Used in Large Organizations
  - For Stability and Dedicated Support

2.  Linux kernel :

- linux Kernel is the brain of the Linux Operating System
- Its manage key like CPU, Memory.
- Running Multiple Programs at once
- Organization Files and Storage
- Managing Network Communication
- _Hardware Abstractions_:
  - Software doesn't need to know the details of your hardware. That make kernel Flexible and Efficient
- You can add Extra Features:
  - Device Drivers, Network Protocols
- _Customizable_:
  - Personal Use
  - Powering Servers

3.  What is a Shell in Linux, and how Is it Different From Bash ?

- _Shell_
  - Basically a Command-Line Interface That Lets you Interact With the Operating System.
  - Shell is a General Term for any Command-Line Interface
  - Basically it is a bridge between you and kernel.
  - Scripting, Command History, Job Control. popular Shells in linux :
    - _Bash(Bourne Again Shell)_: Bash Is a Specific Type of Shell with Advanced Features.
      - Better Scripting Tools
      - Command-Line Editing
      - Support for Arrays and Functions
    - Zsh
    - Fish.

4. What Are the basic Components of a Linux OS ?

- Linux operating System Is Built on Five Key Components, Kernel, System Library,
- _kernel_
  - Memory Management
  - Process Scheduling
  - Device Communication
- _System Library_
  - System Library that provides function to allow application to access the kernel feature
- _System Utility_
  - File Management
  - System Monitoring
  - Configuration
- _BootLoader_
  - It initialization the system by loading the kernel into memory at startup enabling bootUp. Meaning, It is essential for enable the system boot up.
- _Application Software_

5. What is the init Process in Linux?
   - _Init Process_ : Init is the very First Process the Kernel starts. Init Process ID (PID) is 1
   - Init has been Replaced by systemd

6. How do you find files in Linux?
   - find [path] [options] [expression]
   - Path : Starting point (e.g., /home/user)
   - Options : File type (-type f) or directory (-type d)
   - Expression: Conditions like -name "\*.txt" or -size +1M

7. What is the different between soft link and hard link and File Permission ?
   - Soft Link ( Symbolic Link)
     - A pointer to the original File
     - Can link across different file system
     - Deleting the original file breaks the link
     - ln -s target link_name
     - require additional inode for the link

   - Hard Link
     - A Direct reference to the File's data on disk
     - Must obe on the same file system
     - File remains accessible until all the hards link are deleted
     - ln target link_name
     - Share the same inode with the original file

   - File Permission
     - chmod 777 file_name
