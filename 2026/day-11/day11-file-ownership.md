# Day 11 Challenge – File Ownership (chown & chgrp)

## Task 1: Understanding Ownership
- Ran `ls -l` in home directory.
- Observed format: `-rw-r--r-- 1 owner group size date filename`
- **Owner vs Group:**
  - Owner → single user who created/controls the file.
  - Group → team of users who can share permissions.

---

## Task 2: Basic chown Operations
- Created file: `devops-file.txt`
- Checked ownership: `ls -l devops-file.txt`
- Changed owner to `tokyo` → `sudo chown tokyo devops-file.txt`
- Changed owner to `berlin` → `sudo chown berlin devops-file.txt`
- Verified with `ls -l`.

---

## Task 3: Basic chgrp Operations
- Created file: `team-notes.txt`
- Checked group: `ls -l team-notes.txt`
- Created group: `sudo groupadd heist-team`
- Changed group: `sudo chgrp heist-team team-notes.txt`
- Verified with `ls -l`.

---

## Task 4: Combined Owner & Group Change
- Created file: `project-config.yaml`
- Changed owner & group: `sudo chown professor:heist-team project-config.yaml`
- Created directory: `app-logs/`
- Changed owner & group: `sudo chown berlin:heist-team app-logs/`
- Verified with `ls -ld app-logs`.

---

## Task 5: Recursive Ownership
- Created directory structure:
  ```bash
  mkdir -p heist-project/vault
  mkdir -p heist-project/plans
  touch heist-project/vault/gold.txt
  touch heist-project/plans/strategy.conf
