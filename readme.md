# Linux Cheat Sheet

#### This is a simple compilation of basic linux commands which were used in a talk/ppt.

- pwd  
``pwd``  
Find the current directory. https://man7.org/linux/man-pages/man1/pwd.1.html  

- ls  
``ls``  
Find the files present in the current directory. https://man7.org/linux/man-pages/man1/ls.1.html  
Examples  
``ls folder``  
``ls -ll`` shows all files along with permissions and timestamp and other info.
``ls -la`` same as above but shows hidden files.  



- cd  
``cd``
Change the directory to another directory. https://man7.org/linux/man-pages/man1/cd.1p.html  
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
Examples - 
`mv file.txt files/` 
move a single file "file.txt" into a folder named as "files"  
`mv fi* files/`
move all files starting with "fi" to folder named as "files"



### Generic Scenarios

##### Check for open ports  

- If we have access to a server and can check directly with the help of a utility called as `netstat`  
Get a list of all open ports    
`netstat -ano`  
Filter the result to only 1 port  
`netstat -ano | grep "<port_no>"`

- If we dont have access to the server, we can use a utility called as `telnet` to check if the port is open.  
`telnet <ip_addr> <port>`

##### Zip unzip / untar files

- To unzip files  
`sudo apt-get install unzip`  
`unzip file.zip -d destination_folder`  

- To untar files (tar is another compression used commonly in linux)  
`tar xvzf file.tar.gz`  

##### Download files/folders from external sources
- Download files from a url  
``wget <url>``


delete
delete folder





python -m runserver
tmux
check open ports
vim
nano
netcat
check ip
