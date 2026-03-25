# Day 10 Challenge

## Files Created

* devops.txt
* notes.txt
* script.sh

---

## Permission Changes

* script.sh → made executable using `chmod +x`
* devops.txt → removed write permission (read-only)
* notes.txt → set to 640 (rw-r-----)
* project directory → set to 755 (rwxr-xr-x)

---

## Commands Used (Detailed)

### 🔹 File Creation

```bash
touch devops.txt
```

* Creates an empty file

```bash
echo "This is my DevOps practice file" > notes.txt
```

* Creates a file and writes content into it

```bash
vim script.sh
```

* Opens editor to create a script file
* Content added:

```bash
echo "Hello DevOps"
```

---

### 🔹 File Reading

```bash
cat notes.txt
```

* Displays full content of file

```bash
vim -R script.sh
```

* Opens file in read-only mode (prevents accidental edits)

```bash
head -n 5 /etc/passwd
```

* Displays first 5 lines of file

```bash
tail -n 5 /etc/passwd
```

* Displays last 5 lines of file

---

### 🔹 Viewing Permissions

```bash
ls -l
```

* Lists files with permissions, owner, and group

```bash
ls -l devops.txt notes.txt script.sh
```

* Shows permissions of specific files

---

### 🔹 Changing Permissions

```bash
chmod +x script.sh
```

* Adds execute permission (required to run script)

```bash
./script.sh
```

* Executes the script

```bash
chmod -w devops.txt
```

* Removes write permission (makes file read-only)

```bash
chmod 640 notes.txt
```

* Sets permission:

  * Owner → read & write
  * Group → read only
  * Others → no access

```bash
mkdir project
```

* Creates a directory

```bash
chmod 755 project
```

* Sets permission:

  * Owner → full access (rwx)
  * Group → read & execute
  * Others → read & execute

---

### 🔹 Testing Permissions

```bash
echo "test" >> devops.txt
```

* Attempt to write to read-only file → results in "Permission denied"

```bash
chmod -x script.sh
./script.sh
```

* Removes execute permission and attempts to run script → results in "Permission denied"

---

## What I Learned

* How Linux file permissions work using rwx system
* How to modify permissions using symbolic and numeric methods
* Why execute permission is required to run scripts
* How to secure files by restricting write access
* How to test and troubleshoot permission-related errors

---

## Why This Matters for DevOps

Understanding file permissions is essential for:

* Securing sensitive configuration files
* Controlling access in multi-user systems
* Running automation scripts safely
* Preventing unauthorized changes in production environments
