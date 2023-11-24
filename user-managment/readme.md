### Linux User Management Overview

User management in Linux involves creating, modifying, and deleting user accounts. There are three primary methods for user management:

1. **Graphical Tools:**
   - Suitable for new users.
   - Provides a user-friendly interface to perform user management tasks.

2. **Command Line Tools:**
   - Used by server administrators.
   - Includes commands like `useradd`, `userdel`, `passwd`, etc.

3. **Editing Configuration Files:**
   - Rarely used.
   - Directly editing local configuration files, such as `/etc/passwd` using tools like `vi`.

### `/etc/passwd` File

The local user database in Linux is stored in the `/etc/passwd` file. Each line in the file represents a user account and has seven columns separated by a colon:
1. Username
2. Placeholder for the password (often 'x' for shadow password)
3. User ID (UID)
4. Primary Group ID (GID)
5. Description or Comment
6. Home Directory
7. Login Shell

#### Root User
- The root user is the superuser with all privileges.
- Always has a UID of 0.

### `useradd` Command

The `useradd` command is used to add a new user. Example:

```bash
useradd -m -d /home/xyz -c "xyz" xyz
```

- `-m`: Create a home directory.
- `-d`: Specify the home directory.
- `-c`: Set the user's description.

### `/etc/default/useradd` File

File containing default user options. View with `useradd -D`.

### `userdel` Command

To delete a user account, use the `userdel` command:

```bash
userdel -r xyz
```

- `-r`: Removes the user's home directory.

### `usermod` Command

Modify properties of an existing user with `usermod`:

```bash
usermod -c 'jhonny' john
```

- `-c`: Change the user's description.

### `/etc/skel/` Directory

Contains hidden files with default values for profiles. Used as a default home directory for new users.

### Deleting Home Directories

Delete home directories along with user accounts using:

```bash
userdel -r john
```

### Login Shell

The `/etc/passwd` file indicates the login shell for each user.

### Changing Login Shell

Change the login shell for a user with `usermod`:

```bash
usermod -s /bin/bash jtp
```

### `chsh` Command

Users can change their login shell with the `chsh` command:

```bash
chsh
chsh -s /bin/sh
```

This overview provides insights into user management, including user creation, deletion, modification, and changing login shells in a Linux system.

### Linux Introduction to Users

In a Linux system, multiple users may have individual user accounts, allowing each person to have their own settings and permissions. This tutorial provides an introduction to identifying user accounts and creating additional user accounts. It also demonstrates how to run programs with different user accounts using `su` and `sudo` commands.

### `whoami` Command

The `whoami` command provides information about the current system's username.

```bash
whoami
```

- Example Output:
  ```
  sssit
  ```

### `who` Command

The `who` command displays information about all users currently logged on to the system.

```bash
who
```

- Example Output:
  ```
  sssit  tty1         2023-11-23 12:34 (:0)
  ```

### `who am i` Command

The `who am i` command shows information about the current user only.

```bash
who am i
```

- Example Output:
  ```
  sssit  tty1         2023-11-23 12:34 (:0)
  ```

### `w` Command

The `w` command provides information about logged-in users and their activities.

```bash
w
```

- Example Output:
  ```
  12:34:56 up 1:23, 1 user, load average: 0.15, 0.20, 0.25
  USER     TTY      FROM             LOGIN@   IDLE   JCPU   PCPU WHAT
  sssit    tty1     :0               12:34   1:23   0.10s  0.05s -bash
  ```

### `id` Command

The `id` command displays information about the user ID, primary group ID, and group memberships.

```bash
id
```

- Example Output:
  ```
  uid=1000(sssit) gid=1000(sssit) groups=1000(sssit),4(adm),24(cdrom),27(sudo),30(dip),46(plugdev),116(lpadmin),126(sambashare)
  ```

This tutorial gives a brief overview of commands to identify users, their activities, and their group memberships in a Linux system.

### Linux Create User

On a Linux server, creating and managing user accounts is a fundamental task. This tutorial explains two common methods to add a user to a Linux system: through the graphical user interface (GUI) and using the `useradd` command in the terminal.

#### 1. **Graphically through User Manager:**

1. Open the system settings and navigate to "Details" -> "About."

2. Click on "Users," and you may need to unlock the settings by entering the system security password.

3. Click on "Add User," and provide details such as username, password, and account type (Standard or Administrator).

4. The new user (e.g., JTP2) is successfully created.

#### 2. **Using the `useradd` Command:**

The `useradd` command is a command-line utility used to add or remove a user on a Linux server. It performs tasks like editing relevant files, creating a home directory, and setting ownerships and permissions.

```bash
sudo useradd JTP3
```

- The above command creates a user named JTP3.

```bash
sudo passwd JTP3
```

- Set the password for the newly created user (JTP3).

```bash
sudo useradd -m Demo
```

- The `-m` option forces the creation of a home directory for the user Demo.

```bash
sudo useradd -

m -d /Demo1 Demo1
```

- The `-d` option allows creating a user with a different home directory (/Demo1 in this case).

```bash
sudo useradd -d /home/test -e 2020-03-16 Demo2
```

- The `-e` option sets an expiry date for the user Demo2, making it auto-delete after 16 March 2020.

These commands demonstrate how to create users with various options, including specifying home directories and setting expiry dates. It's essential to understand the options available with the `useradd` command for effective user management on a Linux system.

### Linux `su` Commands

The `su` command in Linux allows users to run a shell as another user. Here are various examples demonstrating the usage of the `su` command:

#### 1. **Switching to Another User:**

```bash
su jtp
```

- The above command switches the user account from 'sssit' to 'jtp'.

#### 2. **Switching to Root:**

