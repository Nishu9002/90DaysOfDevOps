# Day 13 Challenge – Linux Volume Management (LVM)

## Task 0: Setup
- Switched to root user:
  ```bash
  sudo -i
Usage: Ensures you have full privileges to run LVM commands.

Created a 1GB virtual disk image:

bash
dd if=/dev/zero of=/tmp/disk1.img bs=1M count=1024
Usage: Creates a fake disk file filled with zeros, size = 1GB.


bash
losetup -fP /tmp/disk1.img
losetup -a
Usage: Maps the disk image to a loop device (e.g., /dev/loop6) so Linux treats it like a real disk.

Task 1: Check Current Storage
bash
lsblk
pvs
vgs
lvs
df -h
lsblk: Lists block devices (disks, partitions, loop devices).

pvs: Shows physical volumes known to LVM.

vgs: Shows volume groups.

lvs: Shows logical volumes.

df -h: Displays mounted filesystems and usage in human-readable format.

Task 2: Create Physical Volume
bash
pvcreate /dev/loop6
pvs
pvcreate: Initializes /dev/loop6 as an LVM physical volume.

pvs: Confirms the physical volume exists.

Task 3: Create Volume Group
bash
vgcreate devops-vg /dev/loop6
vgs
vgcreate: Creates a volume group named devops-vg using /dev/loop6.

vgs: Displays the new volume group and its size.

Task 4: Create Logical Volume
bash
lvcreate -L 500M -n app-data devops-vg
lvs
lvcreate: Creates a logical volume named app-data of size 500MB inside devops-vg.

lvs: Shows logical volumes and their details.

Task 5: Format and Mount
bash
mkfs.ext4 /dev/devops-vg/app-data
mkdir -p /mnt/app-data
mount /dev/devops-vg/app-data /mnt/app-data
df -h /mnt/app-data
mkfs.ext4: Formats the logical volume with the ext4 filesystem.

mkdir -p: Creates a mount point directory /mnt/app-data.

mount: Attaches the logical volume to /mnt/app-data.

df -h: Confirms the volume is mounted and shows available space.

Task 6: Extend the Volume
bash
lvextend -L +200M /dev/devops-vg/app-data
resize2fs /dev/devops-vg/app-data
df -h /mnt/app-data
lvextend: Increases the logical volume size by 200MB.

resize2fs: Resizes the filesystem to use the new space.

df -h: Verifies the updated size.

What I Learned
Mounting makes a storage device visible in the filesystem tree (like how C: drive is visible in Windows).

LVM provides flexibility: you can create, resize, and manage volumes without recreating partitions.

Loop devices are a safe way to practice LVM without needing extra hardware or cloud volumes.

