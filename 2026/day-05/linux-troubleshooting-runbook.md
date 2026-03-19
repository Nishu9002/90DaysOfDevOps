1. ENVIRONMENT BASICS: uname and cat os release

ubuntu@ip-172-31-0-235:~$ uname -a (shows the kernel details)
Linux ip-172-31-0-235 6.17.0-1009-aws #9~24.04.2-Ubuntu SMP Fri Mar  6 23:50:29 UTC 2026 x86_64 x86_64 x86_64 GNU/Linux

ubuntu@ip-172-31-0-235:~$ cat /etc/os-release   (os details in os release file)
PRETTY_NAME="Ubuntu 24.04.3 LTS"
NAME="Ubuntu"
VERSION_ID="24.04"
VERSION="24.04.3 LTS (Noble Numbat)"
VERSION_CODENAME=noble
ID=ubuntu
ID_LIKE=debian
HOME_URL="https://www.ubuntu.com/"
SUPPORT_URL="https://help.ubuntu.com/"
BUG_REPORT_URL="https://bugs.launchpad.net/ubuntu/"
PRIVACY_POLICY_URL="https://www.ubuntu.com/legal/terms-and-policies/privacy-policy"
UBUNTU_CODENAME=noble
LOGO=ubuntu-logo
ubuntu@ip-172-31-0-235:~$ ^C


2. Filesystem sanity: 
Created test directory and copied hosts file

Command:
mkdir /tmp/runbook-demo
cp /etc/hosts /tmp/runbook-demo/hosts-copy
ls -l /tmp/runbook-demo

Observation:
File successfully copied, permissions visible

ubuntu@ip-172-31-0-235:~$ mkdir /tmp/runboook-demo
ubuntu@ip-172-31-0-235:~$ cp /etc/hosts /tmp/runbook-demo/hosts-copy
cp: cannot create regular file '/tmp/runbook-demo/hosts-copy': No such file or directory
ubuntu@ip-172-31-0-235:~$ mkdir /tmp/runboook-demo
mkdir: cannot create directory ‘/tmp/runboook-demo’: File exists
ubuntu@ip-172-31-0-235:~$ cp /etc/hosts /tmp/runbook-demo/hosts-copy
cp: cannot create regular file '/tmp/runbook-demo/hosts-copy': No such file or directory
ubuntu@ip-172-31-0-235:~$ ls -ld /tmp/runbook-demo
ls: cannot access '/tmp/runbook-demo': No such file or directory
ubuntu@ip-172-31-0-235:~$ ^C
ubuntu@ip-172-31-0-235:~$ cp /etc/hosts /tmp/runboook-demo/hosts-copy
ubuntu@ip-172-31-0-235:~$ ls -l hosts-copy
ls: cannot access 'hosts-copy': No such file or directory
ubuntu@ip-172-31-0-235:~$ ls -l /tmp/runboook-demo
total 4
-rw-r--r-- 1 ubuntu ubuntu 221 Mar 19 13:12 hosts-copy
ubuntu@ip-172-31-0-235:~$ ls -l /tmp/runboook-demo/hosts-copy
-rw-r--r-- 1 ubuntu ubuntu 221 Mar 19 13:12 /tmp/runboook-demo/hosts-copy
ubuntu@ip-172-31-0-235:~$ ls -l /etc/hosts
-rw-r--r-- 1 root root 221 Dec 11 22:50 /etc/hosts


3. CPU and Memory:

pgrep cron
532

pregp to find process id of cron service

 ps -o pid,pcpu,pmem,comm -p 532
    PID %CPU %MEM COMMAND
    532  0.0  0.3 cron  
after getting the pid of a process, checked everything about cpu and memory usage of that process 

free -h
               total        used        free      shared  buff/cache   available
Mem:           911Mi       371Mi       298Mi       2.7Mi       406Mi       539Mi
Swap:             0B          0B          0B
free to check the free memory


4. Disk/IO commands:

df -h
Filesystem       Size  Used Avail Use% Mounted on
/dev/root        6.8G  2.5G  4.3G  37% /
tmpfs            456M     0  456M   0% /dev/shm
tmpfs            183M  868K  182M   1% /run
tmpfs            5.0M     0  5.0M   0% /run/lock
efivarfs         128K  3.8K  120K   4% /sys/firmware/efi/efivars
/dev/nvme0n1p16  881M  159M  660M  20% /boot
/dev/nvme0n1p15  105M  6.2M   99M   6% /boot/efi
tmpfs             92M   12K   92M   1% /run/user/1000

df checks the memory usage, so if the processes use more than 90% of disk space, its a big problem then

### Log directory size

du -sh /var/log
du: cannot read directory '/var/log/private': Permission denied
du: cannot read directory '/var/log/chrony': Permission denied
du: cannot read directory '/var/log/amazon': Permission denied
59M     /var/log

Command: du -sh /var/log

Output:
Permission denied errors for some directories
Total visible size: 59M

Observation:
Log directory size is small and not consuming excessive space.
Some directories were restricted due to permissions, so actual size may be slightly higher.
No immediate disk risk observed.

5. NETWORK:

