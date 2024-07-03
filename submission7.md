# Virtualization Lab

## Task 1: VM Deployment

![version](/images/version.png)
![memory](/images/memory.png)
![cpu](/images/cpu.png)
![network](/images/network.png)
![storage](/images/storage.png)
![vm](/images/vm.png)

## Task 2: System Information Tools

1. **Processor, RAM, and Network Information**:

`lshw`

```
ubuntu@ubuntu:~$ sudo lshw -class cpu
  *-cpu                     
       product: AMD Ryzen 5 4600H with Radeon Graphics
       vendor: Advanced Micro Devices [AMD]
       physical id: 2
       bus info: cpu@0
       version: 23.96.1
       width: 64 bits
       capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp x86-64 constant_tsc rep_good nopl nonstop_tsc cpuid extd_apicid tsc_known_freq pni pclmulqdq ssse3 cx16 sse4_1 sse4_2 x2apic movbe popcnt aes xsave avx rdrand hypervisor lahf_lm cmp_legacy cr8_legacy abm sse4a misalignsse 3dnowprefetch ssbd vmmcall fsgsbase avx2 rdseed clflushopt arat
       configuration: microcode=100664870
```

```
ubuntu@ubuntu:~$ sudo lshw -class memory
  *-firmware                
       description: BIOS
       vendor: innotek GmbH
       physical id: 0
       version: VirtualBox
       date: 12/01/2006
       size: 128KiB
       capacity: 128KiB
       capabilities: isa pci cdboot bootselect int9keyboard int10video acpi
  *-memory
       description: System memory
       physical id: 1
       size: 3GiB
```

```
ubuntu@ubuntu:~$ sudo lshw -class network
  *-network                 
       description: Ethernet interface
       product: 82540EM Gigabit Ethernet Controller
       vendor: Intel Corporation
       physical id: 3
       bus info: pci@0000:00:03.0
       logical name: enp0s3
       version: 02
       serial: 08:00:27:6b:80:6d
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm pcix bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000 driverversion=6.8.0-31-generic duplex=full ip=10.0.2.15 latency=64 link=yes mingnt=255 multicast=yes port=twisted pair speed=1Gbit/s
       resources: irq:19 memory:f0200000-f021ffff ioport:d020(size=8)
```

2. **Operating System Specifications**:

`neofetch`

![neofetch](/images/neofetch.png)
