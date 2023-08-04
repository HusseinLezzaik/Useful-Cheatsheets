## Terminal
```
$ exit 
$ clear
$ whoami // returns user name
$ history 
$ ctrl + a // cursor at beginning
$ ctrl + e // cursor at end
$ ctrl + c // kill process
$ ctrl + x // 
$ ctrl + D // close shell
$ ctrl + R // reverse search command
$ ctrl + alt + t // to access the terminal right away
```

## Manual
```
$ man <command> // shows you manual page for a commmand
$ man bash // starts with command section 1 
$ man 3 printf // library function section
$ man 2 write // system call section
```

## Make Directory
```
$ mkdir -p make/new/directory
$ mkcd <directory_name> // create directory and cd into it
$ mv file1.txt file2.txt
```

## CTAGS
```
$ man ctags // manual of ctags, most unix text editors know how to use tags
$ ctags * // generates file "tags" that has 3 columns: a tag, filename, and RegEx
```

## Sed
-  is a command-line utility for Unix-like operating systems that allows you to perform text transformations on a file or stream of text data.

## Change Directory
```
$ cd // take me home
$ cd .. // (..) means parent directory
$ cd ~ // take me home
$ cd - // go back to previous directory
$ cd !$ // !$ alias for arguement of last command
$ cd ~/opt // from home
$ cd /opt // from absolute root
$ cd opt // from current directory
$ cd $GCMLEAF
$ cd /altstore // This works because cd has a search path, CDPATH, which contains your $HOME
$ help cd
```

## Copy
- `SCP` means secure copy from machine to another
```
$ cp -r file1.txt file2.txt
$ cp -r ~/catkin_ws/src/* ~/catkin_ws_kris/src/. // copy everything inside /src from one directory into another
$ scp -r ubuntu@10.10.10.1:~/catkin_ws/src/directory . // copying from one Remote Machine to another (Jetson)
```

## which
```
$ which bash // finds location of interpreter
$ which <command> | less
```

## file
```
$ file .filename // tells us it's type, like for example its a wave file
$ file <file_name.type> // prints type of the file/documents
```

## locate
```
$ locate <program_name> // tells you location of program, if any
$ locate <command> or locate <filename> // tells us where things are, using a database
```

## cat
```
$ cat README.md // displays the contents of a text file you created previously, works with yaml files as well
$ cat >> file2 // anything that cat comes up with, stick it in this file, append text to a file
$ cat hello.txt // prints content of a text file
$ cat < hello.txt
$ cat < hello.txt > hello2.txt // puts hello into hello2.txt, think of it as another way to do "cp" command
$ cat hello2.txt // prints hello
$ cat < hello.txt >> hello2.txt // appends to the file hello2.text a "helo" command
```

## watch
```
$ watch free -h // watch runs command every 2 seconds
```

## whatis
```
$ whatis <command>
$ whatis sh
$ whatis ls
$ whatis whatis
```

## source
```
$ source /.bashrc
$ source mcd.sh // will run this program in our shell and load it, even though it didn't print anything
$ source ./devel/setup.bash // for ROS in new terminal
```

## Touch
```
$ touch foobar.txt // creates text file
$ touch {foo,bar}/{a..h} // this creates files foo/a, foo/b, .., foo/h, bar/a, bar/b, ...
$ touch foo/x bar/y
```

## Path
```
$ pwd // print working directory
```

## Link
```
$ ln -s CTAGS .tags 
```

## find
```
$ find . -name "FAIL" // looks for files/folders with FAIL, can also use regex 
$ find . -name *.area // find something
```

## Remove
```
$ rm -rf 0* // remove all directories starting with 0
$ rm -rf *.out // remove all directories ending with .out
$ rm -rf * -R // delete everything in this directory
$ rm -rf <directory_name> // deletes a directory
```

## ls
```
$ ls // List what's in the current directory
$ ls -a // List what's in the current directory with hiden files
$ ls -all // List what's in the current directory and all hidden files
$ ls -l // list what's in the current directory with their properties
$ ls -la // with permission
$ ls *.c
$ ls a*: List what's in the current directory that starts with a
$ ls *.md: List what's in the current directory that ends with .md
$ ls -l / | tail -n1 // the tail command can specify which line we want to print on our screen
$ ls /bin // lists a bunch of important unix utilities
```

