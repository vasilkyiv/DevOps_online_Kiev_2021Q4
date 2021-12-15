
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


