# Lab 6 : Operating Systems & Networking Lab

## Task 1: Operating System Analysis

1. **Analyze System Boot Time**:
   - Using `systemd-analyze` + `blame` shows my system boot time and the time it takes for my services to start up, Below we can see that the service that takes the longest time is `snapd.seeded.service`.

     ```sh
        suwilanji@SUWILANJI-PCV3:~$ systemd-analyze
        systemd-analyze blame
        Startup finished in 1.009s (userspace)
        graphical.target reached after 999ms in userspace
        561ms snapd.seeded.service
        435ms snapd.service
        407ms networkd-dispatcher.service
        356ms logrotate.service
        295ms dev-sdc.device
        200ms systemd-resolved.service
        125ms user@1000.service
        89ms systemd-logind.service
        81ms apport.service
        74ms systemd-journal-flush.service
        72ms e2scrub_reap.service
        59ms systemd-udev-trigger.service
        55ms systemd-udevd.service
        46ms keyboard-setup.service
        44ms systemd-journald.service
        39ms systemd-user-sessions.service
        33ms dev-hugepages.mount
        32ms dev-mqueue.mount
        31ms rsyslog.service
        31ms sys-kernel-debug.mount
        29ms sys-kernel-tracing.mount
        22ms snap-bare-5.mount
        20ms snap-core22-1122.mount
        20ms systemd-tmpfiles-setup-dev.service
        20ms modprobe@configfs.service
        19ms snap-core22-1380.mount
        19ms modprobe@drm.service
        18ms modprobe@efi_pstore.service
        18ms modprobe@fuse.service
        16ms systemd-remount-fs.service
        16ms snap-gtk\x2dcommon\x2dthemes-1535.mount
        16ms systemd-sysctl.service
        15ms systemd-tmpfiles-setup.service
        14ms plymouth-quit.service
        13ms snap-snapd-21465.mount
        13ms plymouth-read-write.service
        12ms systemd-sysusers.service
        11ms snap-snapd-21759.mount
        10ms user-runtime-dir@1000.service
        10ms plymouth-quit-wait.service
        7ms snap-ubuntu\x2ddesktop\x2dinstaller-1284.mount
        7ms snap-ubuntu\x2ddesktop\x2dinstaller-1286.mount
        7ms setvtrgb.service
        6ms wsl-binfmt.service
        6ms systemd-update-utmp.service
        6ms console-setup.service
        4ms systemd-update-utmp-runlevel.service
        3ms snap.mount
        3ms e2scrub_all.service
        3ms ufw.service
        3ms sys-fs-fuse-connections.mount
        3ms snapd.socket
        lines 24-52/52 (END)
     ```

2. **Check System Load and Uptime**:
   - Using `uptime` and `w` we can see the system load and uptime. Here we see my system has been up for 8 minutes and has a very low average load. And with the `w` command we can see what every user is up to, in this case only one user is logged on.

     ```sh
        suwilanji@SUWILANJI-PCV3:~$ uptime
        16:07:11 up 8 min,  1 user,  load average: 0.00, 0.04, 0.03
        suwilanji@SUWILANJI-PCV3:~$ w
        16:07:17 up 8 min,  1 user,  load average: 0.00, 0.03, 0.02
        USER     TTY      FROM             LOGIN@   IDLE   JCPU   PCPU WHAT
        suwilanj pts/1    -                15:59    7:47   0.05s  0.03s -bash
        suwilanji@SUWILANJI-PCV3:~$
     ```

## Task 2: Networking Analysis

**Objective**: Perform network diagnostics and analyze DNS resolution to understand network paths and latency.

1. **Traceroute**:
   - Traceroute provides a map of how data on the internet moves from its source to its destination.It's helpful for figuring out the routing paths data has to go through, as well as response delays as it travels. The report below shows a traceroute of `youtube.com`. The report lists data pertaining to every router the packets pass through as they head to their destination. We have the ip addresses as well as three time measurements which show the lentency send packets from your my machine to that router and back.

     ```sh
        suwilanji@SUWILANJI-PCV3:~$ traceroute youtube.com
        traceroute to youtube.com (108.177.14.93), 64 hops max
        1   172.27.0.1  0.312ms  0.174ms  0.182ms
        2   10.242.1.1  0.782ms  0.622ms  0.634ms
        3   10.250.0.2  0.978ms  1.030ms  0.793ms
        4   10.252.6.1  1.421ms  1.193ms  1.319ms
        5   84.18.123.1  15.935ms  14.410ms  20.436ms
        6   188.170.164.138  22.294ms  19.087ms  18.507ms
        7   *  *  *
        8   108.177.14.93  54.281ms  53.699ms  53.590ms
        suwilanji@SUWILANJI-PCV3:~$
     ```

2. **Dig**:
   - Below i perform a DNS lookup for `youtube.com`. The `Header` section shows the DNS query and response details.

     ```sh
        suwilanji@SUWILANJI-PCV3:~$ dig youtube.com

        ; <<>> DiG 9.18.24-0ubuntu0.22.04.1-Ubuntu <<>> youtube.com
        ;; global options: +cmd
        ;; Got answer:
        ;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 65008
        ;; flags: qr rd ad; QUERY: 1, ANSWER: 4, AUTHORITY: 0, ADDITIONAL: 0
        ;; WARNING: recursion requested but not available

        ;; QUESTION SECTION:
        ;youtube.com.                   IN      A

        ;; ANSWER SECTION:
        youtube.com.            0       IN      A       64.233.163.136
        youtube.com.            0       IN      A       64.233.163.190
        youtube.com.            0       IN      A       64.233.163.91
        youtube.com.            0       IN      A       64.233.163.93

        ;; Query time: 0 msec
        ;; SERVER: 172.27.0.1#53(172.27.0.1) (UDP)
        ;; WHEN: Tue Jul 02 16:29:34 MSK 2024
        ;; MSG SIZE  rcvd: 104

        suwilanji@SUWILANJI-PCV3:~$
     ```
   - Adding the `+trace` tag shows the path from the root DNS servers to the authoritative servers for the domain.
     ```sh
        suwilanji@SUWILANJI-PCV3:~$ dig +trace youtube.com

        ; <<>> DiG 9.18.24-0ubuntu0.22.04.1-Ubuntu <<>> +trace youtube.com
        ;; global options: +cmd
        .                       18913   IN      NS      a.root-servers.net.
        .                       18913   IN      NS      g.root-servers.net.
        .                       18913   IN      NS      c.root-servers.net.
        .                       18913   IN      NS      m.root-servers.net.
        .                       18913   IN      NS      f.root-servers.net.
        .                       18913   IN      NS      i.root-servers.net.
        .                       18913   IN      NS      l.root-servers.net.
        .                       18913   IN      NS      j.root-servers.net.
        .                       18913   IN      NS      b.root-servers.net.
        .                       18913   IN      NS      h.root-servers.net.
        .                       18913   IN      NS      e.root-servers.net.
        .                       18913   IN      NS      d.root-servers.net.
        .                       18913   IN      NS      k.root-servers.net.
        ;; Received 527 bytes from 172.27.0.1#53(172.27.0.1) in 870 ms

        ;; Received 40 bytes from 192.33.4.12#53(d.root-servers.net) in 60 ms

        suwilanji@SUWILANJI-PCV3:~$
     ```