## bashrc
- calls everytime the terminal opens
```
$ sudo nano .bashrc # to edit the bashrc from the terminal directly
```

## Alliases
```
$ alias // prints all aliases we have in our system
$ alias ll="ls -l --color=auto"
$ alias ..="cd .."
$ alias ...="cd ../.."
$ alias ....="cd ../../.."
$ alias .....="cd ../../../.."
$ alias ......="cd ../../../../.."
$ alias .......="cd ../../../../../.."
```

## rsync
```
- tool to move stuff fast b/w local and another machine, useful for backup
$ rsync -avr <source_directory> <target_directory> 
```

## grep
```
$ grep -r SEARCHWORD // will look for SEARCHWORD in root directory and below
$ grep something foo.txt // search for "something" inside file called foo.txt
$ grep -i "thread" * -R | less // -i: Prints lines with matching criteria while ignores casing (Upper/Lowecase).
$ grep C850 trip.in | less
$ rostopic list | grep slam // use "grep" to find strings only with a specific name
```

## less
```
$ less <script>
$ less + "/" // search for a pattern which will take you to the next occurrence.
$ less + "?" //
$ n // for next match in forward
$ N // for previous match in backward
$ SPACE // Navigate Forward One Window
$ b // Navigate Backward One Window
$ ENTER // navigate forward one line
$ k // navigate backward one line
$ q // exit the less pager
$ g // go to start of file
$ G // go to end of file
```

## more
```
$ more parameterized.txt // displays the text inside the text file, useful for big log texts to display page by page
$ more hello.txt // prints context of a text file
```

## jobs
```
$ jobs // list jobs
$ %1 // puts job in frontground
$ ctrl + c // kill job
```

## Memory and CPU
```
$ free // info about memory and processors av/used
$ free -h // human readable-format
$ free -g // rough estimate in gigabytes
$ less proc/cpuinfo // more info
$ df 
$ df -a // for all fs disk space usage
$ df -h // human readable
$ tail -f syslog
$ top // to take a look at Memory usage
$ gnome-system-monitor //  To check out different packages and performances
```

## diff
```
$ diff <file1.txt> <file2.txt>
$ diff file1.txt file2.txt > output.txt // prints difference into output.txt
$ diff <(ls foo) <(ls bar) // show differences between files in foo and bar
```

## umask
```
- umask changes the default permissions, compared to chmod
$ umask # should be 027
$ umask // display current value (as octal)
$ umask -S // display current value symbolically
$ umask 007 // set the mast to 007
```

## Executable Permissions
- There's 3 permissions: read, write, execute for 3 users: super, normal, and guest.
- 7 = 111 hence 777
- To list scripts wiht permissions run: ` $ ls -l `
```
- user (rwx) | group (rwx) | everyone (rwx)
        421           421              421
	 7 bits	  	7 bits 		7 bits
$ chmod +x test.sh // make file executable for anyone
$ chmod 700 // i am the only person that can do anything with this file
$ chmod 744 // anyone can read
$ chmod 644 file1  // for modules
$ chmod 755 file1 // for directories
```
- Examples
```
$ sudo chmod 777 odrive.py
```

## Pushd and Popd
```
$ pushd . 
$ popd 
```

