### Classic SysAdmin: The Linux Filesystem Explained

This classic article provides a comprehensive understanding of the Linux filesystem, helping users navigate its structure efficiently.

#### Structure Overview

1. **Root Directory ("/"):**
   - Central starting point for the entire filesystem.
   - Use the `tree` command to visualize the directory tree.

   ```bash
   tree /
   ```

   - Limit tree depth with `-L` option:

   ```bash
   tree -L 1 /
   ```

2. **Key Directories:**

   - **/bin:**
     - Contains binaries and basic command applications.

   - **/boot:**
     - Essential files for system startup.
     - Handle with care; critical for system operation.

   - **/dev:**
     - Holds device files, generated during boot or dynamically.

   - **/etc:**
     - Historically "et cetera," now "Everything to configure."
     - System-wide configuration files reside here.
     - Exercise caution; critical system settings.

   - **/home:**
     - User personal directories.
     - e.g., `/home/username`

   - **/lib:**
     - Libraries containing code for applications.
     - Essential for various system functions.

   - **/media:**
     - Automatic mount point for external storage.
     - Dynamic directory for plug-and-play devices.

   - **/mnt:**
     - Manual mount point for storage devices.
     - Less common in modern systems.

   - **/opt:**
     - Directory for user-compiled software.
     - Applications: `/opt/bin`, Libraries: `/opt/lib`.

   - **/proc:**
     - Virtual directory providing information about the system.
     - Generated at boot or dynamically during runtime.

   - **/root:**
     - Home directory for the superuser (Administrator).
     - Reserved for system administration; avoid user interference.

   - **/run:**
     - Stores temporary data for system processes.
     - System processes use this for temporary storage.

   - **/sbin:**
     - Contains essential system binaries.
     - Requires superuser privileges (`sudo`).

   - **/usr:**
     - Originally for user home directories.
     - Now holds a mix of applications, libraries, documentation, etc.
     - Subdirectories: `/usr/bin`, `/usr/sbin`, `/usr/lib`.

   - **/srv:**
     - Data for servers.
     - e.g., `/srv/http`, `/srv/ftp`.

   - **/sys:**
     - Virtual directory, similar to `/proc` and `/dev`.
     - Contains information from connected devices.

   - **/tmp:**
     - Temporary files, often placed by running applications.
     - Users can interact without superuser privileges.

   - **/var:**
     - Originally named for variable data; contains frequently changing data.
     - e.g., `/var/log` for logs, `/var/spool` for spooled tasks.

#### Digging Deeper

- Use `cd` to change directories, `pwd` to print the current directory, and `ls` to list directory contents.
  
  ```bash
  cd /desired/directory
  pwd
  ls
  ```

- Explore subdirectories using `cd ..` to move up one level.

#### Conclusion

- Linux filesystem layout is generally consistent across distributions.
- Explore and familiarize yourself using commands like `tree`, `ls`, and `cd`.
- Navigating directories becomes intuitive with practice.
- Understanding the filesystem enhances system administration capabilities.