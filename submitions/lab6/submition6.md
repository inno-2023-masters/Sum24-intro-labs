# Lab6

## Task 1

1. `system-analize`
    ```
     wat4er@wat4er  ~/Master/devops/Sum24-intro-labs   master  systemd-analyze
    Startup finished in 8.733s (firmware) + 1.661s (loader) + 10.869s (kernel) + 36.645s (userspace) = 57.909s 
    graphical.target reached after 36.644s in userspace.
     wat4er@wat4er  ~/Master/devops/Sum24-intro-labs   master  systemd-analyze blame 
    30.165s NetworkManager-wait-online.service
    2.318s systemd-modules-load.service
    1.683s NetworkManager.service
    1.250s docker.service
    822ms systemd-fsck@dev-disk-by\x2duuid-54690d56\x2da064\x2d4418\x2d8541\x2dc51a089e0c5a.service
    547ms dev-disk-by\x2duuid-497791ab\x2d6339\x2d4e9b\x2dbd3d\x2d574da9f614ae.device
    387ms systemd-backlight@backlight:intel_backlight.service
    359ms udisks2.service
    357ms systemd-udev-trigger.service
    331ms home-manager-wat4er.service
    230ms user@1000.service
    205ms firewall.service
    194ms systemd-journal-flush.service
    190ms mount-pstore.service
    174ms systemd-tmpfiles-clean.service
    170ms systemd-journald.service
    153ms systemd-tmpfiles-setup-dev-early.service
    145ms systemd-pstore.service
    145ms systemd-remount-fs.service
    137ms upower.service
    135ms accounts-daemon.service
    119ms run-media-wat4er-porn.mount
    113ms modprobe@efi_pstore.service
    110ms bluetooth.service
    104ms dbus.service
    97ms modprobe@fuse.service
    96ms boot.mount
    95ms suid-sgid-wrappers.service
    85ms modprobe@drm.service
    83ms systemd-timesyncd.service
    77ms systemd-random-seed.service
    73ms modprobe@configfs.service
    71ms kmod-static-nodes.service
    67ms systemd-backlight@leds:dell::kbd_backlight.service
    66ms resolvconf.service
    64ms dev-mqueue.mount
    64ms sys-kernel-debug.mount
    63ms cups.service
    63ms dev-hugepages.mount
    62ms polkit.service
    62ms ModemManager.service
    60ms systemd-rfkill.service
    53ms systemd-fsck@dev-disk-by\x2duuid-2049\x2d091F.service
    51ms alsa-store.service
    48ms systemd-logind.service
    47ms network-setup.service
    42ms power-profiles-daemon.service
    39ms nvidia-persistenced.service
    38ms systemd-tmpfiles-setup.service
    38ms systemd-oomd.service
    37ms systemd-udevd.service
    35ms systemd-update-utmp.service
    32ms systemd-vconsole-setup.service
    30ms systemd-sysctl.service
    29ms audit.service
    28ms logrotate-checkconf.service
    25ms systemd-boot-random-seed.service
    21ms wpa_supplicant.service
    19ms network-local-commands.service
    17ms NetworkManager-dispatcher.service
    17ms systemd-tmpfiles-setup-dev.service
    15ms user-runtime-dir@1000.service
    15ms systemd-user-sessions.service
    13ms sys-fs-fuse-connections.mount
    13ms sys-kernel-config.mount
    12ms display-manager.service
    9ms nscd.service
    7ms rtkit-daemon.service
    1ms docker.socket
    ```
    - My system loads in a minute (which is about right)
    - The longest service to load is "NetworkManager-wait-online.service"

2. `uptime`
    ```
    wat4er@wat4er  ~/Master/devops/Sum24-intro-labs   master  uptime     
    04:38:44  up 4 days  8:26,  1 user,  load average: 0,42, 0,82, 1,28
    ```
    - Shows how long is system up
    - Shows some "magic numbers" is load average 

3. `w`
    ```
    wat4er@wat4er  ~/Master/devops/Sum24-intro-labs   master  w                       
    04:38:48 up 4 days,  8:26,  1 user,  load average: 0,42, 0,82, 1,28
    USER     TTY        LOGIN@   IDLE   JCPU   PCPU WHAT
    wat4er   tty3      Вт20    4days  0.49s  0.49s /nix/store/sapa40f2ki28y1l2x1qnd07lwvk28j9d-plasma-workspace-6.0.5.1/bin/startplasma-wayland
    ```
    - `w` provides an extended wersion of `uptime` command

