
[DevOps_online_Kiev_2021Q4 (MY GITHUB URL REPO)](https://github.com/vasilkyiv/DevOps_online_Kiev_2021Q4.git)
=======================================

[MODULE 06 LINUX NETWORKING](https://github.com/vasilkyiv/DevOps_online_Kiev_2021Q4/tree/main/m6) 
===========================================================================

 # [TASK_6.1 INUX NETWORKING](https://github.com/vasilkyiv/DevOps_online_Kiev_2021Q4/tree/main/m6)

> 1. Create virtual machines connection according to figure 1:

[![*Report in screenshots*](shreenshot/1.png?raw=true)](https://github.com/vasilkyiv/DevOps_online_Kiev_2021Q4/tree/main/m6/task6.1)

> 2. VM2 has one interface (internal), VM1 has 2 interfaces (NAT and internal). Configure all network interfaces in order to make VM2 has an access to the Internet (iptables, forward, masquerade).

>  # for host 1

***hostnamectl set-hostname vm1***

***echo vm1  127.0.0.1 >> /etc/hosts***
    
 > - ###  діюча  конфігурація netplan (static)

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

    root@vm1:/home/ubuntu

> - ### діюча конфігурація netplan (dhcp)

    root@vm1:/home/ubuntu# cat /etc/netplan/01-network-manager-all.yaml 

    # Let NetworkManager manage all devices on this system

    network:
      version: 2
      renderer: NetworkManager
      ethernets:
        enp0s3:
          dhcp4: yes
          dhcp6: no
          #addresses: [10.0.2.15/24]
          #gateway4: 10.0.2.2
          #nameservers: 
          # addresses: [8.8.8.8,8.8.4.4]
        # routes:
        # - to: 0.0.0.0/0
        #   via: 10.0.2.2
        #   metric: 0 
        enp0s8:
          dhcp4: no
          dhcp6: no
          addresses: [192.168.1.1/24]
          gateway4: 10.0.2.2
          nameservers:
            addresses: [8.8.8.8,8.8.4.4]
    root@vm1:/home/ubuntu# 

***echo 1 >> /proc/sys/net/ipv4/ip_forward***

***sudo iptables -t nat -A POSTROUTING -o enp0s3 -j MASQUERADE***

***sudo iptables -t nat -A PREROUTING -i enp0s3 -p tcp --dport 2222 -j DNAT --to-destination 192.168.1.10:22***

> - ### **bash_history**

      1  set hostnamectl vm1
      2  echo vm1 127.0.0.1 >> /etc/resolv.conf 
      3  vi /etc/resolv.conf 
      4  echo vm1 127.0.0.1 >> /etc/hosts 
      5  vim /etc/netplan/01-network-manager-all.yaml 
      6  vi /etc/netplan/01-network-manager-all.yaml 
      7  pwd
      8  hostnamectl set-hostname vm1
      9  echo vm1 127.0.0.1 >> /etc/hosts
    10  pwd
    11  ls -la
    12  clear
    13  ssh-keygen 
    14  clear
    15  ls .ssh/
    16  ls -la .ssh/
    17  ssh-keygen 
    18  cat .ssh/id_rsa 
    19  clear
    20  apt install vim
    21  vim /etc/netplan/01-network-manager-all.yaml 
    22  echo enp0s8: /etc/netplan/01-network-manager-all.yaml 
    23  echo 'enp0s8:' /etc/netplan/01-network-manager-all.yaml 
    24  cat /etc/netplan/01-network-manager-all.yaml 
    25  vim /etc/netplan/01-network-manager-all.yaml 
    26  fd
    27  fg
    28  netplan --debug apply
    29  vim /etc/netplan/01-network-manager-all.yaml 
    30  netplan --debug apply
    31  vim /etc/netplan/01-network-manager-all.yaml 
    32  netplan --debug apply
    33  vim /etc/netplan/01-network-manager-all.yaml 
    34  netplan --debug apply
    35  fg
    36  netplan --debug apply
    37  fg
    38  vim /etc/netplan/01-network-manager-all.yaml 
    39  netplan --debug apply
    40  ifconfigifconfiigf
    41  vim /etc/netplan/.01-network-manager-all.yaml.swp 
    42  rm /etc/netplan/.01-network-manager-all.yaml.swp 
    43  vim /etc/netplan/.01-network-manager-all.yaml
    44  vim /etc/netplan/01-network-manager-all.yaml
    45  netplan --debug apply
    46  vim /etc/netplan/01-network-manager-all.yaml
    47  netplan --debug apply
    48  fg
    49  netplan --debug apply
    50  vim /etc/netplan/01-network-manager-all.yaml
    51  netplan --debug apply
    52  vim /etc/netplan/01-network-manager-all.yaml
    53  netplan --debug apply
    54  vim /etc/netplan/01-network-manager-all.yaml
    55  netplan --debug apply
    56  ifconfig
    57  ping 192.168.1.10
    58  ping 10.0.2.2
    59  reboot
    60  sudo iptables -t nat -A POSTROUTING -o enp0s3 -j MASQUERADE
    61  iptables -t nat -S
    62  ip a
    63  ping 8.8.8.8
    64  route -n
    65  route  del 0.0.0.0
    66  route  del default vai 0.0.0.0
    67  route  del default via 10.0.2.2
    68  ip route  del default via 10.0.2.2
    69  route -n
    70  ip route add default via 10.0.2.2
    71  ping 8.8.8.8
    72  netplan apply
    73  vi  /etc/netplan/
    74  nano  /etc/netplan/01-network-manager-all.yaml 
    75  netplan apply
    76  nano  /etc/netplan/01-network-manager-all.yaml 
    77  netplan apply
    78  nano  /etc/netplan/01-network-manager-all.yaml 
    79  netplan --debug apply
    80  ip a
    81  ping 8.8.8.8
    82  iptables -t nat -S
    83  ip a
    84  iptables -t nat -A POSTROUTING -o enp0s3 -j MASQUERADE
    85  ufw disable
    86  ping 8.8.8.8
    87  ping 192.168.1.10
    88  iptables -S
    89  iptables -t nat -S
    90  iptables -F
    91  iptables -t nat -F
    92  iptables -t nat -A POSTROUTING -o enp0s3 -j MASQUERADE
    93  reboot 
    94  echo 8.8.8.8 /etc/resolv.conf 
    95  echo 8.8.8.8 >> /etc/resolv.conf 
    96  echo 8.8.4.4 >> /etc/resolv.conf 
    97  cta /etc/resolv.conf 
    98  cat /etc/resolv.conf 
    99  vim  /etc/resolv.conf 
    100  ping 8.8.8.8
    101  ping google.com.ua
    102  ping 192.168.1.10
    103  ssh ubuntu@192.168.1.10
    104  ssh -p 2222 ubuntu@192.168.1.10
    105  cat /etc/hosts
    106  iptables
    107  iptables -h
    108  iptables -h | less4
    109  iptables -h | less
    110  iptables -F
    111  ssh ubuntu@10.0.2.1
    112  ssh ubuntu@10.0.2.15
    113  ssh -p 2222 ubuntu@10.0.2.15
    114  ssh ubuntu@10.0.2.15:2222
    115  ssh ubuntu@10.0.2.15
    116  ssh -p  ubuntu@10.0.2.15
    117  ssh  ubuntu@10.0.2.15
    118  route
    119  vi /etc/netplan/01-network-manager-all.yaml 
    120  netplan --debug apply
    121  vi /etc/netplan/01-network-manager-all.yaml 
    122  netplan --debug apply
    123  ping 192.168.1.10
    124  ping 10.0.2.2.
    125  ping 10.0.2.2
    126  ping 10.0.2.1
    127  ping google.com.ua
    128  ping 8.8.8.8
    129  ssh ubuntu@192.168.1.10
    130  nano /proc/sys/net/ipv4/ip_forward
    131  exit
    132  history 

# for host 2

***hostnamectl set-hostname vm2***

***echo vm2  127.0.0.1 >> /etc/hosts***

[Как настроить сеть с Netplan в Ubuntuclear](https://ubuntos.ru/kak-nastroit-set-s-netplan-v-ubuntu)

 > - ###  діюча  конфігурація netplan (static) 

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
            gateway4: 192.168.1.1
            nameservers: 
              addresses: [8.8.8.8]
            routes:
              - to: 0.0.0.0/0
                via: 192.168.1.1  
    root@ubuntu2110:/home/ubuntu# 

### bash_history

  ubuntu@vm2:~$ history 
      1  sudo -s
      2  ping 192.168.1.1
      3  ping 10.0.2.2
      4  google.com.ua
      5  ping ukr.net
      6  sudo -
      7  sudo -s
      8  ip a
      9  route -n
    10  ping 8.8.8.8
    11  vi /etc/netplan/01-network-manager-all.yaml 
    12  traceroute 8.8.8.8
    13  ping 192.168.1.1
    14  ping 8.8.8.8
    15  vi /etc/netplan/01-network-manager-all.yaml 
    16  ip a
    17  ip a
    18  sudo netplan --debug apply
    19  ip a
    20  route  -n
    21  ping 8.8.8.8
    22  ping 192.169.1.2
    23  ping 192.168.1.20
    24  ping 192.168.1.1
    25  ip  route add default via 192.168.1.1
    26  sudo ip  route add default via 192.168.1.1
    27  route -n
    28  ping 8.8.8.8
    29  sudo ip  route del default via 192.168.1.1
    30  route -n
    31  sudo ip  route add default via 192.168.1.1
    32  sudo ip  route del default via 169.254.0.0
    33  sudo ip  route del 169.254.0.0
    34  sudo ip  route del 169.254.0.0/0
    35  route -n
    36  ping 8.8.8.8
    37  ping google.com
    38  ping 8.8.8.8
    39  route -n
    40  ping 192.168.1.1
    41  ping 10.0.2.2
    42  ip route add 10.0.2.0/24 via 192.168.1.1
    43  sudo ip route add 10.0.2.0/24 via 192.168.1.1
    44  ping 10.0.2.2
    45  ping 8.8.8.8
    46  sudo ip link set enp0s8 down
    47  sudo ip link set enp0s8 up
    48  ip a
    49  ping 8.8.8.8
    50  ping 192.168.1.1
    51  ping 8.8.8.8
    52  route -n
    53  sudo ip route addd default via 192.168.1.1
    54  sudo ip route add default via 192.168.1.1
    55  ping 8.8.8.8
    56  sudo reboot
    57  ip a
    58  route -n
    59  ping 8.8.8.8
    60  ping google.com
    61  route -n
    62  history 



