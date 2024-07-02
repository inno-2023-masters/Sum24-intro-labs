# Lab 6: Operating Systems & Networking Lab
## Anton Buguev, a.buguev@innopolis.university, M23-RO-01

### Task 1. Operating System Analysis.

1. Analyze system boot time
```sh
$ systemd-analyze 

Startup finished in 11.128s (firmware) + 2.438s (loader) + 4.514s (kernel) + 27.364s (userspace) = 45.446s 
graphical.target reached after 25.521s in userspace
```

```sh
$ systemd-analyze blame 

21.361s plymouth-quit-wait.service
 6.237s NetworkManager-wait-online.service
 2.799s systemd-timesyncd.service
  943ms docker.service
  893ms snapd.seeded.service
  826ms fwupd.service
  682ms snapd.service
  538ms dev-loop1.device
  538ms dev-loop3.device
  537ms dev-loop4.device
  537ms dev-loop2.device
  537ms dev-loop0.device
  536ms dev-loop7.device
  534ms dev-loop6.device
  534ms dev-loop5.device
  456ms dev-nvme0n1p2.device
  270ms networkd-dispatcher.service
  260ms systemd-udev-trigger.service
  248ms accounts-daemon.service
  238ms systemd-logind.service
  229ms bluetooth.service
  214ms upower.service
  214ms systemd-resolved.service
  193ms user@1000.service
  191ms systemd-oomd.service
  173ms e2scrub_reap.service
  169ms ModemManager.service
```
From these outputs we can analyze how much time it takes to boot the system and which processes took the most of the time.

2. System load and uptime:
```sh
$ uptime 

 17:06:15 up  1:46,  1 user,  load average: 0.53, 0.57, 0.62
```

```sh
$ w

 17:06:16 up  1:46,  1 user,  load average: 0.53, 0.57, 0.62
USER     TTY      FROM             LOGIN@   IDLE   JCPU   PCPU WHAT
anton    tty2     tty2             15:20    1:46m  0.04s  0.04s /usr/libexec/gnome-session-binary --session=
```

From this output we can understand how many users are currently logged in.