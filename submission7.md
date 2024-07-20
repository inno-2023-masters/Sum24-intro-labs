# Submission for Lab 7

## Task 1

### VirtualBox Version

**Version: 7.0.10**

![VB Versuin](/Resources/vbversion.png)

### VM Deployment

* VM was created by selecting the new option in VirtualBox
* The VM was given 6 logical cores and 8GB of ram. Everything else was left as the default.

![System Memory](/Resources/sysmem.png)
![System Cpu](/Resources/sysprocessor.png)
> Note: Settings are shaded here because I took the screenshot while the VM was running.

![VM](/Resources/vm.png)

## Task 2

### CPU info tool

`lscpu` was used to display CPU info, and didn't require any package installation.

![CPU Info](/Resources/lscpu.png)

### Memory info tool

`free` was used to display memory info, and didn't require any package installation. It was also ran with the `-h` option to make the output human readable.

![Memory Info](/Resources/free.png)

### Network info tool

`ip` was used with the `address` command (shortened to just `a`) to display the network information, and didn't require any package installation.

![Network Info](/Resources/ip%20a.png)

### Operation system info

`lsb_release` was used to display OS info with `-a` option to show all available info, and didn't require any package installation.

![OS Info](/Resources/lsb_release.png)
