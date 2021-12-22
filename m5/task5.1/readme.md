
[DevOps_online_Kiev_2021Q4 (MY GITHUB URL REPO)](https://github.com/vasilkyiv/DevOps_online_Kiev_2021Q4.git)
=======================================

[MODULE 05 LinuxEssentials](https://github.com/vasilkyiv/DevOps_online_Kiev_2021Q4/tree/main/m5) 
===========================================================================
 # [TASK_5.1 LinuxEssentials](https://github.com/vasilkyiv/DevOps_online_Kiev_2021Q4/tree/main/m5)

# [Part 1](https://github.com/vasilkyiv/DevOps_online_Kiev_2021Q4/tree/main/m5)

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

> 7) What is skell_dir? What is its structure?

# [ skel is derived from the skeleton because it contains basic structure of home directory ](https://sauravomar01.medium.com/etc-skel-directory-in-linux-dcefc0278f49)

# [ What is the /etc/skel directory in Linux? ](https://www.linuxgurus.in/linux-etc-skel-directory/)
     
     - What is the /etc/skel directory in Linux?
     SAHIL HASANWHAT IS
     - In this article, you will learn about What is the /etc/skel directory in Linux?

     Note: “skeleton” directory is define in /etc/default/useradd file

     Below you can see the picture of /etc/default/useradd file which defines the skel directory. You can change the default location /etc/skel to any other location.

     cat /etc/default/useradd

     # useradd defaults file
     GROUP=100
     HOME=/home
     INACTIVE=-1
     EXPIRE=
     SHELL=/bin/bash
     SKEL=/etc/skel
     CREATE_MAIL_SPOOL=yes

     Changing the default user home location 

     vim /etc/default/useradd

     And change the default value from /home to the consider home location. For example, if you want to change it /data/userhome then you just need to type.

     HOME=/data/userhome

     When you create any new users, then the new users’ home will be /data/userhome.

     Default permission of /etc/skel directory
     The default permission of /etc/skel directory is drwxr-xr-x.

     It is not recommended to change the permission of the skel directory or its contents. Changing the permission may break some of the programs because in the skel directory some profiles need the permission of ‘read’ and trying to permit it to execute will cause some programs/profiles to work unexpectedly.

     Conclusion
     In this tutorial, we learn about the /etc/skel directory in Linux. I hope, you understand, but if you have any questions, you can ask in the comment section.

     You can read about

     The /etc/skel directory contains files and directories that are automatically copied over to a new user’s home directory when such a user is created by the useradd program. skel is derived from the “skeleton”. Below is shown a picture.

     - skel is derived from the skeleton because it contains basic structure of home directory
     - The /etc/skel directory contains files and directories that are automatically copied over to a new user’s when it is created from useradd command.
     - This will ensure that all the users gets same intial settings and environment.

     The location of /etc/skel can be changed by editing the line that begins with SKEL= in the configuration file /etc/default/useradd. By default this line says SKEL=/etc/skel.

     - Default Permission of the /etc/skel directory is drwxr-xr-x.
     - It is not recommended to change the permission of skel directory or its contents. skel directory there are some profiles that needs the permission of read and trying to give it permission of execute will cause some programs/profiles to stop work or not works as expected.
     
     ls -la /etc/skel/

     root@ict-net-adm:/# ls -la /etc/skel/
     total 20
     drwxr-xr-x  2 root root 4096 Apr 23  2020 .
     drwxr-xr-x 95 root root 4096 Dec  7 16:42 ..
     -rw-r--r--  1 root root  220 Feb 25  2020 .bash_logout
     -rw-r--r--  1 root root 3771 Feb 25  2020 .bashrc
     -rw-r--r--  1 root root  807 Feb 25  2020 .profile
     root@ict-net-adm:/#

> 7) * Describe in plans that you are working on laboratory work 1. Tip: You should read the documentation for the finger command.
     
     man finger
     info finger

