
[DevOps_online_Kiev_2021Q4 (MY GITHUB URL REPO)](https://github.com/vasilkyiv/DevOps_online_Kiev_2021Q4.git)
=======================================

[MODULE 06 LINUX NETWORKING](https://github.com/vasilkyiv/DevOps_online_Kiev_2021Q4/tree/main/m6) 
===========================================================================

 # [TASK_6.1 INUX NETWORKING](https://github.com/vasilkyiv/DevOps_online_Kiev_2021Q4/tree/main/m6)

> 1. Create virtual machines connection according to figure 1:

[![*Report in screenshots*](shreenshot/1.png?raw=true)](https://github.com/vasilkyiv/DevOps_online_Kiev_2021Q4/tree/main/m6/task6.1)

> 2. VM2 has one interface (internal), VM1 has 2 interfaces (NAT and internal). Configure all network interfaces in order to make VM2 has an access to the Internet (iptables, forward, masquerade).

hostnamectl set-hostname vm1

echo vm2 127.0.0.1 >> /etc/hosts

ip addr add 192.168.1.10/255.255.255.0 broadcast 192.168.1.255 dev eth0

ip link set eth0 up

echo vm1 127.0.0.1 >> /etc/hosts
