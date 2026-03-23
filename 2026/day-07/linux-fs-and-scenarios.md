# Day 07 – Linux File System & Scenario Practice

---

## 🔹 Part 1: Linux File System Hierarchy

### /

Root directory – starting point of entire Linux system.

Command:
ls -l /

Observation:
Contains directories like bin, etc, home, var

Use case:
I would use this when navigating the system from the top level.

---

### /home

Stores user home directories.

Command:
ls -l /home

Observation:
User folders present (like ubuntu, ec2-user)

Use case:
I would use this to access user files and data.

---

### /root

Home directory of root user.

Command:
ls -l /root

Observation:
Contains root-specific files

Use case:
I would use this when working as root user.

---

### /etc

Contains configuration files.

Command:
ls -l /etc

Observation:
Files like hostname, hosts, passwd

Use case:
I would use this when modifying system configurations.

---

### /var/log

Stores system logs.

Command:
ls -l /var/log

Observation:
Files like syslog, auth.log

Use case:
I would use this for debugging issues and checking logs.

---

### /tmp

Temporary files storage.

Command:
ls -l /tmp

Observation:
Temporary files created by system/apps

Use case:
I would use this for temporary storage or testing.

---

### /bin

Essential system binaries.

Command:
ls -l /bin

Observation:
Commands like ls, cp, mv

Use case:
I would use this to understand where basic commands come from.

---

### /usr/bin

User-level binaries.

Command:
ls -l /usr/bin

Observation:
Large number of executable programs

Use case:
I would use this when checking installed applications.

---

### /opt

Optional third-party software.

Command:
ls -l /opt

Observation:
May contain installed apps

Use case:
I would use this for custom software installations.

---

## 🔹 Hands-on Practice

Find largest logs:
du -sh /var/log/* 2>/dev/null | sort -h | tail -5

Check hostname:
cat /etc/hostname

Check home directory:
ls -la ~

---

## 🔹 Part 2: Scenario-Based Practice

### Scenario 1: Service Not Starting

Step 1:
systemctl status myapp  
Why: Check if service is running or failed

Step 2:
journalctl -u myapp -n 50  
Why: View recent logs for errors

Step 3:
systemctl is-enabled myapp  
Why: Check if service starts on boot

Step 4:
systemctl start myapp  
Why: Try starting service manually

---

### Scenario 2: High CPU Usage

Step 1:
top  
Why: View live CPU usage

Step 2:
ps aux --sort=-%cpu | head -10  
Why: List top CPU-consuming processes

Step 3:
htop  
Why: Better visualization (if installed)

Step 4:
kill <PID>  
Why: Stop problematic process if needed

---

### Scenario 3: Finding Service Logs

Step 1:
systemctl status docker  
Why: Check service status

Step 2:
journalctl -u docker -n 50  
Why: View last 50 log lines

Step 3:
journalctl -u docker -f  
Why: Monitor logs in real-time

---

### Scenario 4: File Permission Issue

Step 1:
ls -l /home/user/backup.sh  
Why: Check permissions

Step 2:
chmod +x /home/user/backup.sh  
Why: Add execute permission

Step 3:
ls -l /home/user/backup.sh  
Why: Verify permission update

Step 4:
./backup.sh  
Why: Execute script

---

## ✅ What I Learned

- Linux file system structure is very important for troubleshooting
- Logs and configs are stored in specific directories
- Step-by-step debugging is key in DevOps
