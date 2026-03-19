process management:
1. ps aux - it will list all the running processes
2. top - it will show real time view of all the processes, basically its like a live video feed as it will show view of all the processes actively running
3. htop - it is also similar to top, shows real time view of all the processes but it is more like an advanced version, it will help you to navivate between the process and even kill or stop the processes, more user friendly interface
4. kill -9 PID - to force stop a process
5. kill -STOP PID - to pause a process
6. kill -CONT PID - to resume a paused process
7. jobs - list background jobs in the shell
8. fg %1 - bring job to 1 to foreground
9. bg %1 - resume job 1 in background
10. systemctl status <serice> - check the service status

File system:
1. ls -l - lists all the files
2. pwd - shows the current working directory
3. mkdir - helps create a new directory
4. cp - copy files or folder content from source to destination (cp file1 file2) it will copy file1 to file 2
5. cd - changes the directory
6. mv file dir/ - moves file1 cocntent to directory
7. rm file - deletees the file
8. rm -r dir/ - deletes all the contents of the directory and the folder too
9. find /path -name "x.log" - finds a file by the name
10. du -sh <dir> - shows the disk usage of a directory

Networking troubleshooting:
1. ping google.com - tests connectivity to a host (checks if the host is reachable)
2. ip addr - shows the ip address of network interfaces 
3. curl https://example.com - fetches a webpage (checks if the service is responding properly)
4. dig example.com - DNS loopkup (is the domain correct or does the domain resolve correctly)
5. netstat -tulnp - lists open ports and listening services

   
