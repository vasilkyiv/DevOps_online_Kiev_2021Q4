
[DevOps_online_Kiev_2021Q4 (MY GITHUB URL REPO)](https://github.com/vasilkyiv/DevOps_online_Kiev_2021Q4.git)
=======================================

************************************************************************
[MODULE 02](https://github.com/vasilkyiv/DevOps_online_Kiev_2021Q4/tree/main/m2) 
===========================================================================
> - [TASK_2.1](https://github.com/vasilkyiv/DevOps_online_Kiev_2021Q4/tree/main/m2)

### PART 1. HYPERVISORS 
1. What are the most popular hypervisors for infrastructure virtualization?
> 1. [proxmox-ve](https://www.proxmox.com/en/proxmox-ve)
> 2. [vmware esx](https://docs.vmware.com/en/vCenter-Converter-Standalone/6.2/com.vmware.convsa.guide/GUID-668740BF-2161-4EF4-870B-B014FCA660BA.html)
> 3. [aws](https://aws.amazon.com/)
> 4. [google](https://cloud.google.com/compute)
> 5. [oracle](https://datastore.net.ua/servisy/it-infrastruktura-v-hmari/?gclid=CjwKCAiA1aiMBhAUEiwACw25MfxsM2fPbCaHp7GZHUdND6_v0Y4rXQCCBW8dq1ATuDsQ0CgqHrgpbRoCIhEQAvD_BwE)
> 6. [citrix](https://www.citrix.com/solutions/vdi-and-daas/what-is-vdi-virtual-desktop-infrastructure.html)
> 6. [openvz](https://openvz.org/)

2. Briefly describe the main differences of the most popular hypervisors?
> - https://www.ibm.com/cloud/learn/hypervisors


 
=======
### PART 2. WORK WITH VIRTUALBOX ###

 # 1. First run VirtualBox and Virtual Machine (VM).
> 1.1 Get acquainted with the structure of the user manual VirtualBox [1] (see list of references in the end of the document)

> 1.2 From the official VirtualBox site [2] download the latest stable version of VirtualBox according to the host operating system (OS) installed on the student's workplace. For Windows, the file may be called, for example, VirtualBox-6.1.10-138449-Win.exe. Install VirtualBox.

> 1.3 Download the latest stable version of Ubuntu Desktop or Ubuntu Server from the official site [3].

> 1.4 Create VM1 and install Ubuntu using the instructions [1, chapter 1.8]. Set machine name as "host machine name"_"student last name"

[![*Report in screenshots*](shreenshot/1.png?raw=true)](https://github.com/vasilkyiv/DevOps_online_Kiev_2021Q4/tree/main/m2/task2.1/shreenshot/1.png)

> 1.5 Get acquainted with the possibilities of VM1 control - start, stop, reboot, save state, use Host key and keyboard shortcuts, mouse capture, etc. [1, ch.1.9].

> 1.6 Clone an existing VM1 by creating a VM2 [1, ch.1.14].

[![*Report in screenshots*](shreenshot/2.png?raw=true)](https://github.com/vasilkyiv/DevOps_online_Kiev_2021Q4/tree/main/m2/task2.1/shreenshot/2.png)

> 1.7 Create a group of two VM: VM1, VM2 and learn the functions related to groups [1, ch.1.10].

[![*Report in screenshots*](shreenshot/3.png?raw=true)](https://github.com/vasilkyiv/DevOps_online_Kiev_2021Q4/tree/main/m2/task2.1/shreenshot/3.png)

> 1.8 For VM1, changing its state, take several different snapshots, forming a branched tree of snapshots [1, ch.1.11].

[![*Report in screenshots*](shreenshot/5.png?raw=true)](https://github.com/vasilkyiv/DevOps_online_Kiev_2021Q4/tree/main/m2/task2.1/shreenshot/5.png)

> 1.9 Export VM1. Save the *.ova file to disk. Import VM from *.ova file [1, ch.1.15].

[![*Report in screenshots*](shreenshot/6.png?raw=true)](https://github.com/vasilkyiv/DevOps_online_Kiev_2021Q4/tree/main/m2/task2.1/shreenshot/6.png)

# 2. Configuration of virtual machines
> 2.1 Explore VM configuration options (general settings, system settings, display, storage, audio, network, etc.).

> 2.2 Configure the USB to connect the USB ports of the host machine to the VM [1, ch.3.11].

> 2.3 Configure a shared folder to exchange data between the virtual machine and the host [1, ch.4.3].

[![*Report in screenshots*](shreenshot/11.png?raw=true)](https://github.com/vasilkyiv/DevOps_online_Kiev_2021Q4/tree/main/m2/task2.1/shreenshot/11.png)

> 2.4 Configure different network modes for VM1, VM2. Check the connection between VM1, VM2, Host, Internet for different network modes. You can use the ping command to do this. Make a table of possible connections.

> 3. Work with CLI through VBoxManage.
> 3.1 Run the cmd.exe command line.
> 3.2 Examine the purpose and execute the basic commands of VBoxManage list, showvminfo, createvm, startvm, modifyvm, clonevm, snapshot, controlvm [1, ch.8].

[![*Report in screenshots*](shreenshot/7.png?raw=true)](https://github.com/vasilkyiv/DevOps_online_Kiev_2021Q4/tree/main/m2/task2.1/shreenshot/7.png)

# 3. PART 3. WORK WITH VAGRANT

> 1. Download the required version of Vagrant according to the instructions [5] and according to the host operating system (OS) installed on the student's workplace. For Windows, the file may be called, for example, vagrant_2.2.0_x86_64.msi. Install Vagrant. Check the path to Vagrant bin in the Path variable (My computer -> Properties -> Advanced system settings -> Advanced -> Environment Variables).

> 2. Run the powershell. Create a folder "student name" (in English). In this example, create a folder vagrant_test. Next, go to the folder.

> 3. Initialize the environment with the default Vagrant box: init hashicorp/precise64

> 4. Run vagrant up and watch for messages during VM boot and startup.

[![*Report in screenshots*](shreenshot/8.png?raw=true)](https://github.com/vasilkyiv/DevOps_online_Kiev_2021Q4/tree/main/m2/task2.1/shreenshot/8.png)

> 5. Connect to the VM using the program PuTTY (can be downloaded from [6]), using SSH, IP address and port listed above (127.0.0.1:2222). By default, login - vagrant and password are also vagrant

[![*Report in screenshots*](shreenshot/9.png?raw=true)](https://github.com/vasilkyiv/DevOps_online_Kiev_2021Q4/tree/main/m2/task2.1/shreenshot/9.png)