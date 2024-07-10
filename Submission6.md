# Analyze System Boot Time:
1. `system-analyze` command
```bash
Startup finished in 4.127s (firmware) + 1.172s (loader) + 1.589s (kernel) + 9.112s (userspace) = 16.000s 
graphical.target reached after 9.070s in userspace
```

2. `systemd-analyze blame` command
```bash
6.453s NetworkManager-wait-online.service
3.463s plymouth-quit-wait.service
1.129s docker.service
796ms fwupd.service
 ...
 ...
 ...
```

# Check System Load and Uptime:

1. `uptime` command
```bash
01:37:32 up  1:07,  1 user,  load average: 0.34, 0.33, 0.38
 ```

 2. `w` command
 ```bash
01:38:00 up  1:07,  1 user,  load average: 0.28, 0.32, 0.38
USER     TTY      FROM             LOGIN@   IDLE   JCPU   PCPU WHAT
karim    :0       :0               00:30   ?xdm?  14:55   0.00s /usr/libexec/gdm-x-session --run-script env GNOME_SHELL_SESSIO
```

# Document the Analysis
### system-analyze Command Output:

This command breaks down the boot time into different phases, such as the time taken by the firmware, bootloader, kernel, and userspace. It helps in identifying which stage of the boot process is taking the longest.

* Firmware: `4.127s` - This indicates the time taken by the BIOS/UEFI firmware to initialize hardware and hand over control to the bootloader.
* Loader: `1.172s` - The time taken by the bootloader to load the kernel.
* Kernel: `1.589s` - Time taken by the kernel to initialize the system and start the userspace initialization.
* Userspace: `9.112s` - The duration for the userspace to complete initialization. The graphical target (GUI) was reached in `9.070s`, indicating that most of * the userspace time was spent initializing services required for the graphical interface.
* The total boot time is `16.000s`, with the graphical interface being ready in just over `9` seconds.

### systemd-analyze blame Command Output:
This command provides a sorted list of all systemd services and their respective startup times. It is useful for pinpointing specific services that may be causing delays in the boot process, allowing for targeted optimizations or troubleshooting.

* NetworkManager-wait-online.service: `6.453` - This service is the most time-consuming during boot. It waits for the network to be fully configured before proceeding, which can delay the overall boot process.
* Plymouth-quit-wait.service: `3.463s` - This service handles the graphical boot splash screen and waits for it to finish, contributing significantly to the boot time.
* Docker.service: `1.129s` - Docker initialization, while relatively quick, still adds over a second to the boot process.
* fwupd.service: `796ms` - This service is responsible for updating firmware and adds a moderate delay.
* etc... 

### uptime Command Output:
This command provides a quick summary of the system's operational status, showing how long the system has been running since the last boot and indicating the average system load over the past 1, 5, and 15 minutes.
* Current Time: `01:37:32`
* Uptime: 1 hour and 7 minutes - The system has been running for just over an hour.
* Load Average: `0.34, 0.33, 0.38` - The load averages over the last 1, 5, and 15 minutes, respectively. These values are well below 1.0, indicating a lightly loaded system.

### w Command Output:
This command displays detailed information about users currently logged into the system, including their login time, terminal, remote host, idle time, JCPU (total CPU time used by all processes attached to the terminal), and PCPU (CPU time used by the current process). It also provides the system uptime and load averages, similar to the uptime command.

* Current Time: `01:38:00`
* Uptime: 1 hour and 7 minutes - Consistent with the uptime command.
* Load Average: `0.28, 0.32, 0.38` - Slightly lower than the values seen in the uptime command, indicating very little activity in the few seconds between commands.
* Users Logged In: 1 user (karim)
* TTY: :0 - Indicates the user is logged in via the graphical interface (GNOME session).
* Login Time: `00:30` - The user logged in around 30 minutes after the system booted.
* Idle Time: Unknown (represented by ?xdm?).
* JCPU: `14:55` - Total CPU time used by all processes attached to the terminal.
* PCPU: `0.00s` - CPU time used by the current process (/usr/libexec/gdm-x-session).


## Insights and Observations:
### Boot Time:

The system's total boot time of 16 seconds is reasonably efficient, though the time taken by the NetworkManager-wait-online.service `(6.453s)` and plymouth-quit-wait.service `(3.463s)` are significant contributors to the delay.
Optimizations could focus on reducing the wait time for network initialization and potentially streamlining the graphical boot process.

### System Load:

The load averages are consistently low, indicating the system is not under significant stress.
A load average well below `1.0` is typical for a system with minimal activity or few active processes.
### Uptime:

The system has been running for a little over an hour, suggesting it was recently rebooted or powered on.
Only one user is logged in, and they have been active for about an hour, mostly using the GNOME graphical interface.

