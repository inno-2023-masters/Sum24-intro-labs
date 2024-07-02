# Lab 6. Operating Systems & Networking Lab

## Task 1. Operating System Analysis

1. Booth time of Ubuntu server is 9.087s.

```bash
root@dimoninbirsk:~# systemd-analyze
Startup finished in 4.161s (kernel) + 4.925s (userspace) = 9.087s
graphical.target reached after 4.886s in userspace
```
As for the most time consuming processes to load the system:
1. 2.198s | ifupdown-pre.service
2. 2.178s | dev-vda2.device
3. 1.286s | tuned.service
4. 1.245s | certbot.service
5. 870ms  | apt-daily-upgrade.service

```bash
root@dimoninbirsk:~# systemd-analyze blame
2.198s ifupdown-pre.service
2.178s dev-vda2.device
1.286s tuned.service
1.245s certbot.service
 870ms apt-daily-upgrade.service
 751ms networkd-dispatcher.service
 743ms apt-daily.service
 617ms pollinate.service
 572ms docker.service
 491ms keyboard-setup.service
 483ms systemd-udev-trigger.service
 385ms systemd-logind.service
 329ms apport.service
 289ms systemd-journald.service
 281ms systemd-timesyncd.service
 281ms systemd-udevd.service
 204ms containerd.service
 204ms multipathd.service
 202ms apparmor.service
 201ms user@0.service
 197ms dev-hugepages.mount
 195ms dev-mqueue.mount
 194ms sys-kernel-debug.mount
```

2. My VPS server already work 35 days
```bash
root@dimoninbirsk:~# uptime
 10:35:35 up 35 days, 20:47,  1 user,  load average: 0.00, 0.00, 0.00
```

And currently there one user that logged in.

```bash
root@dimoninbirsk:~# w
 10:36:41 up 35 days, 20:48,  1 user,  load average: 0.00, 0.00, 0.00
USER     TTY      FROM             LOGIN@   IDLE   JCPU   PCPU WHAT
root     pts/0    188.130.155.182  10:18    1.00s  0.05s  0.01s w
```

