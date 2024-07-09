# Lab 7 Virtualization

## Task 1: VM Deployment

VirtualBox version = 7.0.18 r162988 (Qt5.15.2)

1. Install VirtualBox
2. Created new virtual machine with following settings:
    - Type: Linux
    - Version: Ubuntu 22.04 LTS (Jammy Jellyfish) (64-bit)
    - Memory: 8 GB
    - CPU: 1
    - Virtual Disc: 9 GB
3. Launch virtual machine
4. In GNU GRUB select "Try or Install Linux"
5. In setup process specify language, account login and password, network.
6. After the setup process virtual machine is rebooted
7. Using my login and password I login into system.

![alt text](image.png)

## Task 2: System Information Tools

### 1. Processor

Use ``lscpu`` tool:

![alt text](image-2.png)

### 2. RAM

Use ``free`` tool:

![alt text](image-4.png)

### 3. Network Information

I use ``ifconfig`` for it, but initially it doesn't installed on virtual machine so I install it with ``sudo apt install net-tools``

![alt text](image-1.png)

### 4. Operating System

![alt text](image-5.png)