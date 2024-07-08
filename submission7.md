# Lab 7: Virtualization Lab
## Anton Buguev, a.buguev@innopolis.university, M23-RO-01

### Task 1. VM Deployment.

1. Install virtual box: 
    1. I downloaded the latest version from the official software and tried to install it. However, when I tried to laucnh VirtaulBox I got the error:
    ```sh
    WARNING: The vboxdrv kernel module is not loaded. Either there is no module
         available for the current kernel (6.5.0-41-generic) or it failed to
         load. Please recompile the kernel module and install it by

           sudo /sbin/vboxconfig

         You will not be able to start VMs until this problem is fixed.
    ```
    2. I've run the following command that allowed me to install prevoius version which worked successfully:
    ```sh
    sudo apt install --reinstall virtualbox-dkms
    ```
    3. Check VirtaulBox version:

    ```sh
    $ vboxmanage -version

    6.1.50_Ubuntur161033
    ```
    ![](images/vbox.png)

2. Deploy Virtual Machine
    1. Downloaded **Ubuntu 20** image from official [website](https://releases.ubuntu.com/focal/).
    2. Inside VirtualBox created new Virtual Machine, chose Ubuntu OS, adjusted RAM to ~10 GB, created virtual disk and selecetd it as VDI with dynamically allocated memory, adjusted storage size to 30 GB and created virtual machine.
    3. Opened settings for newly created virtual machine and increased number of CPU cores (up to 4) and video monitor memory (up to 128 MB).
    4. After that opened *Storage* in the settings and selected downloaded Ubuntu image as optical disk to install the system.
    5. Now it is time to run virtual machine and follow instructions to install ubuntu. For simplicity I chose minimal installation without downloading updates. When installation is finished, VirtualBox automatically *ejects* the optical disk which is required to fully finish installation and restart the system.

    You can see running VM on the image below with my profile in the terminal:
    ![](images/vm_running.png)

### Task 2. System Information Tools.

1. Processor, RAM and Network information:
    1. Processor information
        ```sh
        $ lscpu
        
        Architecture:                       x86_64
        CPU op-mode(s):                     32-bit, 64-bit
        Byte Order:                         Little Endian
        Address sizes:                      48 bits physical, 48 bits virtual
        CPU(s):                             4
        ```
        We can see that there is indeed only 4 cores available (as on screenshot above).
    
    2. RAM information
        ```sh
        $ free -m
                      total        used        free      shared  buff/cache   available
        Mem:          10012        1475        7040          31        1497        8256
        Swap:          1401           0        1401
        ```
        We can see that there is indeed ~10 GB of RAM available (as on screenshot above).

    3. Network information
        ```sh
        $ sudo apt install net-tools
        $ ifconfig

        enp0s3: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
                inet 10.0.2.15  netmask 255.255.255.0  broadcast 10.0.2.255
                inet6 fe80::c130:ef57:f808:443d  prefixlen 64  scopeid 0x20<link>
                ether 08:00:27:39:b2:4f  txqueuelen 1000  (Ethernet)
                RX packets 284  bytes 263118 (263.1 KB)
                RX errors 0  dropped 0  overruns 0  frame 0
                TX packets 214  bytes 36127 (36.1 KB)
                TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
        
        lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
                inet 127.0.0.1  netmask 255.0.0.0
                inet6 ::1  prefixlen 128  scopeid 0x10<host>
                loop  txqueuelen 1000  (Local Loopback)
                RX packets 154  bytes 13398 (13.3 KB)
                RX errors 0  dropped 0  overruns 0  frame 0
                TX packets 154  bytes 13398 (13.3 KB)
                TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
        ```
        Here we can see device IP address (10.0.2.15) as well as other network information.

2. Operating system specifications:
    ```sh
    $ cat /etc/os-release

    NAME="Ubuntu"
    VERSION="20.04.6 LTS (Focal Fossa)"
    ID=ubuntu
    ID_LIKE=debian
    PRETTY_NAME="Ubuntu 20.04.6 LTS"
    VERSION_ID="20.04"
    HOME_URL="https://www.ubuntu.com/"
    SUPPORT_URL="https://help.ubuntu.com/"
    BUG_REPORT_URL="https://bugs.launchpad.net/ubuntu/"
    PRIVACY_POLICY_URL="https://www.ubuntu.com/legal/terms-and-policies/privacy-policy"
    VERSION_CODENAME=focal
    UBUNTU_CODENAME=focal
    ```
Here we can see the information about installed operating system.