> 8) * List the contents of the home directory using the ls command, define its files and directories. Hint: Use the help system to familiarize yourself with the ls command.

     ls --help
     info ls
     man ls

     ls -alh --group-directories-first ~
     ls -lah ~
     ls -la ~

[![*Report in screenshots*](shreenshot/1.png?raw=true)](https://github.com/vasilkyiv/DevOps_online_Kiev_2021Q4/tree/main/m3/task5.1)

# [Part 2](https://github.com/vasilkyiv/DevOps_online_Kiev_2021Q4/tree/main/m5)

1) Examine the tree command. Master the technique of applying a template, for example, display all files that contain a character c, or files that contain a specific sequence of characters. List subdirectories of the root directory up to and including the second nesting level.

# [ Linux see directory tree structure using tree command ](https://www.cyberciti.biz/faq/linux-show-directory-structure-command-line/)

     Syntax – Linux see directory tree structure
     The syntax is:

     tree
     tree /path/to/directory
     tree [options]
     tree [options] /path/to/directory

     To list contents of /etc in a tree-like format:
     
     tree /etc

     The -a option should be passed to see all files. By default tree does not print hidden files (those beginning with a dot ‘.’). In no event does tree print the file system constructs ‘.’ (current directory) and ‘..’ (previous directory).:
     
     tree -a

     To list directories only, run:
     
     tree -d

     Pass the -C option to see colorized output, using built-in color defaults:
     
     tree -C

          ------- Listing options -------
     -a            All files are listed.
     -d            List directories only.
     -l            Follow symbolic links like directories.
     -f            Print the full path prefix for each file.
     -x            Stay on current filesystem only.
     -L level      Descend only level directories deep.
     -R            Rerun tree when max dir level reached.
     -P pattern    List only those files that match the pattern given.
     -I pattern    Do not list files that match the given pattern.
     --ignore-case Ignore case when pattern matching.
     --matchdirs   Include directory names in -P pattern matching.
     --noreport    Turn off file/directory count at end of tree listing.
     --charset X   Use charset X for terminal/HTML and indentation line output.
     --filelimit # Do not descend dirs with more than # files in them.
     --timefmt <f> Print and format time according to the format <f>.
     -o filename   Output to file instead of stdout.
     -------- File options ---------
     -q            Print non-printable characters as '?'.
     -N            Print non-printable characters as is.
     -Q            Quote filenames with double quotes.
     -p            Print the protections for each file.
     -u            Displays file owner or UID number.
     -g            Displays file group owner or GID number.
     -s            Print the size in bytes of each file.
     -h            Print the size in a more human readable way.
     --si          Like -h, but use in SI units (powers of 1000).
     -D            Print the date of last modification or (-c) status change.
     -F            Appends '/', '=', '*', '@', '|' or '>' as per ls -F.
     --inodes      Print inode number of each file.
     --device      Print device ID number to which each file belongs.
     ------- Sorting options -------
     -v            Sort files alphanumerically by version.
     -t            Sort files by last modification time.
     -c            Sort files by last status change time.
     -U            Leave files unsorted.
     -r            Reverse the order of the sort.
     --dirsfirst   List directories before files (-U disables).
     --sort X      Select sort: name,version,size,mtime,ctime.
     ------- Graphics options ------
     -i            Don't print indentation lines.
     -A            Print ANSI lines graphic indentation lines.
     -S            Print with CP437 (console) graphics indentation lines.
     -n            Turn colorization off always (-C overrides).
     -C            Turn colorization on always.
     ------- XML/HTML/JSON options -------
     -X            Prints out an XML representation of the tree.
     -J            Prints out an JSON representation of the tree.
     -H baseHREF   Prints out HTML format with baseHREF as top directory.
     -T string     Replace the default HTML title and H1 header with string.
     --nolinks     Turn off hyperlinks in HTML output.
     ---- Miscellaneous options ----
     --version     Print version and exit.
     --help        Print usage and this help message and exit.
     --            Options processing terminator.

