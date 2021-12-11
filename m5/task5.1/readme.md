
[DevOps_online_Kiev_2021Q4 (MY GITHUB URL REPO)](https://github.com/vasilkyiv/DevOps_online_Kiev_2021Q4.git)
=======================================

[MODULE 05 NETWORKING](https://github.com/vasilkyiv/DevOps_online_Kiev_2021Q4/tree/main/m5) 
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
[![*Report in screenshots*](shreenshot/1.png?raw=true)](https://github.com/vasilkyiv/DevOps_online_Kiev_2021Q4/tree/main/m3/task4.1)

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