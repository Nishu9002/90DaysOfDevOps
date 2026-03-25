# Day 09 Challenge

## Users & Groups Created

* Users: tokyo, berlin, professor, nairobi
* Groups: developers, admins, project-team

---

## Group Assignments

* tokyo → developers, project-team
* berlin → developers, admins
* professor → admins
* nairobi → project-team

---

## Directories Created

* /opt/dev-project → group: developers → permissions: 775
* /opt/team-workspace → group: project-team → permissions: 775

---

## Commands Used (Detailed Explanation)

### 1. User Management

**Create user with home directory**

```
sudo useradd -m <username>
```

* `useradd` → creates a new user
* `-m` → creates a home directory (/home/username)

Example:

```
sudo useradd -m tokyo
```

---

**Set password for user**

```
sudo passwd <username>
```

* Assigns or changes password for a user

Example:

```
sudo passwd tokyo
```

---

### 2. Group Management

**Create a group**

```
sudo groupadd <groupname>
```

* Creates a new group

Example:

```
sudo groupadd developers
```

---

**Add user to a group**

```
sudo usermod -aG <groupname> <username>
```

* `usermod` → modifies user
* `-a` → append (keeps existing groups)
* `-G` → specifies group

Example:

```
sudo usermod -aG developers tokyo
```

---

**Check group membership**

```
groups <username>
```

* Displays groups a user belongs to

Example:

```
groups tokyo
```

---

### 3. Directory & Permission Management

**Create directory**

```
sudo mkdir -p /path
```

* `mkdir` → creates directory
* `-p` → creates parent directories if needed

Example:

```
sudo mkdir -p /opt/dev-project
```

---

**Change group ownership**

```
sudo chgrp <groupname> <directory>
```

* Changes group ownership of a file/directory

Example:

```
sudo chgrp developers /opt/dev-project
```

---

**Change permissions**

```
sudo chmod 775 <directory>
```

* Sets permission:

  * 7 → read + write + execute (owner)
  * 7 → read + write + execute (group)
  * 5 → read + execute (others)

Example:

```
sudo chmod 775 /opt/dev-project
```

---

**Check permissions**

```
ls -ld <directory>
```

* Shows permissions, owner, and group

Example:

```
ls -ld /opt/dev-project
```

---

### 4. Testing Access (Important)

**Run command as another user**

```
sudo -u <username> <command>
```

* Executes command as specified user

Example:

```
sudo -u tokyo touch /opt/dev-project/file1.txt
```

---

**Create file**

```
touch <filename>
```

* Creates empty file

Example:

```
touch file1.txt
```

---

**List files with details**

```
ls -l <directory>
```

* Shows file owner, group, permissions

Example:

```
ls -l /opt/dev-project
```

---

## What I Learned

* Difference between users and groups in Linux
* How group-based permissions simplify access control
* How to use chmod to control file access
* How to simulate users using `sudo -u`
* How shared directories work in real DevOps environments

---

## Why This Matters for DevOps

User and permission management is critical in production systems to:

* Control access to applications and files
* Enable team collaboration securely
* Prevent unauthorized changes
* Manage multi-user environments effectively
