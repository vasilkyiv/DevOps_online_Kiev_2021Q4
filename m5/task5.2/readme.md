
[DevOps_online_Kiev_2021Q4 (MY GITHUB URL REPO)](https://github.com/vasilkyiv/DevOps_online_Kiev_2021Q4.git)
=======================================

[MODULE 05 NETWORKING](https://github.com/vasilkyiv/DevOps_online_Kiev_2021Q4/tree/main/m5) 
===========================================================================
 # [TASK_5.2 LinuxEssentials](https://github.com/vasilkyiv/DevOps_online_Kiev_2021Q4/tree/main/m5)

> 1) Analyze the structure of the ***/etc/passwd*** and ***/etc/group*** file, what fields are present in it, what ***users*** exist on the system? Specify several pseudo-users, how to define them?

[Файл /etc/passwd](https://www.ibm.com/docs/ru/aix/7.1?topic=passwords-using-etcpasswd-file)

     Традиционно в файле /etc/passwd сохраняются данные обо всех зарегистрированных пользователях, имеющих доступ к системе.

     Файл /etc/passwd содержит следующие записи, разделенные двоеточиями:
     Имя пользователя
     Зашифрованный пароль
     Цифровой идентификатор пользователя (UID)
     Цифровой идентификатор группы пользователя (GID)
     Полное имя пользователя (GECOS)
     Домашний каталог пользователя
     Оболочка входа в систему
     Ниже приведен пример файла /etc/passwd:

     В отличие от систем UNIX, система AIX хранит зашифрованные пароли не в файле /etc/passwd, а в файле /etc/security/passwd 1, который доступен для чтения только пользователю root. Значение в поле пароля в файле /etc/passwd в AIX просто указывает, задан ли пароль и заблокирована ли учетная запись.
     Прим.: начало изменения Если оболочка входа в систему не задана, вход в систему успешно выполняется, и применяется оболочка входа в систему Bourne для ssh. При получении доступа через команду su в качестве оболочки входа в систему применяется sh - жесткая ссылка на ksh.конец изменения
     Файл /etc/passwd принадлежит пользователю root и должен быть доступен для чтения всем пользователям, но для записи - только пользователю root, на что и указывают права доступа -rw-r--r--. Если для ИД пользователя установлен пароль, то в поле пароля будет находиться ! (восклицательный знак). Если у пользователя нет пароля, то в поле пароля будет указана звездочка (*). Зашифрованные пароли хранятся в файле /etc/security/passwd. Приведенный ниже пример содержит четыре последних записи файла /etc/security/passwd, соответствующего приведенному выше файлу /etc/passwd.

     guest:
          password = *
                                             
     nobody: 
          password = * 
                                             
     lpd: 
          password = * 

     paul: 
          password = eacVScDKri4s6 
          lastupdate = 1026394230 
          flags = ADMCHG                   

     У пользователя jdoe нет записи в файле /etc/security/passwd, так как для него не задан пароль в файле /etc/passwd.

     Соответствие файла /etc/passwd можно проверить с помощью командыpwdck. Команда pwdck проверяет указанную в файлах пользовательской базы данных информацию о паролях, просматривая определения всех или только указанных пользователей.

     На уровень выше:
     Пароль
     1 /etc/security/passwd

[Understanding /etc/group File](https://www.cyberciti.biz/faq/understanding-etcgroup-file/)

[/etc/group File](https://www.ibm.com/docs/en/aix/7.2?topic=files-etcgroup-file)

     Can you explain me the format of /etc/group user group file under Linux / UNIX-like operating systems?

     The /etc/group is a text file which defines the groups to which users belong under Linux and UNIX operating system. Under Unix / Linux multiple users can be categorized into groups. Unix file system permissions are organized into three classes, user, group, and others. The use of groups allows additional abilities to be delegated in an organized fashion, such as access to disks, printers, and other peripherals. This method, amongst others, also enables the Superuser to delegate some administrative tasks to normal users.

     Understanding the /etc/group File
     It stores group information or defines the user groups i.e. it defines the groups to which users belong. There is one entry per line, and each line has the following format (all fields are separated by a colon (:)

     Where,
     group_name: It is the name of group. If you run ls -l command, you will see this name printed in the group field.
     Password: Generally password is not used, hence it is empty/blank. It can store encrypted password. This is useful to implement privileged groups.
     Group ID (GID): Each user must be assigned a group ID. You can see this number in your /etc/passwd file.
     Group List: It is a list of user names of users who are members of the group. The user names, must be separated by commas.
     More About User Groups
     Users on Linux and UNIX systems are assigned to one or more groups for the following reasons:

     To share files or other resource with a small number of users
     Ease of user management
     Ease of user monitoring
     Group membership is perfect solution for large Linux (UNIX) installation.
     Group membership gives you or your user special access to files and directories or devices which are permitted to that group

     User tom is part of both ‘Web developers’ and ‘Sales’ group. So tom can access files belongs to both groups.

***Task: View Current Groups Settings***

     Type any one of the following command:
     $ less /etc/group

     OR use the more command:
     $ more /etc/group

     OR use the cat command:
     $ more /etc/group

***Task: Find Out the Groups a User Is In***

     Type the following groups command:
     $ groups {username}
     $ groups
     $ groups vivek

     Sample outputs:

     vivek : vivek adm dialout cdrom plugdev lpadmin netdev admin sambashare libvirtd
     Task: Print user / group Identity
     Use the id command to display information about the given user.

***Display only the group ID, enter:***
     Use the id command:
     $ id -g
     $ id -g user
     $ id -g vivek

     OR
     $ id -gn vivek



****************************
     cut -d: -f1 /etc/passwd
     sed 's/:.*//' /etc/passwd
     awk -F: '{print $1}' /etc/passwd

     cat /etc/passwd

[![*Report in screenshots*](shreenshot/1.png?raw=true)](https://github.com/vasilkyiv/DevOps_online_Kiev_2021Q4/tree/main/m3/task5.2)

[![*Report in screenshots*](shreenshot/2.png?raw=true)](https://github.com/vasilkyiv/DevOps_online_Kiev_2021Q4/tree/main/m3/task5.2)

2) What are the uid ranges? What is UID? How to define it?

[Everything Important You Need to Know About UID in Linux](https://linuxhandbook.com/uid-linux/)

[Команда id — найти UID пользователя или GID](https://www.oslogic.ru/knowledge/1071/komanda-id-najti-uid-polzovatelya-ili-gid/)

[id command in Linux with examples](https://www.geeksforgeeks.org/id-command-in-linux-with-examples/)

[What is UID in Linux, How to Find and Change it](https://www.fosslinux.com/39230/what-is-uid-in-linux-and-how-to-find-and-change-it.htm)

     A UID is an abbreviation of the word User Identifier, while GID is an abbreviation of the word Group Identifier. In this particular article, we will focus on the User Identifier (UID).

     A UID is a unique identification number assigned to every user present in a Linux system. The primary role of the UID number is to identify the user to the Linux kernel.

     It is used to manage the system resources that a user has access to in the system. It is one of the reasons for using a unique UID for every user available. Otherwise, if we have two users listed under one UID, then they could both have access to resources meant for the other.

***Where to find stored UID?***

     You can find the UID in the /etc/passwd file, which is the file that also stores all users registered in the system. To view the /etc/passwd file contents, run the cat command on the file, as shown below on the terminal.

     The /etc/passwd file holds all necessary attributes or basic information about every single user in the system. The data is displayed in seven columns, as listed below. These fields are separated by colons (:). This file also contains system-defined accounts and groups required for proper installation, running, and update of the system.

     Column 1 – Name
     Column 2 – Password – If the user has set a password on this field, then it is indicated with the letter (x).
     Column 3 – UID (User ID)
     Column 4 – GID (Group ID)
     Column 5 – Gecos – Contain general information about the user and can be empty.
     Column 6 – Home directory
     Column 7 – Shell – The path to the default shell for the user.

***Identify the UID***

     From the image above, the first user listed on the file is root. Root has overall control over every aspect of the system. The root user is assigned UID Zero (O) and GID (0). The other that follow are the system-defined accounts and groups.

     One more thing to note is that UID = 0 and GID = 0 are what give the root user all the powers in the system. If you wish to prove so, rename the root to something else like Example_User and create a new root user with a new UID and GID. You will realize that the Example_User will still have elevated privileges despite not having the username root.

     As you will also notice from the image, the system-defined accounts and groups that follow the root user have the UID 1,2,3,4,… and so on. It is because most Linux systems reserve the first 500 UID for system users. Other users added with the useradd command are assigned UID from 500. In Ubuntu and Fedora systems, a new user, even one created during the installation process, is given the UID from 1000 and above.

     You can see this in the image below, where we have two users. Fosslinux_admin and Tuts.

     The user “tuts” was created during the installation process and is assigned the UID 1000. The other user, “fosslinux,” was added later and was given the UID 1001.

***How to find the UID of a User, Group or an account***

     We have discussed how we can find a UID by displaying the contents of /etc/passwd file. There is a faster and easier way. We will use the id command.

     For example, to find the UID of user Fosslinux_admin and Tuts, execute the command below. You might be required to enter the root password.

     id fosslinux_admin
     id tuts

     We can also run the id command on other groups, as shown below. By executing the id command alone in the terminal, it will display the UID of the current logged in user. See the image below.

***How to change UID’s***

     Suppose you are managing a system with a lot of users, say an organization or institution. If a user left the company, you would probably need to assign the new user the UID of the employee who quit.

     Let’s first create a temporary user for this example. We will use the useradd command. You will need to have root privileges. See the command below.

***useradd example_user***

     By running the command id on user example_user, we can see that this new user has the UID 1003

     Now, let’s delete the Fosslinux_admin user who had the UID = 1001 and assign it to our new user. We will use the userdel command to remove the user.

     sudo userdel -r fosslinux_admin
     Once done that, we will assign our new user – example_user, the UID that belonged to fosslinux_admin. That is UID = 1001. We will do this using the usermod command.

     usermod -u 1001 exmple_user
     By running the id command on the user, for example, _user, we see that the user now has the UID = 1001.

     Now once you have the new user the UID of the old user, you will need to sync these with all other files that belonged to the old user. You can do this by executing the command below.

     find / -user [UID_of_old_user] -exec chown -h [new_user] {} \;
     e.g
     sudo find / -user 1001 -exec chown -h user_2 {} \;

***Create a New User With a Specific UID***

     Alternatively, we can create a new user with useradd command and assign the user a specific UID. See the syntax below.

     sudo useradd -u 1111 user_2
     By running the id command on user_2, we see that the user’s UID = 1111.

***Conclusion***

     That’s it! Everything you need to know about UID’s in Linux systems. If you think we missed a meaningful concept or need any clarification, don’t hesitate to let us know in the comment section below
********************************
[UID, GID, SID and RID](http://pig.made-it.com/uidgid.html)

     All in all a rough overview of what is used where can be created like this:
     IDs	Usage
     -2	nobody on AIX and Mac OS X
     0-99	Unix local users and groups, statically asigned
     99	Red Hat based system nobody user and group ID
     100-499	Unix local users and groups, dynamic
     529	Used as ID for nobody on some systems (and not used by Microsoft)
     32767	Historic reservation for nobody (have not find any use)
     60001	Nobody on IRIX and SunOS
     65530-65535	Unix nobody user and (no)group (Debian and nfsnobody RHEL)
     4294967292	Group-owner on Isilon BSD
     4294967293	Null user on Isilon BSD
     4294967294	Everyone on Isilon BSD
     4294967295	Nobody (32-bit)

#   Superuser (root uid = 0)
#   Generaluser ( uid 500-60000)
#   Pseudouser ( uid 1-499)


> 3) What is GID? How to define it?
[What does GID actually mean?](https://unix.stackexchange.com/questions/43744/what-does-gid-mean)

     Every process in a UNIX-like system, just like every file, has an owner (the user, either real or a system "pseudo-user", such as daemon, bin, man, etc) and a group owner. The group owner for a user's files is typically that user's primary group, and in a similar fashion, any processes you start are typically owned by your user ID and by your primary group ID.

     Sometimes, though, it is necessary to have elevated privileges to run certain commands, but it is not desirable to give full administrative rights. For example, the passwd command needs access to the system's shadow password file, so that it can update your password. Obviously, you don't want to give every user root privileges, just so they can reset their password - that would undoubtedly lead to chaos! Instead, there needs to be another way to temporarily grant elevated privileges to users to perform certain tasks. That is what the SETUID and SETGID bits are for. It is a way to tell the kernel to temporarily raise the user's privileges, for the duration of the marked command's execution. A SETUID binary will be executed with the privileges of the owner of the executable file (usually root), and a SETGID binary will be executed with the group privileges of the group owner of the executable file. In the case of the passwd command, which belongs to root and is SETUID, it allows normal users to directly affect the contents of the password file, in a controlled and predictable manner, by executing with root privileges. There are numerous other SETUID commands on UNIX-like systems (chsh, screen, ping, su, etc), all of which require elevated privileges to operate correctly. There are also a few SETGID programs, where the kernel temporarily changes the GID of the process, to allow access to logfiles, etc. sendmail is such a utility.

     The sticky bit serves a slightly different purpose. Its most common use is to ensure that only the user account that created a file may delete it. Think about the /tmp directory. It has very liberal permissions, which allow anyone to create files there. This is good, and allows users' processes to create temporary files (screen, ssh, etc, keep state information in /tmp). To protect a user's temp files, /tmp has the sticky bit set, so that only I can delete my files, and only you can delete yours. Of course, root can do anything, but we have to hope that the sysadmin isn't deranged!

     For normal files (that is, for non-executable files), there is little point in setting the SETUID/SETGID bits. SETGID on directories on some systems controls the default group owner for new files created in that directory.

[Interview Question | What is UID and GID in Linux | User Identifier | Group Identifier in Linux](https://www.linuxtopic.com/2019/07/uid-and-gid-in-linux.html)

     UID : User Identifier

     UID (User identifier)is a number that assigned by Linux to every user of the system. UIDs are stored in the /etc/passwd

     Value of UID

     0 to 99 value = System

     100 to 499 = Reserved for dynamic allocation

     500 / 1000 = Reserved for new users

     How to Check Default UID Value ?

     We can check default uid value by the command :
     cat /etc/login.defs | grep UID
     Output something like this

     UID_MIN 1000
     UID_MAX 60000
     #SYS_UID_MIN 100
     #SYS_UID_MAX 999


     What is UID and GID of root User ?

     root is the first user of the system so uid and gid is 0

     GID : Group Identifier

     All Groups of Linux are defined by GIDs (group IDs). GIDs are stored in the /etc/groups file. the first 100 GIDs are usually reserved for system use.


     Difference UID and GID


     UID

     UID full form is User Identifier, It Used to assign a Identity Number of User

***UID Store in /etc/passwd***

     GID

     GID full form is Group Identifier, It Used to assign a Identity Number of Group

***GID Store in /etc/group***

#   GUI 0 (zero) - root group
#   GUI 1-99 (zero) - system and apps group
#   GUI 100+ - users group

> 4) How to determine belonging of user to the specific group?

[How do I find out what groups I belong to under Linux operating systems?](https://www.cyberciti.biz/faq/linux-show-groups-for-user/)

***/etc/group***

     is a text file which defines the groups on the system. You can use the groups command to display group memberships for any user using the following syntax.

     $ groups
     $ groups root

     $ id -Gn
     $ id -Gn userName
     $ id -Gn vivek

     $ getent group userName
     $ getent group vivek

> 5) What are the commands for adding a user to the system? What are the basic
parameters required to create a user?

[How to Create Users in Linux (useradd Command)](https://linuxize.com/post/how-to-create-users-in-linux-using-the-useradd-command/)

### The general syntax for the useradd command is as follows:
     useradd [OPTIONS] USERNAME

###  How to Create a New User in Linux
     To create a new user account, invoke the useradd command followed by the name of the user.

     For example to create a new user named username you would run:

***sudo useradd username***
    
     When executed without any option, useradd creates a new user account using the default settings specified in the /etc/default/useradd file.

     The command adds an entry to the /etc/passwd, /etc/shadow, /etc/group and /etc/gshadow files.

###  To be able to log in as the newly created user, you need to set the user password. To do that run the passwd command followed by the username:

***sudo passwd username***

     You will be prompted to enter and confirm the password. Make sure you use a strong password.

     Changing password for user username.
     New password:
     Retype new password:
     passwd: all authentication tokens updated successfully.

### How to Add a New User and Create Home Directory
     On most Linux distributions, when creating a new user account with useradd, the user’s home directory is not created.

     Use the -m (--create-home) option to create the user home directory as /home/username:

***sudo useradd -m username***
     Copy
     The command above creates the new user’s home directory and copies files from /etc/skel directory to the user’s home directory. If you list the files in the /home/username directory, you will see the initialization files:

     ls -la /home/username/
     
     drwxr-xr-x 2 username username 4096 Dec 11 11:23 .
     drwxr-xr-x 4 root     root     4096 Dec 11 11:23 ..
     -rw-r--r-- 1 username username  220 Apr  4  2018 .bash_logout
     -rw-r--r-- 1 username username 3771 Apr  4  2018 .bashrc
     -rw-r--r-- 1 username username  807 Apr  4  2018 .profile

###  Creating a User with Specific Home Directory
     By default useradd creates the user’s home directory in /home. If you want to create the user’s home directory in other location, use the d (--home) option.

     Here is an example showing how to create a new user named username with a home directory of /opt/username:

***sudo useradd -m -d /opt/username username***

### Creating a User with Specific User ID
     In Linux and Unix-like operating systems, users are identified by unique UID and username.
     
     User identifier (UID) is a unique positive integer assigned by the Linux system to each user. The UID and other access control policies are used to determine the types of actions a user can perform on system resources.

     By default, when a new user is created, the system assigns the next available UID from the range of user IDs specified in the login.defs file.

***sudo useradd -u 1500 username***

     You can verify the user’s UID, using the id command:

***id -u username***
     
     1500

### Creating a User with Specific Group ID
     Linux groups are organization units that are used to organize and administer user accounts in Linux. The primary purpose of groups is to define a set of privileges such as reading, writing, or executing permission for a given resource that can be shared among the users within the group.

     When creating a new user, the default behavior of the useradd command is to create a group with the same name as the username, and same GID as UID.

     The -g (--gid) option allows you to create a user with a specific initial login group. You can specify either the group name or the GID number. The group name or GID must already exist.

     The following example shows how to create a new user named username and set the login group to users type:

***sudo useradd -g users username***

     To verify the user’s GID, use the id command:

***id -gn username***

     users

### Creating a User and Assign Multiple Groups
     There are two types of groups in Linux operating systems Primary group and Secondary (or supplementary) group. Each user can belong to exactly one primary group and zero or more secondary groups.

     You to specify a list of supplementary groups which the user will be a member of with the -G (--groups) option.

     The following command creates a new user named username with primary group users and secondary groups wheel and docker.

***sudo useradd -g users -G wheel,developers username***

You can check the user groups by typing

***id username***

     uid=1002(username) gid=100(users) groups=100(users),10(wheel),993(docker)

### Creating a User with Specific Login Shell
     By default, the new user’s login shell is set to the one specified in the /etc/default/useradd file. In some distributions the default shell is set to /bin/sh while in others it is set to /bin/bash.

     The -s (--shell) option allows you to specify the new user’s login shell.

     For example, to create a new user named username with /usr/bin/zsh as a login shell type:

***sudo useradd -s /usr/bin/zsh username***

     Check the user entry in the /etc/passwd file to verify the user’s login shell:

***grep username /etc/passwd***

     username:x :1001:1001::/home/username:/usr/bin/zsh

### Creating a User with Custom Comment
     The -c (--comment) option allows you to add a short description for the new user. Typically the user’s full name or the contact information are added as a comment.

     In the following example, we are creating a new user named username with text string Test User Account as a comment:

***sudo useradd -c "Test User Account" username***

     The comment is saved in /etc/passwd file:

***grep username /etc/passwd***

     username:x :1001:1001:Test User Account:/home/username:/bin/sh

     The comment field is also known as GECOS.

### Creating a User with an Expiry Date
     To define a time at which the new user accounts will expire, use the -e (--expiredate) option. This is useful for creating temporary accounts.

     The date must be specified using the YYYY-MM-DD format.

     For example to create a new user account named username with an expiry time set to January 22 2019 you would run:

***sudo useradd -e 2019-01-22 username***

     Use the chage command to verify the user account expiry date:

***sudo chage -l username***

     The output will look something like this:

     Last password change					: Dec 11, 2018
     Password expires					: never
     Password inactive					: never
     Account expires						: Jan 22, 2019
     Minimum number of days between password change		: 0
     Maximum number of days between password change		: 99999
     Number of days of warning before password expires	: 7

### Creating a System User
     There is no real technical difference between the system and regular (normal) users. Typically system users are created when installing the OS and new packages.

     Use the -r (--system) option to create a system user account. For example, to create a new system user named username you would run:

***sudo useradd -r username***

     System users are created with no expiry date. Their UIDs are chosen from the range of system user IDs specified in the login.defs file, which is different than the range used for normal users.

### Changing the Default useradd Values
     The default useradd options can be viewed and changed using the -D, --defaults option, or by manually editing the values in the /etc/default/useradd file.

     To view the current default options type:

***useradd -D***

     The output will look something like this:

     GROUP=100
     HOME=/home
     INACTIVE=-1
     EXPIRE=
     SHELL=/bin/sh
     SKEL=/etc/skel
     CREATE_MAIL_SPOOL=no
     
     Let’s say you want to change the default login shell from /bin/sh to /bin/bash. To do that, specify the new shell as shown below:

***sudo useradd -D -s /bin/bash***

     You can verify that the default shell value is changed by running the following command:

***sudo useradd -D | grep -i shell***

     SHELL=/bin/bash

### Conclusion
     We have shown you how to create new user accounts using the useradd command. The same instructions apply for any Linux distribution, including Ubuntu, CentOS, RHEL, Debian, Fedora, and Arch Linux.

     useradd is a low-level utility, Debian and Ubuntu users can use the friendlier adduser command instead.

> 6) How do I change the name (account name) of an existing user?

[How to Create Users in Linux (useradd Command)](https://www.cyberciti.biz/faq/howto-change-rename-user-name-id/)

     The syntax is as follows to rename by user name:
     usermod -l login-name old-name

     List all users in Linux system

     cat /etc/passwd
     grep -w '^username' /etc/passwd
     grep -w '^jerry' /etc/passwd
     cut -d: -f1 /etc/passwd


     id tom
     grep '^tom:' /etc/passwd
     grep 'tom' /etc/group
     groups tom

     ls -ld /home/tom/

     ps aux | grep tom
     ps -u tom

     # id tom
# usermod -l jerry tom
## Verify ###
# id tom
# id jerry
# ls -ld /home/tom

> 7) What is skell_dir? What is its structure?

[The /etc/skel Directory](http://www.linfo.org/etc_skel.html)

	
     The /etc/skel directory contains files and directories that are automatically copied over to a new user's home directory when such user is created by the useradd program.

     A home directory, also called a login directory, is the directory on Unix-like operating systems that serves as the repository for a user's personal files, directories and programs, including personal configuration files. It is also the directory that a user is first in after logging into the system. The /etc directory and its subdirectories contain the many important configuration files for the system.

     The useradd program is located in the /usr/sbin/ directory, and on most systems it is accessible only by the root (i.e., administrative) user. On some systems this program might be called adduser.

     /etc/skel allows a system administrator to create a default home directory for all new users on a computer or network and thus to make certain that all users begin with the same settings or environment.

     Several user configuration files are placed in /etc/skel by default when the operating system is installed. Typically they might include .bash_profile, .bashrc, .bash_logout, dircolors, .inputrc and .vimrc. The dots preceding the names of these files indicate that they are hidden files, i.e., files that are not normally visible in order to avoid visual clutter and help reduce the chances of accidental damage.

     The contents of /etc/skel can be viewed by using the ls (i.e., list) command with its -a option (which shows all files and directories, including hidden ones), i.e.,

***ls -a /etc/skel***

     The location of /etc/skel can be changed by editing the line that begins with SKEL= in the configuration file /etc/default/useradd. By default this line says SKEL=/etc/skel.

     It is usually better to keep /etc/skel as small as possible and put system-wide configuration items into global configuration files such as /etc/profile. This is because the latter makes it much easier to update existing users' files because its settings take effect as soon as the system is turned on and apply to new users and old uses alike.

     When a user is removed from the system by an administrator with the userdel command, that user's home directory, including the files and directories that have been copied into it from /etc/skel, remains intact.

     The name of the directory skel is derived from the word skeleton, because the files it contains form the basic structure for users' home directories.

> 8) How to remove a user from the system (including his mailbox)?

[How To: Linux Delete / Remove User Account Using userdel](https://www.cyberciti.biz/faq/linux-remove-user-command/)

     Linux delete user command syntax
     The syntax is as follows to remove a user account on Linux.
     userdel userName
     userdel [options] userName
     userdel -r userName

     userdel command examples
     Let us remove the user named vivek or account named vivek from the local Linux system / server / workstation, enter:
     # userdel vivek

     Next, delete the user’s home directory and mail spool pass the -r option to userdel for a user named ashish, enter:
     # userdel -r ashish

     The above command will remove all files along with the home directory itself and the user’s mail spool. Please note that files located in other file systems will have to be searched for and deleted manually. Pass the -f option for force removal of files, even if not owned by user:
***userdel*** -r -f tom

     To remove any SELinux user mapping for the user pass the -Z option:
***userdel*** -Z -r -f jerry

     Where,
     -f : Delete Linux user account with force removal of files
### -r : Remove Linux user account including home directory and mail spool
     -Z : Remove any SELinux user mapping for the user when deleting user from Linux
     A Note About /etc/login.defs File
     Default values are taken from the information provided in the /etc/login.defs file for RHEL (Red Hat) based distros. Debian and Ubuntu Linux based system use /etc/deluser.conf file:

     You can automate the entire procedure by writing a shell script (to remove any at/cron/print/file jobs etc), which is left as an exercise to the readers.
     See also:
     Help: Old Employees Accessing The Linux Server.
     /etc/passwd – The basic attributes of users.
     /etc/shadow – The basic attributes of users password.
     /etc/group – The basic attributes of groups.
     Man pages – ps(1)

> 9) What commands and keys should be used to lock and unlock a user account?

[How to Lock and Unlock User in Linux](https://linuxhandbook.com/lock-unlock-user/)

### 3 ways to lock and unlock user accounts in Linux

***Method 1: Lock and unlock users with passwd command***

     passwd -l user_name
     passwd -u user_name

***Method 2: Lock and unlock users with usermod command***

     usermod -L user_name
     usermod -U user_name

     usermod -L --expiredate 1970-01-02 user_name
     usermod -U --expiredate '' user_name

***Method 3: Lock and unlock users with chage command***

     chage -E 1 username
     chage -E -1 username

> 10) How to remove a user's password and provide him with a password-free login for subsequent password change?

[Linux: Delete user password command](https://www.cyberciti.biz/faq/linux-delete-user-password/)

### Command to delete user password under Linux
     
     See all GNU/Linux related FAQIam a new Linux user. I would like to disable a password for an account. How do I delete user Password under Linux operating system using command line option?

     All user passwords are stored in /etc/shadow file. The quick way to remove/delete a user password is pass --delete option to the passwd command. First, login in as a root user using sudo command/su command and type the following command:


     Type the following command to delete a user password:
***passwd --delete username***

     OR
***passwd -d username***

     OR
***sudo passwd -d sweta***

     Removing password for user sweta.
     passwd: Success

     Above command delete a user’s password (make it empty). This is a quick way to disable a password for an account. It will set the named account passwordless. User will not able to login. It is also a good idea to setup user shell to nologin to avoid security related problems:
***usermod -s /usr/sbin/nologin username***

     For example to delete password for user sweta, Type:
***passwd -d sweta***

***usermod -s /usr/sbin/nologin sweta***

### Verification
     Use the following chage command/grep command (feel free to replace the username sweta with actual username):
***chage -l sweta***

***grep sweta /etc/passwd***

***grep sweta /etc/shadow***

[Файл Sudoers, включите NOPASSWD для пользователя, все команды](https://qastack.ru/ubuntu/334318/sudoers-file-enable-nopasswd-for-user-all-commands)

man sudoers

***nicholsonjf    ALL=NOPASSWD: ALL***

     Добавленная вами строка была переопределена. От man sudoers:

     Когда несколько записей совпадают для пользователя, они применяются по порядку. При наличии нескольких совпадений используется последнее совпадение (которое не обязательно является наиболее конкретным совпадением).

     В вашем случае nicholsonjfбыл членом группы, sudoпоэтому для него эта строка применяется:

     %sudo   ALL=(ALL:ALL) ALL
     Если вы хотите переопределить записи, /etc/sudoers просто поместите новые записи после них.

     Новая запись должна выглядеть

     myuser ALL=(ALL) NOPASSWD: ALL для одного пользователя, или

     %sudo ALL=(ALL) NOPASSWD: ALL для группы.

> 11) Display the extended format of information about the directory, tell about the information columns displayed on the terminal.

[15 Basic ‘ls’ Command Examples in Linux)](https://www.tecmint.com/15-basic-ls-command-examples-in-linux/)

[Understanding Linux File Permissions)](https://linuxize.com/post/how-to-list-files-in-linux-using-the-ls-command/)


     ls -list
     ls -l

> 12) What access rights exist and for whom (i. e., describe the main roles)?
Briefly describe the acronym for access rights.

[Ls Command in Linux (List Files and Directories)](linux.com/training-tutorials/understanding-linux-file-permissions/)

     Basic File Permissions

     Permission Groups

     Each file and directory has three user based permission groups:

     owner – The Owner permissions apply only the owner of the file or directory, they will not impact the actions of other users.
     group – The Group permissions apply only to the group that has been assigned to the file or directory, they will not effect the actions of other users.
     all users – The All Users permissions apply to all other users on the system, this is the permission group that you want to watch the most.
     Permission Types
     Each file or directory has three basic permission types:

     read – The Read permission refers to a user’s capability to read the contents of the file.
     write – The Write permissions refer to a user’s capability to write or modify a file or directory.
     execute – The Execute permission affects a user’s capability to execute a file or view the contents of a directory.
     Viewing the Permissions

     You can view the permissions by checking the file or directory permissions in your favorite GUI File Manager (which I will not cover here) or by reviewing the output of the “ls -l” command while in the terminal and while working in the directory which contains the file or folder.

     The permission in the command line is displayed as: _rwxrwxrwx 1 owner:group

     User rights/Permissions
     The first character that I marked with an underscore is the special permission flag that can vary.
     The following set of three characters (rwx) is for the owner permissions.
     The second set of three characters (rwx) is for the Group permissions.
     The third set of three characters (rwx) is for the All Users permissions.
     Following that grouping since the integer/number displays the number of hardlinks to the file.
     The last piece is the Owner and Group assignment formatted as Owner:Group.
     Modifying the Permissions

     When in the command line, the permissions are edited by using the command chmod. You can assign the permissions explicitly or by using a binary reference as described below.

     Explicitly Defining Permissions
     To explicity define permissions you will need to reference the Permission Group and Permission Types.

     The Permission Groups used are:

     

     u – Owner
     g – Group
     o – Others
     a – All users
     The potential Assignment Operators are + (plus) and – (minus); these are used to tell the system whether to add or remove the specific permissions.

     The Permission Types that are used are:

     r – Read
     w – Write
     x – Execute
     So for an example, lets say I have a file named file1 that currently has the permissions set to _rw_rw_rw, which means that the owner, group and all users have read and write permission. Now we want to remove the read and write permissions from the all users group.

     To make this modification you would invoke the command: chmod a-rw file1
     To add the permissions above you would invoke the command: chmod a+rw file1

     As you can see, if you want to grant those permissions you would change the minus character to a plus to add those permissions.

     Using Binary References To Set Permissions
     Now that you understand the permissions groups and types this one should feel natural. To set the permission using binary references you must first understand that the input is done by entering three integers/numbers.

     A sample permission string would be chmod 640 file1, which means that the owner has read and write permissions, the group has read permissions, and all other user have no rights to the file.

     The first number represents the Owner permission; the second represents the Group permissions; and the last number represents the permissions for all other users. The numbers are a binary representation of the rwx string.

     r = 4
     w = 2
     x = 1
     You add the numbers to get the integer/number representing the permissions you wish to set. You will need to include the binary permissions for each of the three permission groups.

     So to set a file to permissions on file1 to read _rwxr_____, you would enter chmod 740 file1.

     Owners and Groups

     I have made several references to Owners and Groups above, but have not yet told you how to assign or change the Owner and Group assigned to a file or directory.

     You use the chown command to change owner and group assignments, the syntax is simplechown owner:group filename, so to change the owner of file1 to user1 and the group to family you would enter chown user1:family file1.

     Advanced Permissions

     The special permissions flag can be marked with any of the following:

     _ – no special permissions
     d – directory
     l– The file or directory is a symbolic link
     s – This indicated the setuid/setgid permissions. This is not set displayed in the special permission part of the permissions display, but is represented as a s in the read portion of the owner or group permissions.
     t – This indicates the sticky bit permissions. This is not set displayed in the special permission part of the permissions display, but is represented as a t in the executable portion of the all users permissions
     Setuid/Setgid Special Permissions

     The setuid/setguid permissions are used to tell the system to run an executable as the owner with the owner’s permissions.

     Be careful using setuid/setgid bits in permissions. If you incorrectly assign permissions to a file owned by root with the setuid/setgid bit set, then you can open your system to intrusion.

     You can only assign the setuid/setgid bit by explicitly defining permissions. The character for the setuid/setguid bit is s.

     So do set the setuid/setguid bit on file2.sh you would issue the command chmod g+s file2.sh.

     Sticky Bit Special Permissions

     The sticky bit can be very useful in shared environment because when it has been assigned to the permissions on a directory it sets it so only file owner can rename or delete the said file.

     You can only assign the sticky bit by explicitly defining permissions. The character for the sticky bit is t.

     To set the sticky bit on a directory named dir1 you would issue the command chmod +t dir1.

     When Permissions Are Important

     To some users of Mac- or Windows-based computers you don’t think about permissions, but those environments don’t focus so aggressively on user based rights on files unless you are in a corporate environment. But now you are running a Linux-based system and permission based security is simplified and can be easily used to restrict access as you please.

     So I will show you some documents and folders that you want to focus on and show you how the optimal permissions should be set.

     home directories– The users’ home directories are important because you do not want other users to be able to view and modify the files in another user’s documents of desktop. To remedy this you will want the directory to have the drwx______ (700) permissions, so lets say we want to enforce the correct permissions on the user user1’s home directory that can be done by issuing the command chmod 700 /home/user1.
     bootloader configuration files– If you decide to implement password to boot specific operating systems then you will want to remove read and write permissions from the configuration file from all users but root. To do you can change the permissions of the file to 700.
     system and daemon configuration files– It is very important to restrict rights to system and daemon configuration files to restrict users from editing the contents, it may not be advisable to restrict read permissions, but restricting write permissions is a must. In these cases it may be best to modify the rights to 644.
     firewall scripts – It may not always be necessary to block all users from reading the firewall file, but it is advisable to restrict the users from writing to the file. In this case the firewall script is run by the root user automatically on boot, so all other users need no rights, so you can assign the 700 permissions.

> 13) What is the sequence of defining the relationship between the file and the
user?

[HOW TO USE UNIX AND LINUX FILE PERMISSIONS)](https://its.unc.edu/research-computing/techdocs/how-to-use-unix-and-linux-file-permissions/)






