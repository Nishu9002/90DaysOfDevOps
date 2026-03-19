The core components of Linux (kernel, user space, init/systemd)
- Linux architecture is based on ASK - Application, shell and kernel. kernel is the heart of linux. Applications use shell to connect to the linux kernel and kernel in return takes the commands further to the hardware.
so, basically its like users cannot directly interact with the kernel if they want something like list of files or so from the hardware. so, what we do is we have the shell interface between users and kernel, so the users interact with the kernel using shell.

How processes are created and managed
Okay, so processes are created in this way, when a program runs, kernel executes it and provides it a unique PID. Then later the process is managed through scheduling, sigals and system calls. the very first process that runs when the system boots is init or systemd.


What systemd does and why it matters
systemmd is the init system. it is the very first process that runs after the kernel boots. it starts the essential services like networking, logging and user sessions.


Explain process states (running, sleeping, zombie, etc.)
running-means the process is executing in CPU
sleeping means the process is waiting for resources
stopped means the process is paused by signal
zombie means the process is terminated but not cleaned up


List 5 commands you would use daily
1. create directory - mkdir
2. copy/move/rename a file or folder - cp and mv
3. ping
4. ps aux, top to check the active processes
5. ls to list all files 