ss -tulpn (shows the information of network sockets)
ss -tulpn
Netid           State            Recv-Q           Send-Q                          Local Address:Port                       Peer Address:Port           Process           
udp             UNCONN           0                0                                  127.0.0.54:53                              0.0.0.0:*                                
udp             UNCONN           0                0                               127.0.0.53%lo:53                              0.0.0.0:*                                
udp             UNCONN           0                0                           172.31.0.235%ens5:68                              0.0.0.0:*                                
udp             UNCONN           0                0                                   127.0.0.1:323                             0.0.0.0:*                                
udp             UNCONN           0                0                                       [::1]:323                                [::]:*                                
tcp             LISTEN           0                4096                                  0.0.0.0:22                              0.0.0.0:*                                
tcp             LISTEN           0                4096                            127.0.0.53%lo:53                              0.0.0.0:*                                
tcp             LISTEN           0                4096                               127.0.0.54:53                              0.0.0.0:*                                
tcp             LISTEN           0                4096                                     [::]:22                                 [::]:*                                


curl -I google.com- used to display http headers and response body

curl -I http://localhost
curl: (7) Failed to connect to localhost port 80 after 0 ms: Couldn't connect to server
ubuntu@ip-172-31-0-235:~$ curl -I google.com
HTTP/1.1 301 Moved Permanently
Location: http://www.google.com/
Content-Type: text/html; charset=UTF-8
Content-Security-Policy-Report-Only: object-src 'none';base-uri 'self';script-src 'nonce-7YNRLTNK6vUjurUysSe43A' 'strict-dynamic' 'report-sample' 'unsafe-eval' 'unsafe-inline' https: http:;report-uri https://csp.withgoogle.com/csp/gws/other-hp
Reporting-Endpoints: default="//www.google.com/httpservice/retry/jserror?ei=xQK8adafCdKw5NoPrML1gAk&cad=crash&error=Page%20Crash&jsel=1&bver=2404&dpf=wCkmmEpbCUvvFM_dgVdOqnels9KpUGJJXIfGRUpyAq8"
Date: Thu, 19 Mar 2026 14:05:57 GMT
Expires: Sat, 18 Apr 2026 14:05:57 GMT
Cache-Control: public, max-age=2592000
Server: gws
Content-Length: 219
X-XSS-Protection: 0
X-Frame-Options: SAMEORIGIN


6. LOGS: 

journalctl -u cron -n 10   (checks the logs of cron service)
Mar 19 13:55:01 ip-172-31-0-235 CRON[3241]: pam_unix(cron:session): session closed for user root
Mar 19 14:05:01 ip-172-31-0-235 CRON[3261]: pam_unix(cron:session): session opened for user root(uid=0) by root(uid=0)
Mar 19 14:05:01 ip-172-31-0-235 CRON[3262]: (root) CMD (command -v debian-sa1 > /dev/null && debian-sa1 1 1)
Mar 19 14:05:01 ip-172-31-0-235 CRON[3261]: pam_unix(cron:session): session closed for user root
Mar 19 14:15:01 ip-172-31-0-235 CRON[3297]: pam_unix(cron:session): session opened for user root(uid=0) by root(uid=0)
Mar 19 14:15:01 ip-172-31-0-235 CRON[3298]: (root) CMD (command -v debian-sa1 > /dev/null && debian-sa1 1 1)
Mar 19 14:15:01 ip-172-31-0-235 CRON[3297]: pam_unix(cron:session): session closed for user root
Mar 19 14:17:01 ip-172-31-0-235 CRON[3304]: pam_unix(cron:session): session opened for user root(uid=0) by root(uid=0)
Mar 19 14:17:01 ip-172-31-0-235 CRON[3305]: (root) CMD (cd / && run-parts --report /etc/cron.hourly)
Mar 19 14:17:01 ip-172-31-0-235 CRON[3304]: pam_unix(cron:session): session closed for user root


tail -n 10 /var/log/syslog  (checks all logs of the system)
2026-03-19T14:22:43.014030+00:00 ip-172-31-0-235 systemd[3629]: Listening on pk-debconf-helper.socket - debconf communication socket.
2026-03-19T14:22:43.014083+00:00 ip-172-31-0-235 systemd[3629]: Listening on snapd.session-agent.socket - REST API socket for snapd user session agent.
2026-03-19T14:22:43.037070+00:00 ip-172-31-0-235 systemd[3629]: Listening on dbus.socket - D-Bus User Message Bus Socket.
2026-03-19T14:22:43.043612+00:00 ip-172-31-0-235 systemd[3629]: Listening on gpg-agent-ssh.socket - GnuPG cryptographic agent (ssh-agent emulation).
2026-03-19T14:22:43.043797+00:00 ip-172-31-0-235 systemd[3629]: Reached target sockets.target - Sockets.
2026-03-19T14:22:43.043919+00:00 ip-172-31-0-235 systemd[3629]: Reached target basic.target - Basic System.
2026-03-19T14:22:43.043975+00:00 ip-172-31-0-235 systemd[1]: Started user@1000.service - User Manager for UID 1000.
2026-03-19T14:22:43.044444+00:00 ip-172-31-0-235 systemd[3629]: Reached target default.target - Main User Target.
2026-03-19T14:22:43.044655+00:00 ip-172-31-0-235 systemd[3629]: Startup finished in 120ms.
2026-03-19T14:22:43.048970+00:00 ip-172-31-0-235 systemd[1]: Started session-37.scope - Session 37 of User ubuntu.

observation:
no critical errors in logs, everything is running well. disk and memory usage is fine too.

## If This Worsens (Next Steps)

1. Restart the service
   Command: systemctl restart cron

2. Enable detailed logging
   Modify config to increase log verbosity

3. Trace process behavior
   Command: strace -p <PID>

4. Check for high CPU processes
   Command: top

5. Investigate disk issues
   Command: df -h
