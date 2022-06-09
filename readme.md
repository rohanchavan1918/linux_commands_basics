# Linux Cheat Sheet

#### This is a simple compilation of basic linux commands which were used in a talk/ppt.

- pwd  
``pwd``  
Find the current directory.

- ls  
``ls``  
Find the files present in the current directory.   
Examples  
``ls folder``  
``ls -ll`` - shows all files along with permissions and timestamp and other info.  
``ls -la`` - same as above but shows hidden files.  



- cd  
``cd``
Change the directory to another directory.    
Examples  
``cd <directory>``  - Goto Particular sub directory  
``cd ..`` - Goto parent directory

- cat  
``cat <file_path>``  
Read and print content of any file and display its content in terminal  

- echo  
``echo "text"``
Print any text in terminal.

- sudo  
``sudo <command>``
Run a command with superuser privileges.

- grep  
``grep <pattern>``
This command is used to filter the output of another commands.

- apt update  
``sudo apt update``
This command is used to update the server.

- apt install  
``sudo apt install <package-name>``
This command is used to install a package.

- uname  
`uname -a`  
This command is used to find the info of the server.  

- ifconfig  
``ifconfig``
This commmand is used to find out the IP and available network adapters.

- cp  
`cp <file> <destination_folder> `  
This command is used to create a copy of a file to a specefic destination.  
Examples -  
`cp file.txt files/`   
Copy a single file "file.txt" into a folder named as "files"  
`cp fi* files/`  
Copy all files starting with "fi" to folder named as "files"

- mv  
`mv <file> <destination_folder> `  
This command is used to move a file to a specefic destination.  
Examples  
`mv file.txt files/`  
move a single file "file.txt" into a folder named as "files"  
`mv fi* files/`  
move all files starting with "fi" to folder named as "files"

- rm  
`rm <file_path>`  
This command is used to delete the file. There's no recycle bin in linux so once this file is deleted its deleted permanently.
Note - This command only deletes files

- rmdir  
`rmdir <directory_path>`
This command is used to delete the directory which is empty. To delete directories which has files inside it use the command below.  
`rm -rf <dir_path>`

- alias  
`alias <ALIAS_NAME>="command"`  
This command is used to create alias of a command.

## Working with Text Editors
There are multiple Text editors which can be used in Linux, but vim and nano are the ones which are included in every distro and is a must know. VIM is also present in slim docker images, so it can also be used if you need to manually ssh into a docker container and edit any file, etc.

- #### VIM  
    `vim file.txt`  
    `vi file.txt`   
    `i` to start insert mode in vim
    `:w` save the current changes to a file.  
    `:q` quits Vim. If you have unsaved changes, you will be asked whether or not you'd like to save your changes before quitting.  
    `:q!` quit without saving unsaved changes.  
    `:wq` save and quit.  

    Advanced guide - https://web.stanford.edu/class/cs107/resources/vim.html#:~:text=vim%20has%20two%20%22modes%22%3A,and%20edit%20text%20in%20bulk.

- #### NANO
    Nano is another editor which can be used to create/edit files and folders. It is comparatively easy then VIM as there are no modes on nano.  
    `nano file.txt`   
    `ctrl + o` to save file
    `ctrl + x` to close the file  
    Advanced guide - https://linuxize.com/post/how-to-use-nano-text-editor/

## Important Linux files & directories
- `/home`  
    User home directories
- `/root`  
    root home directories
- `/mnt`  
    The typical mount point for the user-mountable devices such as floppy drives and CDROM
- `/tmp`  
    A standard repository for temporary files created by applications and users.
- `/dev/null`  
    Does nothing. Its like a black hole, once anything goes in it goes forever.
- `/etc/crontab`  
    A parent shell script to run commands periodically.  It invokes hourly, daily, weekly, and monthly scripts.
- `/etc/hosts`  
    Contains host names and their corresponding IP addresses used for name resolution whenever a DNS server is unavailable.
- `/etc/passwd`  
    Contains information regarding registered system users. Passwords are typically kept in a shadow file for better security.
- `.bash_history`  
    File which stores last 500 commands
- `.bashrc`  
    File which stores bash config for the user  
- `.ssh`
    Directory where all ssh keys are typically present

## Generic Scenarios


#### Check for open ports  

- If we have access to a server and can check directly with the help of a utility called as `netstat`  
Get a list of all open ports    
`netstat -ano`  
Filter the result to only 1 port  
`netstat -ano | grep "<port_no>"`

- If we dont have access to the server, we can use a utility called as `telnet` to check if the port is open.  
`telnet <ip_addr> <port>`

#### Zip unzip / untar files

- To unzip files  
`sudo apt-get install unzip`  
`unzip file.zip -d destination_folder`  

- To untar files (tar is another compression used commonly in linux)  
`tar xvzf file.tar.gz`  

#### Download files/folders from external sources
- Download files from a url  
``wget <url>``

#### Serve files on server temperorily  
- Many times we need to download some files from the server to our local environment, the intended way to do this is by using scp. But quick and *dirty* alternative to do this is to host a temperory file server on a particular (*higher*) port. Run this command from the directory where you want to serve the files.  
`python3 -m http.server 5555`  
If you then open your browser and search for `http://<ip>:5555/` all files can be visible and can be downloaded. This is most effective when you want to automate downloading files. You can use `wget` to download these files in your local enviromnent.

#### Multiplexing your terminal window
- `tmux` is a utility that can be used to split/divide one terminal window into multiple windows. This is very helpful when you are monitoring logs etc. It can also be used to save server sessions etc.

- `ctrl + b` -- is the base command for tmux  
- `Ctrl + b ;` -- Toggle last active pane  
- `Ctrl + b %` -- Split pane with horizontal layout  
- `Ctrl + b "` -- Split pane with vertical layout  
- `Ctrl + b {` -- Move the current pane left  
- `Ctrl + b }` -- Move the current pane right  
- `Ctrl + b <arrow_keys>` -- set the pane 

- `Ctrl + b c` -- Create window
- `Ctrl + b ,` -- Rename current window
- `Ctrl + b &` -- Close current window
- `Ctrl + b p` -- Previous window

#### Check currently running processes
- `ps -aux`
    This command will list all the processes running

#### To kill any process
- `kill <pid>`
- `pkill <pid>`
- `pkill -r <process_name>`  

#### Check Memory in real time
- `free -g`

#### Monitor CPU load in real time
- `top`
- Press 1 to see cores and toggle
- press t to toggle info
- `P` Sort according to the %CPU column.
- `M` Sort according to the %MEM column.
- `N` Sort according to the PID column.
- `T` Sort according to the TIME+ column.
- `c` To see full command.

    Advanced Usage - https://www.howtogeek.com/668986/how-to-use-the-linux-top-command-and-understand-its-output/

#### Check free disk space
- `df -h`

#### SSH Access  
Connect to server using ssh  
`ssh <user>@<ip>`  
`ssh <user>@<ip> -i <path_to_pem_file>`  

Transfer files using scp  
`scp source_file_name username@destination_host:destination_folder`