> 2) What command can be used to determine the type of file (for example, text or binary)? Give an example.

# [ file command in Linux with examples ](https://www.geeksforgeeks.org/file-command-in-linux-with-examples/)

     Syntax:

     file [option] [filename]
     
     file email.py
     file name.jpeg
     file Invoice.pdf
     file exam.ods
     file videosong.mp4

> 3) Master the skills of navigating the file system using relative and absolute paths. How can you go back to your home directory from anywhere in the filesystem?

# [ Navigating your filesystem in the Linux terminal ](https://www.redhat.com/sysadmin/navigating-filesystem-linux-terminal)

     You can also always return to your home directory instantly using this shortcut:

     $ cd ~
     $ pwd
     /home/seth

> 4) Become familiar with the various options for the ls command. Give examples of listing directories using different keys. Explain the information displayed on the terminal using the -l and -a switches.

# [ 15 Basic ‘ls’ Command Examples in Linux ](https://www.tecmint.com/15-basic-ls-command-examples-in-linux/)

     info ls
     man ls
     ls --help

     1. List Files and Directories in Linux
     Running ls command with no option list files and directories in a bare format where we won’t be able to view details like file types, size, modified date and time, permission and links, etc.
     2. Long Listing of Files in Linux
     Here, ls -l (-l is a character, not one) shows file or directory, size, modified date and time, file or folder name and owner of the file, and its permission.
     3. View Hidden Files in Linux
     List all files including hidden files starting with ‘.‘.
     4. List Files with Human Readable Format
     With a combination of -lh option, shows sizes in a human-readable format.
     5. List Files and Directories with ‘/’ Character at the End
     Using the -F option with the ls command will add the '/' character at the end of each directory.
     6. List Files in Reverse Order in Linux
     The following command with the ls -r option display files and directories in reverse order.
     7. Recursively list Sub-Directories in Linux
     ls -R option will list very long listing directory trees. See an example of the output of the command.
     8. List Files and Directories in Reverse Order in Linux
     A combination of -ltr will show the latest modification file or directory date as last.
     9. Sort Files by File Size in Linux
     With a combination of -lS displays file size in order, will display big in size first.
     10. Display Inode number of File or Directory
     We can see some numbers printed before the file/directory name. With -i options list file/directory with an inode number.
     11. Shows Version of ls Command
     Check the version of the ls command.
     12. Show ls Command Help Page
     The help page of ls command with their option.
     13. List Directory Information in Linux
     With ls -l command list files under directory /tmp. Wherein with -ld parameters displays information of /tmp directory.
     14. Display UID and GID of Files
     To display UID and GID of files and directories. use option -n with ls command.
     15. ls command and its Aliases
     We have made an alias for ls command, when we execute ls command it’ll take the -l option by default and display a long listing as mentioned earlier.

> 5) Perform the following sequence of operations: 
- create a subdirectory in the home directory; 
- in this subdirectory create a file containing information about directories located in the root directory (using I/O redirection operations);
- view the created file;
- copy the created file to your home directory using relative and absolute addressing.
- delete the previously created subdirectory with the file requesting removal;
- delete the file copied to the home directory.

          mkdir ~/task5.1_part2_p5
         tree -ld /etc > ~/task5.1_part2_p5/info_ebaut_directory
        less ~/task5.1_part2_p5/info_ebaut_directory
         cp ~/task5.1_part2_p5/info_ebaut_directory home/ovo/
          cp /root/task5.1_part2_p5/info_ebaut_directory /home/ovo/
         rm -r ~/task5.1_part2_p5/
          rm /home/ovo/info_ebaut_directory

> 6) Perform the following sequence of operations:

# [ What is the difference between a symbolic link and a hard link?](https://stackoverflow.com/questions/185899/what-is-the-difference-between-a-symbolic-link-and-a-hard-link)

