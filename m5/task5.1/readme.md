
[DevOps_online_Kiev_2021Q4 (MY GITHUB URL REPO)](https://github.com/vasilkyiv/DevOps_online_Kiev_2021Q4.git)
=======================================

[MODULE 05 NETWORKING](https://github.com/vasilkyiv/DevOps_online_Kiev_2021Q4/tree/main/m5) 
===========================================================================
> # [TASK_5 LinuxEssentials](https://github.com/vasilkyiv/DevOps_online_Kiev_2021Q4/tree/main/m5)

> # [TASK_5.1 Part1](https://github.com/vasilkyiv/DevOps_online_Kiev_2021Q4/tree/main/m5)

> 1. Log in to the system as root.
     
     [sudoers](https://www.linux.com/training-tutorials/configuring-linux-sudoers-file/)
     sudo -s
     info sudo
     man sudo
     sudo --help

> 2. Use the passwd command to change the password. Examine the basic parameters of the command. What system file does it change *?

[passwd ](https://www.linuxtechi.com/10-passwd-command-examples-in-linux/)

     Syntax : 
     # passwd {options} {user_name}
     man passwd
     info passwd
     passwd --help

     passwd -Sa
     cat /etc/passwd
     cat /etc/shadow
     cat /etc/pam.d/passwd

> 3) Determine the users registered in the system, as well as what commands they execute. What additional information can be gleaned from the command execution?

# [users ](https://linuxize.com/post/how-to-list-users-in-linux/)

     getent passwd | awk -F: '{ print $1}'

     cut -d : -f 1 /etc/group

     grep -E '^UID_MIN|^UID_MAX' /etc/login.defs

> 4) Change personal information about yourself.

# [chenge user info ](https://tldp.org/LDP/GNU-Linux-Tools-Summary/html/c6239.htm)
     
     chfn --help
     infog chfn
     man chfn
     chfn username

> 5) Become familiar with the Linux help system and the man and info commands. Get help on the previously discussed commands, define and describe any two keys for these commands. Give examples.

# [ info command ](https://www.geeksforgeeks.org/info-command-in-linux-with-examples/)

     info info
     info man
     info --help
     Syntax:

     info [OPTION]... [MENU-ITEM...]
     Options:

     -a, –all: It use all matching manuals.
     -k, –apropos=STRING: It look up STRING in all indices of all manuals.
     -d, –directory=DIR: It add DIR to INFOPATH.
     -f, –file=MANUAL: It specify Info manual to visit.
     -h, –help: It display this help and exit.
     -n, –node=NODENAME: It specify nodes in first visited Info file.
     -o, –output=FILE: It output selected nodes to FILE.
     -O, –show-options, –usage: It go to command-line options node.
     -v, –variable VAR=VALUE: It assign VALUE to Info variable VAR.
     –version: It display version information and exit.
     -w, –where, –location: It print physical location of Info file.

# [ man command ](https://www.geeksforgeeks.org/man-command-in-linux-with-examples/)

     man [COMMAND NAME]
     man man 

# [ help command ](https://www.geeksforgeeks.org/help-command-in-linux-with-examples/)
     
     help help
     // syntax for help command

     $help [-dms] [pattern ...]

> 6) Explore the more and less commands using the help system. View the contents of files .bash* using commands.

# [ less command ](https://www.geeksforgeeks.org/less-command-linux-examples/)

     Syntax : 
     less filename

     dmesg | less

# [ more command ](https://www.geeksforgeeks.org/more-command-in-linux-with-examples/)

     more -d sample.txt
     more -f sample.txt
     more -p sample.txt
     more -c sample.txt
     more -s sample.txt
     more -u sample.txt
     more +/reset sample.txt
     more +30 sample.txt
     cat a.txt | more
     
