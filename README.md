# **Linux Lab 🔍**

**Documentation of linux <ins>(ubuntu)</ins> Commands**. In this file i will write the commands i find and learn in this personal lab. Its just a exercise for myself to learn Linux.📋
<br><br>

here is the list of labs:

[**Users management and file accessibility👥(First lab)**](#users-management-and-file-accessibilityfirst-lab) <br>

## **🫵🏻Basic**

For start we need to know some basic commands to work with linux terminal freely so In this section we are going to learn about some basic commands that will be handy in labs.

> [!TIP]
> To see what version of linux your using you can use `cat /etc/os-release` command.

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

### **File editing📝**

---

Here we are going to explain two _text editor_ in linux, _Vim_ and _Nano_.

### Nano

To use the _nano_ command in Linux, you simply type _nano_ followed by the filename (`nano [options] [file name]`). This command opens the specified file in the nano text editor. If the file doesn’t exist, nano will create it for you.  
 Once you’ve opened a file, you can start editing right away and to save your changes, you press _Ctrl+O_, then Enter. This will write your changes to disk and for exit nano, you press _Ctrl+X_. For more shortcuts and information you can check [Essential Nano keyboard shortcuts](https://itsfoss.com/nano-editor-guide/).

> [!tip]
> To create backup of the current file before saving changes, you can use `nano -B [file name]` command.

### Vim

_Vim_ is more advance than nano and a little hard to learn. Learning _vim_ will be painful at first. It will take time and i recommend to escape👍🏻and here is [Vim Cheat Sheet](https://vim.rtorr.com/).  
 To see if it is installed you can use `command -v vim` command.  
 To install vim you can use `sudo apt install vim-nox` command.  
 When you start first are in _Normal mode_, you can not _edit_ file in this mode, you can't type anything.  
 For typing and editing you need to enter _Insert mode_. If you press `i` or press _shift+a_ you can enter _Insert mode_. If you want to exit Normal mode you press Esc. and for leaving vim you type `:q` and if you want exit without saving changes you can type `:q!`.  
 `:` give us _command mode_ and if you press Esc you come back to _Normal mode_.  
 For saving file you can use `:w` and for saving and quit you can use `:wq`.

> [!TIP]
> For undoing first you need to go on _Normal mode_ and then press `u`

#### Normal mode

- You can delete character in _Normal mode_ by pressing `x` and by pressing `dd` you can delete an entire line and paste it with `p`.
- In this mode move around by `h`, `j`, `k` and `l` keys. `h` to the _left_, `l` to the _right_, `j` to the _down_ and `k` to the _up_.
- If you press `gg` you will go at the beginning of the file and if you press `shift + g` will go at the end of the file.

#### Command mode

- If you want to combine two file in one, first open first file and then go in _Command mode_ and write `:r [path of the second file]`
- By typing `:! [linux command]` you can use linux commands and after execution press _Enter_ to come back to vim or type another command.
- To open second file on vim you can use `:e [file name]` and to switch between files you can use `:bn` (buffer next) or `:bp` (buffer pervious).
- If you don't want to switch to the new buffer you can use this `:badd [file name]` instead.
- To open an empty buffer use `:enew` (edit new) to open an empty buffer. for saving it use `:w [file name]` and then you can navigate between open files including this file.
- If you want to replace some word with something els you use this `:%s/[the word you want to change]/[the word you want to change to]/g`.
- you can delete a buffer by typing `:bd`.
- For having two buffer open on screen at the same time you can use `:split [second file name]` and if you want to navigate between files press `ctrl + ww`.
- For a vertical split use `:vsplit [second file name]` instead.
- To open vim split from start in terminal use `vim -o [first file name] [second file name]` for horizontal split and use `vim -O [first file name] [second file name]` for vertical split.
- To get line number you can use `:set number` and for vanishing numbers `:set nonumber`.

#### Visual mode

- By pressing `v` you can enter _Visual mode_.
- In _Visual mode_ you can highlight the text you want to copy and then press `y` for yanking and then in _Normal mode_ if you press `p` it will paste the text.
- In this mode you can _alphabetized_ texts by highlighting the text you want and then press `:` then type `sort ui`.

> [!TIP]
> In your home directory you can create a configuration file for vim with `vim .vimrc` and then write the rules and commands you want.

### **Shells information**

Run the command `echo $SHELL` to know the Linux shell type that your system is using.  
you can. You have to look into the file named /etc/shells to see all the installed Linux shells in your system which you can do using the `cat /etc/shells` command.  
You can use the `chsh -s [path of shell]` command and change the default Linux shell.

---

### Command Path

The command path is a variable that is used by the shell to determine where to look for the executable files to run. with `echo $PATH` command you can see all the directories that are currently configured in your system’s $PATH.

- #### Temporarily add Directory to PATH Variable

  Adding a directory to the PATH variable will enable you to call on your program or script from anywhere in the system, without needing to specify the path to where you’ve stored it.  
  To Temporarily add a directory to $PATH use `export PATH="[file path]: $PATH"`

- #### Permanently add a directory to $PATH

  To add a directory to $PATH permanently, we’ll need to edit the `.bashrc`file of the user you want to change. Use nano or your favorite text editor to open the file, stored in the home directory(`nano ~/.bashrc`) and at the end of this file, put your new directory that you wish to permanently add to $PATH(`export PATH="[file path]: $PATH"`).  
  Save your changes and exit the file. Afterwards, execute the following command to make the changes take effect in your current session. Alternative, you can log out or reboot the system(`source ~/.bashrc`).

- #### Remove directory from $PATH
  You can remove a directory from PATH by editing the appropriate file and removing the undesirable directory. The directories for PATH can be configured in the `~/.bashrc` file (per user basis) or the `/etc/environment` (system wide variables).

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