- create a subdirectory test in the home directory;
- copy the .bash_history file to this directory while changing its name to labwork2;
- create a hard and soft link to the labwork2 file in the test subdirectory;
- how to define soft and hard link, what do these
concepts;
- change the data by opening a symbolic link. What changes will happen and why
- rename the hard link file to hard_lnk_labwork2;
- rename the soft link file to symb_lnk_labwork2 file;
- then delete the labwork2. What changes have occurred and why?
     
          mkdir ~/test
          cp ~/.bash_history ~/test/labwork2
          ln -P labwork2 PhisicalLink
          ln -s labwork2 SymboliclLink

# [Hard links and soft links in Linux explained](https://www.redhat.com/sysadmin/linking-linux-explained)

Files that are ***hard-linked*** together share the same ***inode*** number.

     [tcarrigan@server demo]$ ls -li link_test /tmp/link_new 
     2730074 -rw-rw-r--. 2 tcarrigan tcarrigan 12 Aug 29 14:27 link_test
     2730074 -rw-rw-r--. 2 tcarrigan tcarrigan 12 Aug 29 14:27 /tmp/link_new

 >    -  A hard link always points a filename to data on a storage device.
 >    -  A soft link always points a filename to another filename, which then points to information on a storage device.

     mv PhisicalLink hard_lnk_labwork2

> 7) Using the locate utility, find all files that contain the squid and traceroute
sequence.

# [locate command in Linux with Examples](https://www.geeksforgeeks.org/locate-command-in-linux-with-examples/)

     man locate
     info locate
     locate --help

     Syntax:

     locate [OPTION]... PATTERN...
     Exit Status: This command will exit with status 0 if any specified match found. If no match founds or a fatal error encountered, then it will exit with status 1.

     Options:

     -b, –basename : Match only the base name against the specified patterns, which is the opposite of –wholename.
     -c, –count : Instead of writing file names on standard output, write the number of matching entries only.
     -d, –database DBPATH : Replace the default database with DBPATH. DBPATH is a : (colon) separated list of database file names. If more than one –database option is specified, the resulting path is a concatenation of the separate paths. An empty database file name is replaced by the default database. A database file name – refers to the standard input. Note that a database can be read from the standard input only once.
     -e, –existing : Print only entries that refer to files existing at the time locate is run.
     -L, –follow : When checking whether files exist (if the –existing option is specified), follow trailing symbolic links. This causes bro ken symbolic links to be omitted from the output. This option is the default behavior. The opposite can be specified using –nofollow.
     -h, –help : Write a summary of the available options to standard output and exit successfully.
     -i, –ignore-case : Ignore case distinctions when matching patterns.
     -l, –limit, -n LIMIT : Exit successfully after finding LIMIT entries. If the –count option is specified, the resulting count is also limited to LIMIT.
     -m, –mmap : Ignored, but included for compatibility with BSD and GNU locate.
     -P, –nofollow, -H : When checking whether files exist (if the –existing option is specified), do not follow trailing symbolic links. This causes broken symbolic links to be reported like other files.
     This option is the opposite of –follow.

     -0, –null : Separate the entries on output using the ASCII NUL character instead of writing each entry on a separate line. This option is designed for interoperability with the –null option of GNU xargs.
     -S, –statistics : Write statistics about each read database to standard output instead of searching for files and exit successfully.
     -q, –quiet : Write no messages about errors encountered while reading and processing databases.
     -r, –regexp REGEXP : Search for a basic regexp REGEXP. No PATTERNs are allowed if this option is used, but this option can be specified multiple times.
     –regex : Interpret all PATTERNs as extended regexps.
     -s, –stdio : Ignored, for compatibility with BSD and GNU locate.
     -V, –version : Write information about the version and license of locate on standard output and exit successfully.
     -w, –wholename : Match only the whole path name against the specified patterns. This option is the default behavior. The opposite can be specified using –basename.

     apt install mlocate-y
     updatedb

     locate -A squid
     locate -A traceroute

     locate -i -0 *sample.txt*
     locate -i *SAMPLE.txt*
     locate -c [.txt]*
     locate "*.html" -n 20
     locate sample.txt 

