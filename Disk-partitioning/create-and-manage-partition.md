📚 Primary partitions are the main partitions on a hard drive and can be used to install an operating system.
🔄 Extended partitions are used to create additional logical partitions.
💾 Logical partitions are contained within extended partitions and are used for data storage.
📊 Linux allows up to four primary partitions or three primary partitions and one extended partition.
🚀 Using logical partitions can overcome the limitation of only having four primary partitions.
📑 GParted is a popular graphical tool for creating and managing partitions in Linux.🔒 It is important to be cautious when modifying partitions, as data loss can occur if not done correctly.


If adding the disk while the machine is running, there is chance the disk might not be visible with ldblk command. To rescan the newly added disk use folowing commands:
ls sys/clsss/sci_host/ | while read host; do echo "---" > /sys/class/sci_host/$host/scan; done


Summary of the commands and their purposes:

1. **parted -l:**
   - Purpose: Lists all available disks and partitions on the system.
   - Usage: `parted -l`
  
2. **fdisk /dev/sdX:**
   - Purpose: Creates a new partition table on the specified disk.
   - Usage: `fdisk /dev/sdX`

3. **p:**
   - Purpose: Used in the fdisk utility to print existing partitions on the disk.
   - Usage: Inside fdisk, press `p`.

4. **d:**
   - Purpose: Used in the fdisk utility to delete a partition.
   - Usage: Inside fdisk, press `d` followed by the partition number.

5. **n:**
   - Purpose: Used in the fdisk utility to create a new partition.
   - Usage: Inside fdisk, press `n` and provide partition type, starting and ending points.

6. **t:**
   - Purpose: Used in the fdisk utility to change the partition type.
   - Usage: Inside fdisk, press `t` followed by the partition number and the new type code.

7. **w:**
   - Purpose: Used in the fdisk utility to write changes to the disk and exit.
   - Usage: Inside fdisk, press `w`.

8. **mkfs.ext4 /dev/sdX#:**
   - Purpose: Creates an ext4 filesystem on the specified partition.
   - Usage: `mkfs.ext4 /dev/sdX#`

9. **mount /dev/sdX# /mnt:**
   - Purpose: Mounts the specified partition to the specified mount point.
   - Usage: `mount /dev/sdX# /mnt`

10. **umount /mnt:**
    - Purpose: Unmounts the currently mounted partition from the specified mount point.
    - Usage: `umount /mnt`

11. **blkid /dev/sdX#:**
    - Purpose: Displays the UUID and other attributes of the specified partition.
    - Usage: `blkid /dev/sdX#`

12. **lsblk:**
    - Purpose: Displays information about all available block devices on the system.
    - Usage: `lsblk`

13. **gdisk /dev/sdX:**
    - Purpose: Creates a new partition table using the GPT format.
    - Usage: `gdisk /dev/sdX`

14. **sgdisk -n 0:0:+500M /dev/sdX:**
    - Purpose: Creates a new partition using the GPT format, specifying start and end points in megabytes.
    - Usage: `sgdisk -n 0:0:+500M /dev/sdX`

15. **partprobe /dev/sdX:**
    - Purpose: Informs the kernel about changes made to the partition table.
    - Usage: `partprobe /dev/sdX`

16. **mkswap /dev/sdX#:**
    - Purpose: Creates a swap space on the specified partition.
    - Usage: `mkswap /dev/sdX#`

17. **swapon /dev/sdX#:**
    - Purpose: Activates the specified swap partition for virtual memory.
    - Usage: `swapon /dev/sdX#`

18. **swapoff /dev/sdX#:**
    - Purpose: Deactivates the specified swap partition.
    - Usage: `swapoff /dev/sdX#`

These commands collectively serve the purpose of managing partitions in Linux, covering tasks such as creation, deletion, formatting, and mounting, with variations depending on the specific requirements and partition types.