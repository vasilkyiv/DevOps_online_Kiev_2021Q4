
[DevOps_online_Kiev_2021Q4 (MY GITHUB URL REPO)](https://github.com/vasilkyiv/DevOps_online_Kiev_2021Q4.git)
=======================================

[MODULE 06 LINUX NETWORKING](https://github.com/vasilkyiv/DevOps_online_Kiev_2021Q4/tree/main/m6) 
===========================================================================

 # [TASK_6.1 INUX NETWORKING](https://github.com/vasilkyiv/DevOps_online_Kiev_2021Q4/tree/main/m6)

> 1. Create virtual machines connection according to figure 1:

[![*Report in screenshots*](shreenshot/1.png?raw=true)](https://github.com/vasilkyiv/DevOps_online_Kiev_2021Q4/tree/main/m6/task6.1)

> 2. VM2 has one interface (internal), VM1 has 2 interfaces (NAT and internal). Configure all network interfaces in order to make VM2 has an access to the Internet (iptables, forward, masquerade).

### for host 1
***hostnamectl set-hostname vm1***

***echo vm1  127.0.0.1 >> /etc/hosts***
    
    ubuntu@vm1:~$ sudo -s

    root@vm1:/home/ubuntu# cat /etc/netplan/01-network-manager-all.yaml 

    # Let NetworkManager manage all devices on this system
    network:
    version: 2
    renderer: NetworkManager
    ethernets:
        enp0s8:
        dhcp4: no
        dhcp6: no
        addresses: [192.168.1.1/24]
        gateway4: 10.0.2.2
        nameservers:
            addresses: [8.8.8.8, 8.8.4.4]
        enp0s3:
        dhcp4: no
        dhcp6: no
        addresses: [10.0.2.15/24]
        gateway4: 10.0.2.2
        nameservers:
            addresses: [8.8.8.8, 8.8.4.4]
        routes:
        - to: 0.0.0.0/0
            via: 10.0.2.2 
            metric: 0  

    root@vm1:/home/ubuntu# 

 

### for host 2

hostnamectl set-hostname vm2

echo vm2  127.0.0.1 >> /etc/hosts

[Как настроить сеть с Netplan в Ubuntuclear](https://ubuntos.ru/kak-nastroit-set-s-netplan-v-ubuntu)


root@ubuntu2110:/home/ubuntu# cat /etc/netplan/01-network-manager-all.yaml 

# Let NetworkManager manage all devices on this system
network:
  version: 2
  renderer: NetworkManager
  ethernets:
    enp0s8:
      dhcp4: no 
      dhcp6: no 
      addresses: [192.168.1.10/24] 
      nameservers: 
        addresses: [8.8.8.8]
      routes:
        - to: 0.0.0.0/0
          via: 192.168.1.1  

root@ubuntu2110:/home/ubuntu# 