[![*Report in screenshots*](shreenshot/2.png?raw=true)](https://github.com/vasilkyiv/DevOps_online_Kiev_2021Q4/tree/main/m3/task5.1)

> 8) Determine which partitions are mounted in the system, as well as the types of
these partitions.

[Which partition is mounted to where? [duplicate])](https://unix.stackexchange.com/questions/192273/which-partition-is-mounted-to-where/192279)

[lsblk Command to list block device on Linux)](https://www.cyberciti.biz/faq/linux-list-disk-partitions-command/)

[19. Partitions, File Systems, Formatting, Mounting](https://rute.gerdesas.com/node22.html)
     
     man fdisk
     man lsblk
     man sfdisk
     man parted

     lsblk
     lsblk /dev/DEVICE
     lsblk /dev/sda
     lsblk -l
     lsblk -d | grep disk

     lsblk -o NAME,FSTYPE,SIZE,MOUNTPOINT

     hwinfo | more
     hwinfo --block | more
     hwinfo --block --short
     inxi -P
     inxi -p | more

     lsblk -f -m | grep ext4
     lsblk -f -m
     blkid

> 9) Count the number of lines containing a given sequence of characters in a given
file.

[How to Count lines in a file in UNIX/Linux](https://www.thegeekdiary.com/how-to-count-lines-in-a-file-in-unix-linux/)

     Using “wc -l”

     wc -l [filename]
     wc -l file01.txt
     wc -l < file01.txt
     cat file01.txt | wc -l

     Using awk
     awk 'END{print NR}' [filename]
     awk 'END{print NR}' file01.txt

     Using sed
     sed -n '$=' [filename]
     sed -n '$=' file01.txt

     Using grep
     grep -c ".*" [filename]
     grep -c ".*" file01.txt
     grep -Hc ".*" [filename]
     grep -c ^ file01.txt
     grep -Hc ".*" file01.txt

     Some more commands
     nl [filename]
     nl file01.txt
     nl file01.txt | tail -1 | awk '{print $1}'
     cat -n file01.txt
     cat -n file01.txt | tail -1 | awk '{print $1}'
     perl -lne 'END { print $. }' file01.txt

> 10) Using the ***find*** command, find all files in the ***/etc*** directory containing the
***host*** character sequence.

[find Command](https://www.ibm.com/docs/en/aix/7.1?topic=f-find-command)

[find command in Linux with examples](https://www.geeksforgeeks.org/find-command-in-linux-with-examples/)

[35 Practical Examples of Linux Find Command](https://www.tecmint.com/35-practical-examples-of-linux-find-command/)
     
          find . -name tecmint.txt
          find /home -name tecmint.txt
          find /home -iname tecmint.txt
          find / -type d -name Tecmint
          find . -type f -name tecmint.php
          find . -type f -name "*.php"
          find . -type f -perm 0777 -print
          find / -type f ! -perm 777
          find / -perm 2644
          find / -perm 1551
          find / -perm /u=s
          find / -perm /g=s
          find / -perm /u=r
          find / -perm /a=x
          find / -type f -perm 0777 -print -exec chmod 644 {} \;
          find / -type d -perm 777 -print -exec chmod 755 {} \;
          find . -type f -name "tecmint.txt" -exec rm -f {} \;
          find . -type f -name "*.txt" -exec rm -f {} \;
               OR
          find . -type f -name "*.mp3" -exec rm -f {} \;
          find /tmp -type f -empty
          find /tmp -type d -empty
          find /tmp -type f -name ".*"
          find / -user root -name tecmint.txt
          find /home -user tecmint
          find /home -group developer
          find /home -user tecmint -iname "*.txt"
          find / -mtime 50
          find / -atime 50
          find / -mtime +50 –mtime -100
          find / -cmin -60
          find / -mmin -60
          find / -amin -60
          find / -size 50M
          find / -size +50M -size -100M
          find / -type f -size +100M -exec rm -f {} \;
          find / -type f -name *.mp3 -size +10M -exec rm {} \;

11) List all objects in /etc that contain the ss character sequence. How can I duplicate a similar command using a bunch of grep?

[How To Use grep Command In Linux](https://www.cyberciti.biz/faq/howto-use-grep-command-in-linux-unix/)

          man grep
          grep --help
          info grep 

          grep 'ss' /etc/*
          grep -i 'ss' /etc/*
          grep -R 'ss' /etc/*
          grep -c 'ss' /etc/*

***Команда Grep***
          Grep или Global Regular Expression Print – основная программа поиска в Unix-подобных системах, которая может искать любой тип строки в любом файле или списке файлов или даже выводить любую команду.

          В качестве шаблона поиска он использует обычные регулярные выражения, кроме обычных строк. В Basic Regular Expressions (BRE) метасимволы вроде: ‘{‘, ‘}’, ‘(‘, ‘)’, ‘|’, ‘+’, ‘?’ теряют свой смысл и считаются нормальными символами строки и должны быть выделены специальным образом, если их следует рассматривать как специальные символы.

          Кроме того, grep использует алгоритм Boyer-Moore для быстрого поиска любой строки или регулярного выражения.

          1 $ grep -C 0 '(f|g)ile' example.txt
          2 $ grep -C 0 '\(f\|g\)ile' example.txt

          В примере выше, когда команда запускается без экранирования ‘(‘ ‘)’ и ‘|’, затем grep ищет полную строку, то есть «(f | g) ile» в файле. Но когда специальные символы были экранированы, grep обрабатывает их как метасимволы и ищет слова «file» или «gile» в файле.

***Команда egrep***
          Egrep или grep -E – это другая версия grep или Extended grep. Эта версия grep эффективна и быстра, когда дело доходит до поиска шаблона регулярных выражений, поскольку она обрабатывает метасимволы как есть и не заменяет их как строки. Egrep использует ERE или Extended Extended Expression.

          В случае egrep, даже если вы не избегаете метасимволы, команда будет относиться к ним как к специальным символам и заменять их своим особым значением вместо того, чтобы рассматривать их как часть строки.

          1 $ egrep -C 0 '(f|g)ile' example.txt
          2 $ egrep -C 0 '\(f\|g\)ile' example.txt

          Здесь egrep ищет строку «file», когда мета-символы не экранированы, поскольку это означает значение этих символов. Но, когда эти символы стали экранированы, egrep рассматривает их как часть строки и ищет полную строку «(f | g) ile» в файле.

***Команда fgrep***
          Fgrep или Fixed grep или grep -F – это еще одна версия grep, которая необходима, когда дело доходит до поиска всей строки вместо регулярного выражения, поскольку оно не распознает ни регулярные выражения, ни метасимволы. Для поиска любой строки напрямую выбирайте эту версия grep.

          Fgrep ищет полную строку и не распознает специальные символы как часть регулярного выражения, несмотря на то экранированы символы или нет.

          1 $ fgrep -C 0 '(f|g)ile' example.txt
          2 $ fgrep -C 0 '\(f\|g\)ile' example.txt

          Когда метасимволы не были экранированы, fgrep искала полную строку «(f | g) ile» в файле, а когда метасимволы стали экранированы, команда fgrep искала «\ (f \ | g \) Ile» все символы которые есть в файле.
          
***Вывод***
          Выше рассмотрены различия между «grep», «egrep» и «fgrep». Несмотря на различия в наборе используемых регулярных выражений и скорости выполнения, параметры командной строки остаются одинаковыми для всех трех версий grep.

> 12) Organize a screen-by-screen print of the contents of the /etc directory. Hint:
You must use stream redirection operations.

[less command in Linux with Examples](https://www.geeksforgeeks.org/less-command-linux-examples/)

[How to Use Less](https://linuxize.com/post/less-command-in-linux/)

     man less
     less --help
     info less

     less [OPTIONS] filename
     less /usr/share/common-licenses/GPL-3
     ps aux | less

     When opening a file which content is too large to fit in one page, you will see a single colon (:).

     To go forward to the next page press either the f key or Space bar. If you want to move down for a specific number of lines, type the number followed by the space or f key.

     You can press either the Down arrow or Enter to scroll forward by one line and Up arrow scroll backward by one line.

     To go back to the previous page hit the b key. Move up for a specific number of lines, by typing the number followed by the b key.

     If you want to search for a pattern, type forward slash (/) followed by the pattern you want to search. Once you hit Enter less will search forward for matches. To search backwards use (?) followed by the search pattern.

     When the end of the file is reached, the string (END) is shown at the bottom of the screen.
     To quit less and go back to the command line press 

     less -N filename
     less -X filename
     less +F /var/log/messages

     When launched with +F, less will behave pretty much the same as 
[tail -f](https://linuxize.com/post/less-command-in-linux/)

[Команды фильтрации в Linux. head, tail, sort, nl, wc, cut, sed, uniq, tac](https://linuxvsem.ru/commands/komandy-filtratsii-v-linux)

     Below are some of the most frequently used commands to navigate through the file content when viewed by less:

     Command	Action
     Down arrow, Enter, e, or j	Move forward one line.
     Up arrow,y or k	Move backward one line.
     Space bar or f	Move Forward one page.
     b	Move Backward one page.
     /pattern	Search forward for matching patterns.
     ?pattern	Search backward for matching patterns.
     n	Repeat previous search.
     N	Repeat previous search in reverse direction.
     g	Go to the first line in the file.
     Ng	Go to the N-th line in the file.
     G	Go to the last line in the file.
     p	Go to the beginning of fthe ile.
     Np	Go to N percent into file.
     h	Display help.
     q	Exit less.
     Conclusion
     By now you should have a good understanding of how to use the less command.

     For a complete list of all options and commands type man less in your terminal.

> 13) What are the types of devices and how to determine the type of device? Give
examples.

[device types](https://linuxjourney.com/lesson/device-types)

     Before we chat about how devices are managed, let's actually take a look at some devices.

     $ ls -l /dev

     brw-rw----   1 root disk      8,   0 Dec 20 20:13 sda

     crw-rw-rw-   1 root root      1,   3 Dec 20 20:13 null

     srw-rw-rw-   1 root root           0 Dec 20 20:13 log

     prw-r--r--   1 root root           0 Dec 20 20:13 fdata

     The columns are as follows from left to right:

     Permissions
     Owner
     Group
     Major Device Number
     Minor Device Number
     Timestamp
     Device Name
     Remember in the ls command you can see the type of file with the first bit on each line. Device files are denoted as the following:

     c - character
     b - block
     p - pipe
     s - socket
***Character Device***

     These devices transfer data, but one a character at a time. You'll see a lot of pseudo devices (/dev/null) as character devices, these devices aren't really physically connected to the machine, but they allow the operating system greater functionality.

***Block Device***

     These devices transfer data, but in large fixed-sized blocks. You'll most commonly see devices that utilize data blocks as block devices, such as harddrives, filesystems, etc.

***Pipe Device***

     Named pipes allow two or more processes to communicate with each other, these are similar to character devices, but instead of having output sent to a device, it's sent to another process.

***Socket Device***

     Socket devices facilitate communication between processes, similar to pipe devices but they can communicate with many processes at once.

***Device Characterization***

     Devices are characterized using two numbers, major device number and minor device number. You can see these numbers in the above ls example, they are separated by a comma. For example, let's say a device had the device numbers: 8, 0:

     The major device number represents the device driver that is used, in this case 8, which is often the major number for sd block devices. The minor number tells the kernel which unique device it is in this driver class, in this case 0 is used to represent the first device (a).

[device types](https://www.tecmint.com/find-linux-filesystem-type/)

***1. Using df Command***
     df command reports file system disk space usage, to include the file system type on a particular disk partition, use the -T flag as below:

     $ df -Th
     OR
     $ df -Th | grep "^/dev"

***2. Using fsck Command***
     fsck is used to check and optionally repair Linux file systems, it can also print the file system type on specified disk partitions.

     The flag -N disables checking of file system for errors, it just shows what would be done (but all we need is the file system type):

     $ fsck -N /dev/sda3
     $ fsck -N /dev/sdb1

***3. Using lsblk Command***
     lsblk displays block devices, when used with the -f option, it prints file system type on partitions as well:

     $ lsblk -f

***4. Using mount Command***
     mount command is used to mount a file system in Linux, it can also be used to mount an ISO image, mount remote Linux filesystem and so much more.

     When run without any arguments, it prints info about disk partitions including the file system type as below:

     $ mount | grep "^/dev"

***5. Using blkid Command***
     blkid command is used to find or print block device properties, simply specify the disk partition as an argument like so:

     $ blkid /dev/sda3

***6. Using file Command***
     file command identifies file type, the -s flag enables reading of block or character files and -L enables following of symlinks:

     $ sudo file -sL /dev/sda3

***7. Using fstab File***
     The /etc/fstab is a static file system info (such as mount point, file system type, mount options etc) file:

     $ cat /etc/fstab

> 14) How to determine the type of file in the system, what types of files are there?

[How to Identify File Types in Linux](https://www.2daygeek.com/find-identify-file-types-in-linux/)

[How to Find Out File Types in Linux](https://www.geeksforgeeks.org/how-to-find-out-file-types-in-linux/)

     man file
     info file
     file --help

     Syntax: file [OPTION…] [FILE…]

     file -v
     file file.txt
     cat file.txt
     file -f file.txt
     file -s /dev/sda
     file -f GFG.txt
     file -F '#' GFG.txt
     file -L stdin
     file --extension GFG.rar

We can also use ls command to determine a type of file.
     Syntax:

ls [OPTION]... [FILE]...

***Regular Files***

    Regular files are ordinary files on a system that contains programs, texts, or data. It is used to store information such as text, or images. These files are located in a directory/folder. Regular files contain all readable files such as text files, Docx files, programming files, etc, Binary files, image files such as JPG, PNG, SVG, etc, compressed files such as ZIP, RAR, etc. 

We can find out block file by using the following command:

***Directory Files***
     
      ls -l | grep ^d 
***1. Block Files:***

      ls -l | grep ^b
***2. Character device files:***

      ls -l | grep ^c
***3. Pipe Files:***

      ls -l | grep ^p
***4. Symbol link files:***

      ls -l | grep ^l
***5. Socket Files:***

      find / -type s 
      ls -l | grep ^s

> 15) * List the first 5 directory files that were recently accessed in the /etc
directory.

[Tail command in Linux with examples](https://www.geeksforgeeks.org/tail-command-linux-examples/)

     It is the complementary of head command.The tail command, as the name implies, print the last N number of data of the given input. By default it prints the last 10 lines of the specified files. If more than one file name is provided then data from each file is precedes by its file name.

     Syntax:

     tail [OPTION]... [FILE]...

     ls -ltr | tail -n 5

[Head command in Linux with examples](https://www.geeksforgeeks.org/head-command-linux-examples/)

     It is the complementary of Tail command. The head command, as the name implies, print the top N number of data of the given input. By default, it prints the first 10 lines of the specified files. If more than one file name is provided then data from each file is preceded by its file name. 

     Syntax: 
     

     head [OPTION]... [FILE]...