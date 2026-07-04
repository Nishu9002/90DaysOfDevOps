create a short note that explains:

The core components of Linux (kernel, user space, init/systemd)

The core components of Linux comprises of ASK configuration: Application, Shell and Kernel. Application is the top layer wherein user interacts. Shell is the layer between kernel and application layer. Shell takes the commands from users and converts it to a form understandable by the kernel. And kernel is the core component of linux that manages the hardware.

user space is isolated from kernel. it is a space(set of memory locations) where non-privileged processes and normal user applications execute.

init is the very first process that start when a kernel boots and acts as a parent of all the processes. Systemd is a modern system manager suite that handles paprallel service setup, aggressive caching and event-based tracking.


How processes are created and managed
In linux, a process is a program in execution. The processes are carried out by relying on a strict parent-child hierarchical tree structure managed by Linux. All processes stem from a single root process systemd. Every subsequent process is spawned by an existing process through a 2-step system call sequence. 2 steps include cloning and execution.  

What systemd does and why it matters
systemd is the suite of buiding blocks that handles paprallel service setup, aggressive caching and event-based tracking.

Explain process states (running, sleeping, zombie, etc.)
running - the process is running in the CPU core or is in queue to be executed.
sleeping - the process is waiting for an event or a resource
zombie - the process is dead but its exit entry remains in the table until the parent reads it. (terminated but not cleaned up)
stopped - the process is suspended or paused by the user.

List 5 commands you would use daily
mkdir - to make directory
cp and mv - to copy and move files
ping
ps aux, top - to check the active processes
ls -l - to list all files
du, df - to see the disk usage and available space



