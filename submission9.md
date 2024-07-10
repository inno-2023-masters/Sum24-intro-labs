# CI/CD Lab - GitHub Actions

## Task 1: Create Your First GitHub Actions Pipeline

![ci](/images/ci.png)

## Task 2: Gathering System Information and Manual Triggering

1. **Configure a Manual Trigger**:

```
on:
  push:
  workflow_dispatch:
```

2. **Gather System Information**:

* CI file

```
- name: Gather System Information
        run: |
          sudo lshw -class cpu
          sudo lshw -class memory
          sudo lshw -class network
          cat /etc/os-release
```

* Output

![system_information](/images/system_information.png)

```
*-cpu:0
       description: CPU
       product: AMD EPYC 7763 64-Core Processor
       vendor: Advanced Micro Devices [AMD]
       physical id: 5
       bus info: cpu@0
       version: 25.1.1
       serial: None
       slot: None
       size: 2450MHz
       capacity: 3525MHz
       width: 64 bits
       clock: 100MHz
       capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp x86-64 constant_tsc rep_good nopl tsc_reliable nonstop_tsc cpuid extd_apicid aperfmperf pni pclmulqdq ssse3 fma cx16 pcid sse4_1 sse4_2 movbe popcnt aes xsave avx f16c rdrand hypervisor lahf_lm cmp_legacy svm cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw topoext invpcid_single vmmcall fsgsbase bmi1 avx2 smep bmi2 erms invpcid rdseed adx smap clflushopt clwb sha_ni xsaveopt xsavec xgetbv1 xsaves clzero xsaveerptr rdpru arat npt nrip_save tsc_scale vmcb_clean flushbyasid decodeassists pausefilter pfthreshold v_vmsave_vmload umip vaes vpclmulqdq rdpid fsrm
       configuration: microcode=4294967295
  *-cpu:1
       description: CPU
       product: Zen (None)
       vendor: None
       physical id: 6
       bus info: cpu@1
       version: AMD EPYC 7763 64-Core Processor
       serial: None
       slot: None
       size: 2450MHz
       capacity: 3525MHz
       clock: 100MHz
  *-cpu:2
       description: CPU
       product: Zen (None)
       vendor: None
       physical id: 7
       bus info: cpu@2
       version: AMD EPYC 7763 64-Core Processor
       serial: None
       slot: None
       size: 2450MHz
       capacity: 3525MHz
       clock: 100MHz
  *-cpu:3
       description: CPU
       product: Zen (None)
       vendor: None
       physical id: 8
       bus info: cpu@3
       version: AMD EPYC 7763 64-Core Processor
       serial: None
       slot: None
       size: 2450MHz
       capacity: 3525MHz
       clock: 100MHz
  *-cpu:4 DISABLED
       description: CPU [empty]
       product: (None)
       vendor: None
       physical id: 9
       version: None
       serial: None
       slot: None
  ...
  *-cpu:63 DISABLED
       description: CPU [empty]
       product: (None)
       vendor: None
       physical id: 44
       version: None
       serial: None
       slot: None
  *-firmware
       description: BIOS
       vendor: American Megatrends Inc.
       physical id: 0
       version: 090008
       date: 12/07/2018
       size: 64KiB
       capacity: 256KiB
       capabilities: isa pci pnp upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video agp ls120boot zipboot biosbootspecification
  *-memory
       description: System Memory
       physical id: 51
       size: 16GiB
     *-bank:0
          product: None
          vendor: Microsoft
          physical id: 0
          serial: None
          slot: M0
          size: 1GiB
     *-bank:1
          product: None
          vendor: Microsoft
          physical id: 1
          serial: None
          slot: M1
          size: 15GiB
     *-bank:2
          description: [empty]
          product: None
          vendor: Microsoft
          physical id: 2
          serial: None
          slot: M2
     ...
     *-bank:124
          description: [empty]
          product: None
          vendor: Microsoft
          physical id: 7c
          serial: None
          slot: M124
  *-network
       description: Ethernet interface
       physical id: 6
       logical name: eth0
       serial: 00:0d:3a:57:84:2f
       capabilities: ethernet physical
       configuration: autonegotiation=off broadcast=yes driver=hv_netvsc driverversion=6.5.0-1023-azure duplex=full firmware=N/A ip=10.1.0.56 link=yes multicast=yes
PRETTY_NAME="Ubuntu 22.04.4 LTS"
NAME="Ubuntu"
VERSION_ID="22.04"
VERSION="22.04.4 LTS (Jammy Jellyfish)"
VERSION_CODENAME=jammy
ID=ubuntu
ID_LIKE=debian
HOME_URL="https://www.ubuntu.com/"
SUPPORT_URL="https://help.ubuntu.com/"
BUG_REPORT_URL="https://bugs.launchpad.net/ubuntu/"
PRIVACY_POLICY_URL="https://www.ubuntu.com/legal/terms-and-policies/privacy-policy"
UBUNTU_CODENAME=jammy
```
