# **Linux Lab 🔍**

**Documentation of linux <ins>(ubuntu)</ins> Commands**. In this file i will write the commands i find and learn in this personal lab. Its just a exercise for myself to learn Linux.📋
<br><br>

here is the list of labs:

[**Users management and file accessibility👥(First lab)**](#users-management-and-file-accessibilityfirst-lab) <br>

## **🫵🏻Basic commands**

For start we need to know some basic commands to work with linux terminal freely so In this section we are going to learn about some basic commands that will be handy in labs.

| Command                                          | Description                                                                                             |
| ------------------------------------------------ | ------------------------------------------------------------------------------------------------------- |
| `pwd`                                            | Displays path of the directory that you are currently in                                                |
| `cd [directory]`                                 | For navigate from one directory to another                                                              |
| `ls [options] [directory]`                       | Without any options or directory, `ls` will list all non-hidden files in the current directory.         |
| `mv [file or directory name] [target directory]` | Used for moving files or directories from one location to another                                       |
| `mv [old file name] [new file name]`             | Also we can use `mv` to rename a file or directory                                                      |
| `cp [source file] [target directory or file]`    | used for copying files from one location to other                                                       |
| `touch [file name]`                              | Creates empty files                                                                                     |
| `cat > [file name]`                              | Creates file and after executing the command, you can type your content                                 |
| `mkdir [directory name]`                         | Creates a directory                                                                                     |
| `rm [file name]`                                 | primary removes files                                                                                   |
| `rmdir [option] [directory name]`                | deletes empty directories and if you want to directories that contains files in option section add `-r` |

### **Directory Hierarchy (file system tree🌲)**

---

Understanding the directory hierarchy is crucial for efficient navigation and file management.

- **/:** Root directory, the top level of the file system.
- **/home:** Home directory contains personal directories for the users.
- **/bin:** This directly contains the executable files of many basic shell commands like ls, cp, cd etc
- **/sbin:** This is similar to the /bin directory. The only difference is that is contains the binaries that can only be run by root or a sudo user
- **/etc:** This directory contains the core configuration files of the system
- **/var:** Var, short for variable, is where programs store runtime information like system logging, user tracking, caches, and other files that system programs create and manage
- **/usr:** In this directory go all the executable files, libraries, source of most of the system programs
- **/lib:** Shared libraries. Libraries are basically codes that can be used by the executable binaries
- **/tmp:** This directory holds temporary files
- **/opt:** This directory is used for installing/storing the files of third-party applications that are not available from the distribution’s repository
- **/mnt:** This directory used by system administrators to manually mount a filesystem

## **Users management and file accessibility👥(First lab)**

### Description

---

In this lab we are going to manage users in three group (normal users, admins, developers) and each file should assign to a group and owner, and also should limited users to only what they need to access.
<br><br>

### **User management👤**

---

Users and groups relatable commands

| Command                             | Description                                                          |
| ----------------------------------- | -------------------------------------------------------------------- |
| `getent passwd` & `cat /etc/passwd` | Displays all the users with details                                  |
| `getent group sudo`                 | Displays just the root users                                         |
| `compgen -u`                        | Displays all users (no details)                                      |
| `sudo useradd [username]`           | Creates user                                                         |
| `sudo passwd [username]`            | Assign a password to user                                            |
| `sudo userdel [username]`           | Deletes user                                                         |
| `compgen -g`                        | Dispalys all groups (no details)                                     |
| `sudo groupadd [groupname]`         | Creates group                                                        |
| `sudo groupdel [groupname]`         | Deletes group                                                        |
| `id [username(optional)]`           | This command display summary of a user's identity as UID, GID etc... |

> [!NOTE]
> Ensures that the group is not the default group of any existing user when you are delete it!

<br>

### **Group memberships info🍸**

---

Here we explained some of the system groups that users can be joined.

- **User ID (uid):** A unique positive integer assigned to every user account. The first user created after installation is typically assigned 1000.

- **Real UID (ruid):** Identifies the user who originally started the process.

- **Admin watcher(adm):** Lets you read system logs like when you can check `/var/log/syslog` to see what went wrong. _it a permission for troubleshooting problems_

- **CD/DVD user(cdrom):** Lets you use CDs, DVDs, or Blu-ray drives. _Without this, your computer won't see inserted discs_

- **The boss(sudo):** Lets you run commands as administrator (root), When you type `sudo apt update`, this group allows it.

> [!WARNING]
> Be careful - members of this group can do anything, even break the system!

- **Old school internet user(dip):** Lets you use dial-up modems(older modems). _it's a leftover from the past_

- **USB plug-and-play(plugdev):** Automatically gives you access to USB drives when you plug them in. _Without this, you'd have to manually "mount" every USB drive using commands_

- **Regular user club(users):** The default group for normal human users. It's just a way to identify _normal users_ vs _system accounts_

- **Printer manager(lpadmin):** Lets you add, remove, and configure printers, Without this, you couldn't set up or manage printers

> [!tip]
> You can use command `cat /etc/group` to see all groups on system that a user can join.

<br>

### **User permissions🧑🏻‍💻👩🏻‍💻**

---

| Command                                      | Description                                                                                                                                          |
| -------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------- |
| `ls -l`                                      | List the files and directories with file permissions for your current location. The first character denotes whether an item is a file or a directory |
| `sudo usermod -a -G [group name] [username]` | Adds user to a group                                                                                                                                 |
| `sudo deluser [username] [groupname]`        | Deletes user from a group                                                                                                                            |
| `sudo -l -U [username]`                      | Displays what sudo commands user can run                                                                                                             |

> [!TIP]
> With this command `sudo useradd -d /home/customdir [username]` you can specify a custom home directory for the user.