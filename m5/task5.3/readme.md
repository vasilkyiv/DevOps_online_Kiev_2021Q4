
[DevOps_online_Kiev_2021Q4 (MY GITHUB URL REPO)](https://github.com/vasilkyiv/DevOps_online_Kiev_2021Q4.git)
=======================================

[MODULE 05 NETWORKING](https://github.com/vasilkyiv/DevOps_online_Kiev_2021Q4/tree/main/m5) 
===========================================================================
 # [TASK_5.3 LinuxEssentials](https://github.com/vasilkyiv/DevOps_online_Kiev_2021Q4/tree/main/m5)

# [Part 1](https://github.com/vasilkyiv/DevOps_online_Kiev_2021Q4/tree/main/m5)

> 1. How many states could has a process in Linux?

[Understanding Linux Process States](https://access.redhat.com/sites/default/files/attachments/processstates_20120831.pdf)

[Process States](https://linuxjourney.com/lesson/process-states)

[Linux Process States](https://www.baeldung.com/linux/process-states)

     R: running or runnable, it is just waiting for the CPU to process it
     S: Interruptible sleep, waiting for an event to complete, such as input from the erminal
     D: Uninterruptible sleep, processes that cannot be killed or interrupted with a signal, usually to make them go away you have to reboot or fix the issue
     Z: Zombie, we discussed in a previous lesson that zombies are terminated processes that are waiting to have their statuses collected
     T: Stopped, a process that has been suspended/stopped

> 2. Examine the pstree command. Make output (highlight) the chain (ancestors) of the current
process.

[pstree Command in Linux with Examples](https://www.geeksforgeeks.org/pstree-command-in-linux-with-examples/)

     pstree [options] [pid or username]

     pstree
     pstree -a
     pstree -p
     pstree -c
     pstree -n
     pstree -u
     pstree -h
     pstree -g
     pstree khushi
     pstree -V

> 3. What is a proc file system?

[proc file system in Linux](https://www.geeksforgeeks.org/proc-file-system-linux/)

     Proc file system (procfs) is virtual file system created on fly when system boots and is dissolved at time of system shut down.

     It contains useful information about the processes that are currently running, it is regarded as control and information center for kernel.

     The proc file system also provides communication medium between kernel space and user space.

     ls -l /proc | grep '^d'
     ps -aux
     ls -ltr /proc/7494

     /proc/PID/cmdline
     /proc/PID/cwd
     /proc/PID/exe
     /proc/PID/maps
     /proc/PID/root
     /proc/PID/statm
     /proc/crypto
     /proc/filesystems
     /proc/meminfo
     /proc/tty

     less /proc/crypto

> 4. Print information about the processor (its type, supported technologies, etc.).

[9 Commands to Check CPU Information on Linux](https://www.binarytides.com/linux-cpu-information/)

     less /proc/cpuinfo
     lscpu
     hardinfo | less
     lshw -class processor
     nproc
     dmidecode
     sudo apt-get install cpuid
     sudo apt-get install inxi
     hwinfo --short --cpu

> 5. Use the ps command to get information about the process. The information should be as follows: the owner of the process, the arguments with which the process was  launched for execution, the group owner of this process, etc.

     ps aufx

[![*Report in screenshots*](shreenshot/1.png?raw=true)](https://github.com/vasilkyiv/DevOps_online_Kiev_2021Q4/tree/main/m5/task5.3)

6. How to define kernel processes and user processes?

[Как в linux определить процессы ядра и пользовательские процессы](https://ru.stackoverflow.com/questions/528566/%D0%9A%D0%B0%D0%BA-%D0%B2-linux-%D0%BE%D0%BF%D1%80%D0%B5%D0%B4%D0%B5%D0%BB%D0%B8%D1%82%D1%8C-%D0%BF%D1%80%D0%BE%D1%86%D0%B5%D1%81%D1%81%D1%8B-%D1%8F%D0%B4%D1%80%D0%B0-%D0%B8-%D0%BF%D0%BE%D0%BB%D1%8C%D0%B7%D0%BE%D0%B2%D0%B0%D1%82%D0%B5%D0%BB%D1%8C%D1%81%D0%BA%D0%B8%D0%B5-%D0%BF%D1%80%D0%BE%D1%86%D0%B5%D1%81%D1%81%D1%8B)


В современном linux, в отличие от многих других Unix есть так называемые "***процессы ядра***". По суди это просто части самого ядра, функции общего кода ядра, работающие в том же адресном пространстве и с теми же привилегиями, что и остальной код ядра. Единственное их отличие от других частей ядра, для них создаются отдельные записи в таблице процессов. Процессами они сделаны для того, что бы их выполнение происходило независимо от остальных частей ядра, с более низким приоритетом. Их выполнение происходит под контролем планировщика, как и все остальные процессы в системе.

Процессы ядра linux запускаются самим ядром, при этом родительским процессом якобы их породившим, назначается процесс ***kthread***, с ***PID=2***. Таким образом процессами ядра надо считать сам процесс с PID=2, а так же процессы у которых PPID (т.е. pid родителя) равен ***2***.

***sudo ps --ppid=2 --pid=2***  

     Пользовательские процессы - все остальные:

***sudo ps -N --ppid=2 --pid=2***

     Так же по умолчанию pstree без параметров показывает только дерево процессов порожденных init, т.е. пользовательских процессов. Процессы ядра покажет 
sudo ***pstree 2.***

     @jumpjet67 init - обычный пользовательский процесс (за исключением того, что это единственный процесс запускаемый самим ядром), он стартует все пользовательские процессы в системе, по ps --ppid=1 вы увидите все запущенные при инициализации системы демоны и обработчики терминалов, они в свою очередь запускают другие процессы. Во многих unix системах такой штуки как "процесс ядра" в принципе не было. В современном linux они работают независимо от init и запускаются kthread'ом. Нашел еще одно отличие: у процессов ядра /proc/pid/exe никуда не указывает, так как нет выполнимого файла на диске – 
     Mike
     
     Ок. Вы пишите "Все процессы ядра linux запускаются одним родительским процессом kthread", а в комменте "init - стартует все пользовательские процессы в системе". А как они связаны друг с другом? init запускает kthread или наоборот? Просто получилось много умных слов, мне как далёкому от этих дел пользователю мало что из них стало ясно. – 
     aryndin
     
     
     @jumpjet67 Подумав, я дописал в ответе про pstree. По нему видно, что у linux два независимых дерева процессов, пользовательские - порожденные init, и ядерные - порожденные kthread. Да, я немного слукавил написав, что init единственный запускаемый ядром процесс. Это у других unix у которых нет ядерных процессов init - общий родитель всего. А в linux ядерные процессы есть, они даже работают в адресном пространстве ядра и ядро само стартует их по мере необходимости, назначая родителем pthread, независимо от init. – 
     Mike

> 7. Print the list of processes to the terminal. Briefly describe the statuses of the processes. What condition are they in, or can they be arriving in?

[Show All Running Processes in Linux using ps/htop commands](https://www.cyberciti.biz/faq/show-all-running-processes-in-linux/)
      
     Linux commands show all running processes
     Apart from ps command, you can also use the following commands to display info about processes on Linux operating systems:

     top command : Display and update sorted information about Linux processes.
     atop command : Advanced System & Process Monitor for Linux.
     htop command : Interactive process viewer in Linux.
     pgrep command : Look up or signal processes based on name and other attributes.
     pstree command : Display a tree of processes.
     
***ps -aux | less***

***ps aux | less***

     Where, 
          A : Select all processes
          u : Select all processes on a terminal, including those of other users
          x : Select processes without controlling ttys
     
***ps -U root -u root -N***

***ps -U root -u root --deselect***

> 8. Display only the processes of a specific user.

***ps -u vivek***

top
pstree

> 9. What utilities can be used to analyze existing running tasks (by analyzing the help for the ps command)?

[man ps](https://man7.org/linux/man-pages/man1/ps.1.html)

### Pages that refer to this page:
      free(1),  fuser(1),  htop(1),  killall(1),  pgrep(1),  pidstat(1),  pmap(1),  pslog(1),  pstree(1),  pwdx(1),  slabtop(1),  systemd(1),  systemd-cgls(1),  systemd-firstboot(1),  systemd-nspawn(1),  tcpdump(1),  tload(1),  top(1),  uptime(1),  w(1),  proc(5),  credentials(7),  pid_namespaces(7),  pthreads(7),  sched(7),  lsof(8),  systemd-machined.service(8),  tcpdump(8),  vmstat(8)

> 10. What information does top command display?

[The top command (table of processes) displays the processor activity of your Linux box and also displays tasks managed by the kernel in real-time.](https://www.tecmint.com/12-top-command-examples-in-linux/)

     top
     htop
> 11. Display the processes of the specific user using the top command.

To display all user-specific running processes information, use the ***-u*** option will list specific User process details.

     top -u tecmint

> 12. What interactive commands can be used to control the top command? Give a couple of examples.

     -h | -v	Help/Version

     Show library version and the usage prompt, then quit.
     -b	Batch-mode operation

     Starts top in 'Batch' mode, which could be useful for sending output from top to other programs or to a file. In this mode, top does not accept input and runs until the iterations limit you've set with the '-n' command-line option, or until killed.
     -c	Command-line/Program-name toggle

     Starts top with the last remembered 'c' state reversed. Thus, if top was displaying command lines, now that field shows program names, and visa versa. See the 'c' interactive command for additional information.
     -d interval	Delay-time, where interval is represented as: ss.tt (secs.tenths)

     Specifies the delay between screen updates, and overrides the corresponding value in one's personal configuration file or the startup default. Later this can be changed with the 'd' or 's' interactive commands.

     Fractional seconds are honored, but a negative number is not allowed. In all cases, however, such changes are prohibited if top is running in 'Secure mode', except for root (unless the 's' command-line option was used).
     -H	Threads-mode operation

     Instructs top to display individual threads. Without this command-line option a summation of all threads in each process is shown. Later this can be changed with the 'H' interactive command.
     -i	Idle-process toggle

     Starts top with the last remembered 'i' state reversed. When this toggle is Off, tasks that have not used any CPU since the last update is not displayed.
     -n limit	Number of iterations

     Specifies the maximum number of iterations, or frames, top should produce before ending.
     -ppid	Monitor-PIDs mode, specified as: -ppid1 -ppid2 ... or -ppid1,pid2,pid3 ...

     Monitor only processes with specified process IDs. This option can be given up to 20 times, or you can provide a comma delimited list with up to 20 pids. Co-mingling both forms is permitted.

     A pid value of zero is treated as the process id of the top program itself (once it is running).

     This command-line option only and should you want to return to normal operation, it is not necessary to quit and restart top -- issue any of these interactive commands: '=', 'u' or 'U'.

     The 'p', 'u' and 'U' command-line options are mutually exclusive.
     -s	Secure-mode operation

     Starts top with secure mode forced, even for root. This mode is far better controlled through the system configuration file (see topic 6. FILES).
     -S	Cumulative-time toggle

     Starts top with the last remembered 'S' state reversed. When 'Cumulative time' mode is On, each process is listed with the cpu time that it and its dead children have used. See the 'S' interactive command for additional information regarding this mode.
     -u|
     -U user-id-or-name	User-filter-mode

     Display only processes with a user id or username matching that given. The '-u' option matches the effective user whereas the '-U' option matches on any user (real, effective, saved, or filesystem).

     The 'p', 'u' and 'U' command-line options are mutually exclusive.
     -w number	Output-width-override

     In 'Batch' mode, when used without an argument, top formats output using the COLUMNS= and LINES= environment variables, if set. Otherwise, width is fixed at the maximum 512 columns. With an argument, output width can be decreased or increased (up to 512) but the number of rows is considered unlimited.

     In normal display mode, when used without an argument, top attempts to format output using the COLUMNS= and LINES= environment variables, if set. With an argument, output width can only be decreased, not increased. Whether using environment variables or an argument with -w, when not in 'Batch' mode actual terminal dimensions can never be exceeded.

     Note: Without the use of this command-line option, output width is always based on the terminal at which top was invoked whether or not in 'Batch' mode.

[Linux top command](https://www.computerhope.com/unix/top.htm)

> 13. Sort the contents of the processes window using various parameters (for example, the amount of processor time taken up, etc.)

[top(1) — Linux manual page](https://man7.org/linux/man-pages/man1/top.1.html)

***top -o %CPU***

***top -o DATA***

***top -u ovo***

***top -o ENVIRON***

***htop --sort-key=PERCENT_MEM***
[![*Report in screenshots*](shreenshot/1.png?raw=true)](https://github.com/vasilkyiv/DevOps_online_Kiev_2021Q4/tree/main/m5/task5.3)

[![*Report in screenshots*](shreenshot/2.png?raw=true)](https://github.com/vasilkyiv/DevOps_online_Kiev_2021Q4/tree/main/m5/task5.3)

[![*Report in screenshots*](shreenshot/3.png?raw=true)](https://github.com/vasilkyiv/DevOps_online_Kiev_2021Q4/tree/main/m5/task5.3)

[![*Report in screenshots*](shreenshot/4.png?raw=true)](https://github.com/vasilkyiv/DevOps_online_Kiev_2021Q4/tree/main/m35/task5.3)

[![*Report in screenshots*](shreenshot/5.png?raw=true)](https://github.com/vasilkyiv/DevOps_online_Kiev_2021Q4/tree/main/m5/task5.3)

[![*Report in screenshots*](shreenshot/6.png?raw=true)](https://github.com/vasilkyiv/DevOps_online_Kiev_2021Q4/tree/main/m5/task5.3)

     ### Use the ***top*** command in Linux/Unix:
     
     press ***shift+m*** after running the top command

          or you can interactively choose which column to sort on

     press ***Shift+f*** to enter the interactive menu

     press the up or down arrow until the ***%MEM*** choice is highlighted

     press ***s*** to select ***%MEM ***choice

     press enter to save your selection

     press ***q*** to exit the interactive menu

> 14. Concept of priority, what commands are used to set priority?
     
[Linux commands: How to manipulate process priority ](https://www.redhat.com/sysadmin/manipulate-process-priority)

      nice(1), renice(1), fork(2), getpriority(2), getrlimit(2),
       setpriority(2), capabilities(7), sched(7)

[How to Set Linux Process Priority Using nice and renice Commands ](https://www.tecmint.com/set-linux-process-priority-using-nice-and-renice-commands/)

***ps axo pid,comm,nice,cls --sort=-nice***

[Change The Priority Of A Process With Nice command](https://ostechnix.com/change-priority-process-linux/)

     In Unix ecosystem, a process is a running program. So, any program running on your Linux box is a process. One or more processes can be running on your Linux box at a time. We can display the information about active processes using ps command. By default, the ps command only shows current user's processes. You can use "ps -ef" (without quotes, of course) command to display all processes. To view the user of a process, we use "ps -u". Hope you got a basic idea about Linux processes. Let us now come to the today's topic - how to change the priority of a process in Linux using nice and renice commands.

     As you might know, by default, Linux kernel considers all processes equally important and allocates the same amount of CPU time for each process. Sometimes, you might want to increase or decrease the priority of certain processes to utilize more CPU time. This is where the nice and renice commands comes in help. Nice command is used to run a process with an user defined priority whereas renice command is used to change the priority of a running process. Generally, nice and renice commands are used to change the priority than the default priority of a process.

***nice -15 cmus &***

***renice -n 18 -p 15059***

***renice -n -20 -g ostechnix***

> 15. Can I change the priority of a process using the top command? If so, how?

[Once given top command, press r. Give PID value of the process you want to change the process value. Give renice value (from -20 to +19)](https://unix.stackexchange.com/questions/484576/how-we-can-change-the-priority-of-a-process-with-top-command-in-linux)

> 16. Examine the kill command. How to send with the kill command process control signal? Give an example of commonly used signals

[kill Command](https://linuxize.com/post/kill-command-in-linux/)

[kill command in Linux with Examples](https://www.geeksforgeeks.org/kill-command-in-linux-with-examples/)

[Linux / UNIX: Kill Command Examples](https://www.cyberciti.biz/faq/unix-kill-command-examples/)

***man kill ***

***kill --help***

***info kill***

***kill -9 6263 6199 6142 6076***

     root@ict-net-adm:/# kill -l
     1) SIGHUP       2) SIGINT       3) SIGQUIT      4) SIGILL       5) SIGTRAP
     6) SIGABRT      7) SIGBUS       8) SIGFPE       9) SIGKILL     10) SIGUSR1
     11) SIGSEGV     12) SIGUSR2     13) SIGPIPE     14) SIGALRM     15) SIGTERM
     16) SIGSTKFLT   17) SIGCHLD     18) SIGCONT     19) SIGSTOP     20) SIGTSTP
     21) SIGTTIN     22) SIGTTOU     23) SIGURG      24) SIGXCPU     25) SIGXFSZ
     26) SIGVTALRM   27) SIGPROF     28) SIGWINCH    29) SIGIO       30) SIGPWR
     31) SIGSYS      34) SIGRTMIN    35) SIGRTMIN+1  36) SIGRTMIN+2  37) SIGRTMIN+3
     38) SIGRTMIN+4  39) SIGRTMIN+5  40) SIGRTMIN+6  41) SIGRTMIN+7  42) SIGRTMIN+8
     43) SIGRTMIN+9  44) SIGRTMIN+10 45) SIGRTMIN+11 46) SIGRTMIN+12 47) SIGRTMIN+13
     48) SIGRTMIN+14 49) SIGRTMIN+15 50) SIGRTMAX-14 51) SIGRTMAX-13 52) SIGRTMAX-12
     53) SIGRTMAX-11 54) SIGRTMAX-10 55) SIGRTMAX-9  56) SIGRTMAX-8  57) SIGRTMAX-7
     58) SIGRTMAX-6  59) SIGRTMAX-5  60) SIGRTMAX-4  61) SIGRTMAX-3  62) SIGRTMAX-2
     63) SIGRTMAX-1  64) SIGRTMAX