## Task 2

1. Install traceroute and dig
    ```nix
    # configuration.nix
    environment.systemPackages = with pkgs; [
        ...
        traceroute
        dig
    ];
    ```

2. traceroute
    ```
    traceroute google.com 
    traceroute to google.com (216.239.38.120), 30 hops max, 60 byte packets
    1  _gateway (10.248.1.1)  1.404 ms  1.526 ms  1.638 ms
    2  10.250.0.2 (10.250.0.2)  0.500 ms  0.486 ms  0.471 ms
    3  10.252.6.1 (10.252.6.1)  0.966 ms  0.839 ms  1.122 ms
    4  1.123.18.84.in-addr.arpa (84.18.123.1)  10.343 ms  10.563 ms  10.433 ms
    5  188.170.164.138 (188.170.164.138)  22.837 ms  23.050 ms  23.294 ms
    6  * * *
    7  * * *
    8  * * *
    9  83.169.204.113 (83.169.204.113)  24.442 ms 83.169.204.115 (83.169.204.115)  23.827 ms 83.169.204.117 (83.169.204.117)  23.656 ms
    10  178.176.152.61 (178.176.152.61)  32.130 ms 72.14.222.181 (72.14.222.181)  22.982 ms  23.290 ms
    11  192.178.241.61 (192.178.241.61)  25.389 ms 108.170.250.51 (108.170.250.51)  24.041 ms 192.178.241.157 (192.178.241.157)  22.708 ms
    12  192.178.241.66 (192.178.241.66)  26.185 ms 192.178.241.70 (192.178.241.70)  23.598 ms 192.178.241.146 (192.178.241.146)  24.080 ms
    13  142.251.238.70 (142.251.238.70)  41.042 ms 142.251.237.154 (142.251.237.154)  40.355 ms 209.85.255.136 (209.85.255.136)  40.897 ms
    14  72.14.232.190 (72.14.232.190)  41.220 ms 216.239.58.69 (216.239.58.69)  39.110 ms 172.253.79.113 (172.253.79.113)  40.424 ms
    15  216.239.56.113 (216.239.56.113)  41.165 ms * *
    16  * * *
    17  * * *
    18  * * *
    19  * * *
    20  * * *
    21  * * *
    22  * * *
    23  * * *
    24  * any-in-2678.1e100.net (216.239.38.120)  40.439 ms *
    ```
    - This command shows the path to the "google.com" (I guess)
    - The most notable thing is that it provides addres of a gate way and addreses of UI DNS servers (I guess 10.250.0.2 and 10.252.6.1 are DNS since they are some what close to our network)
        ```
        ip a
        enp3s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
        link/ether d8:d0:90:04:32:6f brd ff:ff:ff:ff:ff:ff
        inet 10.248.1.20/24 brd 10.248.1.255 scope global dynamic noprefixroute enp3s0
            valid_lft 601162sec preferred_lft 601162sec
        inet6 fe80::e359:c5ea:fcf6:340d/64 scope link noprefixroute 
            valid_lft forever preferred_lft forever
        ```

3. dig
    ```
    dig google.com               

    ; <<>> DiG 9.18.27 <<>> google.com
    ;; global options: +cmd
    ;; Got answer:
    ;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 5669
    ;; flags: qr rd ra; QUERY: 1, ANSWER: 2, AUTHORITY: 0, ADDITIONAL: 1

    ;; OPT PSEUDOSECTION:
    ; EDNS: version: 0, flags:; udp: 4096
    ; COOKIE: 4735df7ed9b2e02136e2911c669c69a45c1aac35acc562ff (good)
    ;; QUESTION SECTION:
    ;google.com.                    IN      A

    ;; ANSWER SECTION:
    google.com.             47181   IN      CNAME   forcesafesearch.google.com.
    forcesafesearch.google.com. 47971 IN    A       216.239.38.120

    ;; Query time: 1 msec
    ;; SERVER: 10.90.137.30#53(10.90.137.30) (UDP)
    ;; WHEN: Sun Jul 21 04:51:32 MSK 2024
    ;; MSG SIZE  rcvd: 113

    ```