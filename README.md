# **Linux Lab 🔍**

**Documentation of linux <ins>(ubuntu)</ins> Commands**. In this file i will write the commands i find and learn in this personal lab. Its just a exercise for myself to learn Linux.📋
<br><br>

here is the list of labs:

[**Users management and file accessibility👥(First lab)**](#users-management-and-file-accessibilityfirst-lab) <br>

## **Users management and file accessibility👥(First lab)**

In this lab we are going to manage users in three group (normal users, admins, developers) and each file should assign to a group and owner, and also should limited users to only what they need to access.
<br><br>

### **User management👤**

---

Users and groups relatable commands

| Command                             | Description                                                          |
| ----------------------------------- | -------------------------------------------------------------------- |
| `getent passwd` & `cat /etc/passwd` | Display all the users with details                                   |
| `getent group sudo`                 | Display just the root users                                          |
| `compgen -u`                        | Display all users (no details)                                       |
| `useradd [username]`                | Adds user and use _sudo_                                             |
| `userdel [username]`                | Deletes user and use _sudo_                                          |
| `compgen -g`                        | Dispaly all groups (no details)                                      |
| `groupadd [groupname]`              | Adds group and use _sudo_                                            |
| `groupdel [groupname]`              | Deletes group and use _sudo_                                         |
| `id [username(optional)]`           | This command display summary of a user's identity as UID, GID etc... |

<br>

> [!NOTE]
> Ensures that the group is not the default group of any existing user when you are delete it!

<br><br>

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

  <br>

> [!tip]
> You can use command `cat /etc/group` to see all groups on system that a user can join.

<br><br>

### **User permissions🧑🏻‍💻👩🏻‍💻**

---

| Command | Description                                                                                                                                          |
| ------- | ---------------------------------------------------------------------------------------------------------------------------------------------------- |
| `ls -l` | List the files and directories with file permissions for your current location. The first character denotes whether an item is a file or a directory |
