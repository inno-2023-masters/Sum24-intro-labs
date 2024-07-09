# Lab 7 : Virtualization

## Task 1: VM Deployment
#### For this lab i installed and used Virtual Box `version 7.0`.

<img src="src/vb_version.png" alt="alt text" width="625" height="500">

#### The first step when creating the Virtual Machine is selcting an operating sytem and giving it a name, in this case i use `ubuntu 22.04`.
<img src="src/name.png" alt="alt text">

#### I then set the hardware parementers, allocating the base memeroy and the number of processors.
<img src="src/hardware.png" alt="alt text">

#### And finally i allocate the harddrive storage.
<img src="src/harddrive.png" alt="alt text">

#### Here is the running Ubuntu virtual machine.
<img src="src/vm.png" alt="alt text" width="700" height="500">


## Task 2: System Information Tools

#### I used the `lscpu` command to display my cpu information.
```sh
suwilanji@suwilanji-VirtualBox:~/Desktop$ lscpu
Architecture:            x86_64
CPU op-mode(s):        32-bit, 64-bit
Address sizes:         39 bits physical, 48 bits virtual
Byte Order:            Little Endian
CPU(s):                  4
On-line CPU(s) list:   0-3
Vendor ID:               GenuineIntel
Model name:            11th Gen Intel(R) Core(TM) i5-11400H @ 2.70GHz
CPU family:          6
Model:               141
Thread(s) per core:  1
Core(s) per socket:  4
Socket(s):           1
Stepping:            1
BogoMIPS:            5376.00
Flags:               fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fx
sr sse sse2 ht syscall nx rdtscp lm constant_tsc rep_good nopl xtopology nonstop_tsc c
puid tsc_known_freq pni pclmulqdq ssse3 cx16 pcid sse4_1 sse4_2 movbe popcnt aes rdran
d hypervisor lahf_lm abm 3dnowprefetch invpcid_single ibrs_enhanced fsgsbase bmi1 bmi2
invpcid rdseed clflushopt arat md_clear flush_l1d arch_capabilities
Virtualization features:
Hypervisor vendor:     KVM
Virtualization type:   full
Caches (sum of all):

L1d:                   192 KiB (4 instances)
L1i:                   128 KiB (4 instances)
L2:                    5 MiB (4 instances)
L3:                    48 MiB (4 instances)
NUMA:

NUMA node(s):          1
NUMA node0 CPU(s):     0-3
Vulnerabilities:

Gather data sampling:  Not affected
Itlb multihit:         Not affected
L1tf:                  Not affected
Mds:                   Not affected
Meltdown:              Not affected
Mmio stale data:       Not affected
Retbleed:              Mitigation; Enhanced IBRS
Spec rstack overflow:  Not affected
Spec store bypass:     Vulnerable
Spectre v1:            Mitigation; usercopy/swapgs barriers and __user pointer sanitization
Spectre v2:            Mitigation; Enhanced / Automatic IBRS; RSB filling; PBRSB-eIBRS SW sequence; BHI Sysca
ll hardening, KVM SW loop
Srbds:                 Not affected
Tsx async abort:       Not affected
suwilanji@suwilanji-VirtualBox:~/Desktop$
```
#### `free h` command to display the RAM information.
```sh
suwilanji@suwilanji-VirtualBox:~/Desktop$ free -h
total        used        free      shared  buff/cache   available
Mem:           2.8Gi       1.4Gi       258Mi       216Mi       1.1Gi       1.0Gi
Swap:          2.6Gi       8.0Mi       2.6Gi
suwilanji@suwilanji-VirtualBox:~/Desktop$
```
#### And `ip a` to display my network information.
```sh
suwilanji@suwilanji-VirtualBox:~/Desktop$ ip a
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
inet 127.0.0.1/8 scope host lo
valid_lft forever preferred_lft forever
inet6 ::1/128 scope host
valid_lft forever preferred_lft forever
2: enp0s3: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
link/ether 08:00:27:84:56:1c brd ff:ff:ff:ff:ff:ff
inet 10.0.2.15/24 brd 10.0.2.255 scope global dynamic noprefixroute enp0s3
valid_lft 85959sec preferred_lft 85959sec
inet6 fe80::60de:e4c2:86ef:b7de/64 scope link noprefixroute
valid_lft forever preferred_lft forever
suwilanji@suwilanji-VirtualBox:~/Desktop$
```
#### To display the VM's operating system specifications I used `neofetch`.
#### I first installed it using:
```sh
sudo apt install neofetch
```
#### And then displayed my os specicifications using:
```sh
neofetch
```
<img src="src/neofetch.png" alt="alt text" width="900" height="500">