## Glob
- The * is a glob: if you do ls /opt/alt/althome/*anchor/Bashrc
```
$ ls *.c
$ rm -rf 00* *.out
```

## Process Status | ps
- Process Attributes: processID, parentID, UMask (permissions), environment
```
$ man ps
$ ps aux // will show a list of all processes running on the system
$ ps # display the processes running in the current shell
$ ps -A # display all the currently running processes
$ ps -T # display all the processes associated with the current terminal
$ ps -u UserName # display all the processes associated with a particular user
```

## Input
```
$ echo ""What is your name?"
$ read name
$ echo "Good Morning $name!!"
$ sleep 1
$ echo "You're looking good today $name!!"
$ sleep 1
```

## tar
```
$ tar xvzf file.tar // extracting files from Archive using option -xvf
$ tar cvf file.tar *.c // creating an uncompressed tar Archive using option -cvf
```

## nohup
- No Hang Up, runs the process even after logging out from the shell/terminal
```
$ nohup bash geekfile.sh
$ nohup bash geekfile.sh > output.txt
```

## ssh
- to ssh into a computer, you must be both connected onto the same network
- public/private keys
```
$ ssh-keygen -t rsa # generate public/private  key
$ cd .ssh
$ ll
```

## Pdf
```
$ evince file_name.pdf // To start the Document Viewer from the command line
```

## Time
```
$ date +%s // prints the absolute date time in seconds, which is how much time has passed since the beginning of the year
$ sudo timedatectl set-timezone America/New_York // change the systems timezone to America/New_York
```
## echo
```
$ echo $PATH // will print all paths that are avaiable that your program bash will use to execute commands
$ echo <arguement> // a program that returns the arguements written with it
$ echo hello > hello.txt // Using notion of streams, using input/output streams
$ echo $foo // prints bar
$ echo "Hello" 
$ echo 'World' // equivalent to above
$ echo "Value is $foo" // Prints Value is bar
$ echo 'Value is $foo' // Value is $foo
```

## firefox
```
$ firefox reasons.html // open html file in firefox 
```

## lynx
```
$ lynx www.ibsplc.com/careers // displays browser content inside terminal
```

## curl
- Curl is a computer software project providing a library and command-line tool for transferring data using various network protocols.
- Linux curl command is used to download or upload data to a server via supported protocols such as HTTP, FTP, IMAP, SFTP, TFTP, IMAP, POP3, SCP, etc. 
- The name stands for "Client URL".
```
$ curl --head --silent google.com | grep --ignore-case content-length | | cut --delimiter=' ' -f2219
```

## wget
```
$ wget url_link_address // downloads content from online
```

## export
- Export is a command used in the bash shell to make use of variables and functions that are to be passed on further to all child processes.

## Environment Variables
```
$ printenv // Display the environment variables
$ foo=bar // Assiging a new variable, spaces are very sensitive here
```

## uname
- The uname command is used to print basic info. 
```
$ uname -a # prints kernel version
```

## USB
- to check if camera is connected:
```
$ ls /dev/video0
```
- to check the authority of rplidar's serial-port:
```
$ ls -l /dev | grep ttyUSB 
```

## Reboot
```
$ sudo shutdown -h now
$ sudo reboot : reboot immediately
```

## Network
- to reset network, run these commands:
```
$ service networking restart // restart the local network interfaces
$ systemctl restart network-manager // resets the wifi
```

## SystemD
- Commands:
```
$ systemctl start <example.service>
$ systemctl stop <example.service>
$ systemctl enable <example.service> // run at startup
$ systemctl disable <example.service> // run at startup
$ systemctl daemon-reload // Reset all of the service files
```

- To edit SystemD in Linux:
```
$ cd /etc/systemd/system 
```

## gedit
```
$ gedit random_driver.cpp 
```

## Application Package Manager | apt
- `apt` is a command-line utility for installing, updating, removing, and otherwise managing deb packages on Ubuntu, Debian, and related Linux distributions
- `apt` is used for managing all packages and dependencies in the terminal for ubuntu
- Updating and Upgrading packages | `apt update && upgrade`
```
$ apt update // The apt package index is basically a database that holds records of available packages from the repositories enabled in your system
$ apt upgrade // To upgrade the installed packages to their latest versions
$ apt full-upgrade // The difference between upgrade and full-upgrade is that the later will remove the installed packages if that is needed to upgrade the whole system.
$ apt-get update && apt-get upgrade // update and upgrade code dependencies
```
- Installing packages | `apt install`
```
$ apt install <package>
$ apt install <package1> <package2>
$ apt install /full/path/file.deb // to install local deb files provide the full path to file
```
- Removing packages | `apt remove`
```
$ apt remove <package> // The remove command will uninstall the given packages, but it may leave some configuration files behind.
$ apt remove <package1> <package2> // To remove multiple installed packages
$ apt purge package_name // If you want to remove the package including all configuration files, use purge instead of remove
$ apt-get purge // to remove a package, instead of using install
```
- Remove unsude packages | `apt autoremove`
```
$ sudo apt autoremove // When the package is removed, the dependencies will stay on the system. This leftover packages are no longer used by anything else and can be removed.
```
- Listing Packages | `apt list`
```
$ apt list // the list command allows you to list the available, installed, and upgradeable packages
$ apt list | grep <package_name> // To find out whether a specific package is installed, you can filter out with the grep command
$ apt list --installed // list only the installed packages type
$ apt list --upgradeable // getting a list of the upgradeable packages may be useful before actually upgrading the packages
```
- Searching Packages | `apt search`
```
$ apt search <package> // this command allows you to search for a given package in the list of the available packages
$ apt search ros-melodic // To find available packages
```
- Package Information | `apt show`
```
$ apt show <package> // To retrieve information about a given package, dependencies/installation size, package source, etc
```

## Systems Performance Monitoring
1) `Top`
- The top command is used to display all the running and active real-time processes in an ordered list and updates it regularly.
- It displays CPU usage, Memory usage, Swap Memory, Cache Size, Buffer Size, Process PID, User, Commands, and much more
```
$ top
```

2) `htop`
- htop command is a Linux utility for displaying crucial information about the system’s processes. It can be considered as a Linux counterpart of Windows Task Manager.
- htop is more of an interactive program as it supports mouse and keyboard operations for switching between values and tabs.
```
$ htop
```

3) Virtual Memory Statistics | `VmStat`
- Linux VmStat command is used to display statistics of virtual memory, kernel threads, disks, system processes, I/O blocks, interrupts, CPU activity, and much more.
```
$ vmstat
```

4) List Open Files | `Lsof`
- The lsof command is used in many Linux/Unix-like systems to display a list of all the open files and the processes. The open files included are disk files, network sockets, pipes, devices, and processes.
- One of the main reasons for using this command is when a disk cannot be unmounted and displays the error that files are being used or opened. With this command, you can easily identify which files are in use.
```
$ lsof
```

5) Network Statistics | `Netstat`
- The netstat is a command-line tool for monitoring incoming and outgoing network packets statistics as well as interface statistics.
- It is a very useful tool for every system administrator to monitor network performance and troubleshoot network-related problems.
```
$ netstat -a | more
$ man ps
$ ps aux
```

## Jounralctl
- It logs all of which that normally shows up when you do a `systemctl status` 
```
$ journalctl -u <your.service> -e
$ journalctl -u <service name>.service -e // This will display the end of a systemd service logs
$ journalctl -u <service name>.service -f // This will follow/tail the systemd service logs
```

## Brew
- A package manager for missing dependencies
```
$ brew install
```

## Notes
- Visual interfaces are limited to what they can do, limited to the keys you have and what are pre-defined. In the terminal you can use command line or text base tools to do those automation. - Command Prompt can be customized.
- `Windows`: Power Shell, `Linux`: Zsh, `Bash` (Born Again Shell) the most famous.
- When you open the terminal, you will have one line at the top known as `Shell Prompt`, which looks like: `user_name@current_machine:current_path$`
- Terminal comes with environment variables that are set whenever you define paths
- `Bash` is a programming language that you can even do things like for loops, while loops, etc
- `Windows` have seperate paths depending on which disks you're using like: `\:d`, whereas `linux/macos` have absolute paths that are fixed
- You can configure the terminal to tell you the whole path of where you are
- If you want to run a program that runs another program, it's better to use `absolute paths` to be able to run it from anywhere
- Most programs take in arguements as `<flags>` or `<options>`, which basically tells you what sort of cool things you can do with a specific command. For example: `ls -- help`, most programs actually have this feature of typing command `-- help`, `-a` is a flag, `-color` is an option
- `chmod` means modify
- `cmown` means owner
- `sudo` stands for "superuser do"
- Why linux is better for programming:
1) Security: bcz it's open source, anti-virus free built-in
2) Workflow: package manager, easy to install compared to other OS
3) No Rebooting: you can update entire OS without rebooting, not the case with Windows/MacOS
4) Powerful Programming Tools: pre-installed like grep, wget, cron; different distributions have different superpowers
5) Task Automation
6) Performance: light-weight, compatible with almost all machines, reliability
7) Useful Error Messages: compared to Windows/MacOs like "Oops something went wrong", you'll see exactly what happened 
8) Customization: limitless, customize environment
