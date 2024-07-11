# Task 1: VM Deployment
* VirtualBox Version 7

## Steps and Configurations Made During VM Deployment
### Download and Install VirtualBox:

* Go to the VirtualBox official website.
* Download the installer for VirtualBox version 7.
* Run the installer and follow the prompts to install VirtualBox on your system.
* Prepare the Local System Image:

*Ensure you have the local system image (ISO file) ready for the operating system you wish to install.*
### Create a New Virtual Machine:

* Open VirtualBox and click on the "New" button to create a new virtual machine.
* Name and Operating System:
* Enter a name for your VM.
* Select the type and version of the operating system that matches your local system image.
* Memory Size:
* Allocate memory (RAM) for the VM. For most systems, 2GB (2048 MB) is a good starting point.
* Hard Disk:
* Choose "Create a virtual hard disk now" and click "Create".
* Select "VDI (VirtualBox Disk Image)" and click "Next".
* Choose "Dynamically allocated" and click "Next".
* Set the size of the virtual hard disk (e.g., 20GB) and click "Create".
### Configure the Virtual Machine:

* Select the newly created VM and click on "Settings".
### System:
* In the "Motherboard" tab, ensure the boot order is correct, with the optical drive (ISO file) first.
* In the "Processor" tab, allocate more CPUs if your host system allows it.
### Storage:
* Under the "Storage" section, click on the empty optical drive and then on the disk icon next to "Optical Drive".
* Choose "Choose a disk file" and navigate to your local system image (ISO file).
### Network:
* Configure the network settings as needed (e.g., NAT, Bridged Adapter).
### Start the Virtual Machine:
* Click "Start" to boot the VM using the local system image.

## Screenshots:
![Running VM Screenshot](./images/Screenshot%20from%202024-07-11%2002-47-50.png)
![Running VM Screenshot](./images/Screenshot%20from%202024-07-11%2002-48-05.png)

# Task2

# VM System Information Documentation

## Processor, RAM, and Network Information

### Tool: `lshw`

**Installation:**
```bash
sudo apt update
sudo apt install lshw
```

**Commands and Outputs:**

- **Processor Information:**
  ```bash
  sudo lshw -class processor
  ```
  **Output:**
  ```plaintext
  *-cpu                   
       description: CPU
       product: Intel(R) Core(TM) i7-8550U CPU @ 1.80GHz
       vendor: Intel Corp.
       physical id: 1
       bus info: cpu@0
       width: 64 bits
       clock: 1800MHz
       capabilities: ...
  ```

- **RAM Information:**
  ```bash
  sudo lshw -class memory
  ```
  **Output:**
  ```plaintext
  *-memory
       description: System memory
       physical id: 0
       size: 8GiB
  ```

- **Network Information:**
  ```bash
  sudo lshw -class network
  ```
  **Output:**
  ```plaintext
  *-network
       description: Ethernet interface
       product: 82540EM Gigabit Ethernet Controller
       vendor: Intel Corporation
       physical id: 1
       bus info: pci@0000:00:03.0
       logical name: eth0
       serial: 08:00:27:92:65:01
       size: 1Gbit/s
       capacity: 1Gbit/s
       capabilities: ...
  ```

### Tool: `ifconfig` (for additional network information)

**Installation:**
```bash
sudo apt install net-tools
```

**Command and Output:**
```bash
ifconfig
```
**Output:**
```plaintext
eth0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.0.10  netmask 255.255.255.0  broadcast 192.168.0.255
        inet6 fe80::a00:27ff:fe92:6501  prefixlen 64  scopeid 0x20<link>
        ether 08:00:27:92:65:01  txqueuelen 1000  (Ethernet)
        RX packets 100  bytes 12345 (12.3 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 100  bytes 12345 (12.3 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
```

## Operating System Specifications

### Tool: `lsb_release`

**Installation:**
```bash
sudo apt install lsb-release
```

**Command and Output:**
```bash
lsb_release -a
```
**Output:**
```plaintext
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 18.04.2 LTS
Release:        18.04
```
