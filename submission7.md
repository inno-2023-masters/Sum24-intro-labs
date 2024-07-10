## Task 1: VM Deployment

### VirtualBox Version

- Version 6.1.34 r150636 (Qt5.6.2)

### Steps to Deploy a VM

1. Download Ubuntu ISO from the [Ubuntu website](https://ubuntu.com/download).(Choose desktop LTS 24.04)
2. Open VirtualBox and click on "New".
3. Name the VM "UbuntuVM", select "Linux" as the type, and choose "Ubuntu (64-bit)" as the version. Click "Next".
4. Allocate 4096 MB (4 GB) of RAM and click "Next".
5. Choose "Create a virtual hard disk now", then select "VDI (VirtualBox Disk Image)" and "Dynamically allocated". Set the disk size to 20 GB and click "Create".
6. Go to "Settings", under "System" > "Processor", allocate 2 CPU cores. Under "Network", ensure Adapter 1 is attached to "NAT".
7. Start the VM, select the Ubuntu ISO file, and follow the installation instructions.

### Screenshot

![Ubuntu VM Running](/media/ubuntuVM.png)

Observations:
There was some problems with network settings it is requered to set Wired NAT connection for my laptop configuration
I also decided to try ubuntu dualboot:
![Ubuntu Dualboot Running](/media/ubuntuDualBoot.png)

## Task 2: System Information Tools

### 1. Processor, RAM, and Network Information

**Tool Used**: `lshw` (Hardware Lister)

**Installation**:

```sh
sudo apt-get install lshw
```

**Commands and Output**:

```sh
sudo lshw -class processor
```

```plaintext
  *-cpu
       description: CPU
       product: Intel(R) Core(TM) i7-8550U CPU @ 1.80GHz
       vendor: Intel Corp.
       physical id: 3
       bus info: cpu@0
       size: 1992MHz
       capacity: 4000MHz
       width: 64 bits
```

```sh
sudo lshw -class memory
```

```plaintext
  *-memory
       description: System memory
       physical id: 0
       size: 4096MiB
```

```sh
sudo lshw -class network
```

```plaintext
  *-network
       description: Ethernet interface
       product: 82540EM Gigabit Ethernet Controller
       vendor: Intel Corporation
       physical id: 1
       logical name: enp0s3
       serial: 08:00:27:1b:9a:bb
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 32 bits
```

### 2. Operating System Specifications

**Tool Used**: `lsb_release`

**Installation**:

```sh
sudo apt-get install lsb-release
```

**Command and Output**:

```sh
lsb_release -a
```

```plaintext
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 20.04.3 LTS
Release:        20.04
Codename:       focal
```

## Conclusion

This lab provided practical experience in deploying a VM using VirtualBox and exploring system information tools within the VM. The steps and commands documented in `submission7.md` serve as a reference for setting up and analyzing a VM environment.