17. Commands jobs, fg, bg, nohup. What are they for? Use the sleep, yes command to demonstrate the process control mechanism with fg, bg&

[Процессы, задачи. Команды fg, bg, jobs, top, nohup](https://intellect.icu/protsessy-zadachi-komandy-fg-bg-jobs-top-nohup-680)

- jobs: Display a list of the jobs with their status 
          
- fg: Move a background job into the foreground
          
- bg: Resume suspended jobs by running them as background jobs

     top 

     CTRL+Z

     jobs 

     fg

[![*Report in screenshots*](shreenshot/7.png?raw=true)](https://github.com/vasilkyiv/DevOps_online_Kiev_2021Q4/tree/main/m5/task5.3)



[Part 2 ](https://github.com/vasilkyiv/DevOps_online_Kiev_2021Q4/tree/main/m5)

1. Check the implementability of the most frequently used OPENSSH commands in the MS
Windows operating system. (Description of the expected result of the commands +
screenshots: command – result should be presented)

[![*Report in screenshots*](shreenshot/8.png?raw=true)](https://github.com/vasilkyiv/DevOps_online_Kiev_2021Q4/tree/main/m5/task5.3)

[![*Report in screenshots*](shreenshot/9.png?raw=true)](https://github.com/vasilkyiv/DevOps_online_Kiev_2021Q4/tree/main/m5/task5.3)

2. Implement basic SSH settings to increase the security of the client-server connection (at least)

[Top 20 OpenSSH Server Best Security Practices](https://www.cyberciti.biz/tips/linux-unix-bsd-openssh-server-best-practices.html)

                    1. Use SSH public key based login

                         $ ssh-keygen -t key_type -b bits -C "comment"

                         $ ssh-keygen -t ed25519 -C "Login to production cluster at xyz corp"

                         $ ssh-keygen -t rsa -b 4096 -f ~/.ssh/id_rsa_aws_$(date +%Y-%m-%d) -C "AWS key for abc corp clients"

                    ***ssh vivek@rhel7-aws-server***

                    2. Disable root user login

                         sudo adduser vivek sudo

                         sudo usermod -aG wheel vivek

                    3. Disable password based login

                    4. Limit Users’ ssh access

                    5. Disable Empty Passwords

                    6. Use strong passwords and passphrase for ssh users/keys

                    7. Firewall SSH TCP port # 22

                    8. Change SSH Port and limit IP binding

                    9. Use TCP wrappers (optional)

> 3. List the options for choosing keys for encryption in SSH. Implement 3 of them.

[Choosing an Algorithm and Key Size](https://www.ssh.com/academy/ssh/keygen#choosing-an-algorithm-and-key-size)


### Choosing an Algorithm and Key Size
     SSH supports several public key algorithms for authentication keys. These include:

     rsa - an old algorithm based on the difficulty of factoring large numbers. A key size of at least 2048 bits is recommended for RSA; 4096 bits is better. RSA is getting old and significant advances are being made in factoring. Choosing a different algorithm may be advisable. It is quite possible the RSA algorithm will become practically breakable in the foreseeable future. All SSH clients support this algorithm.

     dsa - an old US government Digital Signature Algorithm. It is based on the difficulty of computing discrete logarithms. A key size of 1024 would normally be used with it. DSA in its original form is no longer recommended.

     ecdsa - a new Digital Signature Algorithm standarized by the US government, using elliptic curves. This is probably a good algorithm for current applications. Only three key sizes are supported: 256, 384, and 521 (sic!) bits. We would recommend always using it with 521 bits, since the keys are still small and probably more secure than the smaller keys (even though they should be safe as well). Most SSH clients now support this algorithm.

     ed25519 - this is a new algorithm added in OpenSSH. Support for it in clients is not yet universal. Thus its use in general purpose applications may not yet be advisable.

     The algorithm is selected using the -t option and key size using the -b option. The following commands illustrate:

     ssh-keygen -t rsa -b 4096 ssh-keygen -t dsa ssh-keygen -t ecdsa -b 521 ssh-keygen -t ed25519

> 4. Implement port forwarding for the SSH client from the host machine to the guest Linux virtual machine behind NAT.

[How to enable access to VirtualBox via SSH NAT ?](hhttps://bobcares.com/blog/virtualbox-ssh-nat/)

[![*Report in screenshots*](shreenshot/10.png?raw=true)](https://github.com/vasilkyiv/DevOps_online_Kiev_2021Q4/tree/main/m5/task5.3)

[![*Report in screenshots*](shreenshot/11.png?raw=true)](https://github.com/vasilkyiv/DevOps_online_Kiev_2021Q4/tree/main/m5/task5.3)

[![*Report in screenshots*](shreenshot/12.png?raw=true)](https://github.com/vasilkyiv/DevOps_online_Kiev_2021Q4/tree/main/m5/task5.3)

> 5*. Intercept (capture) traffic (tcpdump, wireshark) while authorizing the remote client on the server using ssh, telnet, rlogin. Analyze the result.

[12 Tcpdump Commands – A Network Sniffer Tool](https://www.tecmint.com/12-tcpdump-commands-a-network-sniffer-tool/)

***tcpdump -vv -i any -nn port 22 -w tcp.pcap***

***tcpdump -vv -i any -nn port 23 -w tcp.pcap***