```bash
su root
```

- The `su` command can be used to switch to the root user when the root password is known.

#### 3. **Switching as Root to Another User:**

```bash
su - sssit
```

- When the root user wants to become another user, the `-` option is used. Password is required unless run by root.

#### 4. **Switching from Root to Another User Without Password:**

```bash
su - jtp
```

- The root user can become any existing user without knowing that user's password.

#### 5. **Switching with Different Shell Environment:**

```bash
su - jtp
su jtp
```

- The `-` option maintains the target user's shell environment. Without it, the current shell environment is kept.

#### 6. **Assuming Root by Default:**

```bash
su -
```

- If no username is mentioned, the `su` command assumes 'root' as the target user.

#### 7. **Running Program as Another User with `sudo`:**

```bash
sudo /usr/sbin/useradd -m akki
```

- The `sudo` command allows running programs with the credentials of another user.

#### 8. **Creating User with `sudo` Command:**

```bash
sudo /usr/sbin/useradd -m akki
```

- Users with sudo rights can create new users without becoming root or knowing the root password.

#### 9. **Becoming Root with `sudo su -`:**

```bash
sudo su -
```

- On systems without a set root password, users can use `sudo su -` to become root without the root password.

#### 10. **Becoming Root with `sudo su -` (Password Prompt):**

```bash
sudo su -
```

- The `sudo su -` command asks for the user's own password, not the root password.

These examples illustrate the versatility of the `su` command in Linux, allowing users to switch between accounts and perform various tasks with different privileges. The `sudo` command further extends this capability for users with appropriate permissions.

### Linux User Password

This chapter covers various aspects of managing user passwords in a Linux environment, including changing passwords, encryption, and additional security measures.

#### **1. Changing Passwords with `passwd` Command:**

```bash
passwd
```

- The `passwd` command allows users to change their password. Users must enter the old password twice before setting the new one.

- Users are warned about creating simple passwords. If unsuccessful after multiple attempts, the command fails.

- Root users can change passwords directly without entering the old password.

```bash
passwd <userName>
```

#### **2. Understanding the Shadow File:**

- Encrypted user passwords are stored in the `/etc/shadow` file, which is read-only and accessible only by root.

```bash
/etc/shadow
```

- The `/etc/shadow` file contains nine columns separated by colons, including username, encrypted password, and various password-related information.

#### **3. Encryption with `passwd` and `useradd`:**

- Passwords are stored in encrypted format using the `crypt` function. The `useradd -m` command creates a user with a home directory, and the password is set with the `passwd` command.

```bash
useradd -m <userName>
passwd <typePassword>
```

#### **4. Encryption with `openssl passwd`:**

- The `openssl passwd` command generates an encrypted password. The `-p` option of `useradd` can be used with the encrypted password.

```bash
useradd -m -p $(openssl passwd hunter2) <userName>
```

#### **5. Viewing Default Settings in `/etc/login.defs`:**

- The `/etc/login.defs` file contains default settings for password aging, length, and other configurations.

```bash
grep PASS /etc/login.defs
```

#### **6. Using `chage` to View Password Information:**

- The `chage` command provides information about password aging.

```bash
chage -l <userName>
```

#### **7. Disabling a Password:**

- Passwords starting with an exclamation mark (`!`) in `/etc/shadow` are considered disabled.

- Use `usermod -L` to disable a password.

```bash
usermod -L <userName>
```

- Use `usermod -U` to unlock an account.

```bash
usermod -U <userName>
```

These instructions cover password management, encryption, and security measures in a Linux environment, providing insights into user authentication and password-related configurations.

### Linux Groups

In Linux, users can be organized into different groups, providing a way to set permissions at the group level rather than individually. Group management can be done through graphical tools, command-line tools, or text editors like vi or vigr.

#### **1. Creating Groups with `groupadd` Command:**

```bash
groupadd <groupName>
```

- The `groupadd` command is used to create or add a group in the system.

    ```bash
    groupadd php
    groupadd java
    groupadd android
    groupadd spring
    ```

- In the `/etc/group` file, the first column represents the group name, the second is the group's encrypted password (which may be empty), the third is the group identification (GID), and the fourth is the list of members.

#### **2. Viewing Group Membership with `groups` Command:**

```bash
groups
```

- The `groups` command displays the groups to which the current user belongs.

#### **3. Modifying Group Membership with `usermod` Command:**

```bash
usermod -a -G <group> <userName>
```

- The `usermod` command allows the addition or removal of users from groups. The `-a` option appends the user to the group without removing them from other groups.

    ```bash
    usermod -a -G php akki
    usermod -a -G php abc
    usermod -a -G java jtp
    ```

#### **4. Changing Group Name with `groupmod` Command:**

```bash
#### **4. Changing Group Name with `groupmod` Command:**

```bash
groupmod -n <oldGroup> <newGroup>
```

- The `groupmod` command changes the name of an existing group.

    ```bash
    groupmod -n sql spring
    ```


#### **5. Deleting a Group with `groupdel` Command:**

```bash
groupdel <group>
```

- The `groupdel` command deletes a group permanently from the system.

    ```bash
    groupdel sql
    ```


#### **6. Controlling Group Membership with `gpasswd` Command:**

```bash
gpasswd -A <user> <group>
```

- The `gpasswd` command allows control of group membership and can pass membership to another user.

    ```bash
    gpasswd -A jtp java
    ```


#### **7. Removing Group Administrators with `gpasswd` Command:**

```bash
gpasswd -A "" <group>
```

- The `gpasswd` command can be used to remove all administrators from a group by setting an empty administrator list.

    ```bash
    gpasswd -A "" java
    ```