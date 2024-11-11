# Lab6

## Task 1

1. `system-analyze`
    ```
     Startup finished in 2.910s (kernel) + 26.155s (userspace) = 29.066s 
        graphical.target reached after 26.128s in userspace

    23.601s plymouth-quit-wait.service
    7.924s NetworkManager-wait-online.service
    4.350s docker.service
    2.231s gpu-manager.service
    1.403s snapd.seeded.service
    1.231s networkd-dispatcher.service
    1.226s secureboot-db.service
    1.219s snapd.service
    1.211s accounts-daemon.service
    1.208s avahi-daemon.service
    1.207s bluetooth.service
    1.202s NetworkManager.service
    1.195s apport.service
    1.188s polkit.service
    1.185s grub-common.service
    1.184s power-profiles-daemon.service
    1.174s switcheroo-control.service
    1.154s e2scrub_reap.service
    1.110s systemd-logind.service
    1.109s udisks2.service
    1.106s wpa_supplicant.service
    1.066s thermald.service
    956ms systemd-backlight@backlight:nvidia_0.service
    576ms fwupd.service
    527ms dev-sda2.device
    479ms dev-loop1.device
    479ms dev-loop4.device
    479ms dev-loop6.device
    478ms dev-loop5.device
    478ms dev-loop3.device
    478ms dev-loop2.device
    474ms dev-loop7.device
    420ms systemd-rfkill.service
    383ms dev-loop0.device
    308ms systemd-backlight@leds:platform::kbd_backlight.service
    264ms plymouth-start.service
    253ms dev-loop13.device
    252ms dev-loop12.device
    249ms systemd-udev-trigger.service
    242ms containerd.service
    237ms dev-loop8.device
    232ms dev-loop9.device
    222ms ModemManager.service
    218ms dev-loop11.device
    215ms cups.service
    215ms dev-loop10.device
    193ms systemd-udevd.service
    182ms upower.service
    167ms xl2tpd.service
    167ms systemd-journal-flush.service
    157ms user@1000.service
    135ms systemd-journald.service
    127ms rsyslog.service
    107ms docker.socket
    93ms systemd-resolved.service
    83ms apparmor.service
    82ms systemd-fsck@dev-disk-by\x2duuid-12DC\x2d0DDF.service
    71ms update-notifier-download.service
    69ms systemd-timesyncd.service
    68ms systemd-oomd.service
    55ms gdm.service
    49ms grub-initrd-fallback.service
    46ms systemd-tmpfiles-setup.service
    45ms alsa-restore.service
    43ms systemd-sysctl.service
    42ms snapd.apparmor.service
    42ms keyboard-setup.service
    39ms colord.service
    37ms systemd-modules-load.service
    36ms packagekit.service
    31ms openvpn.service
    31ms systemd-tmpfiles-clean.service
    25ms systemd-binfmt.service
    25ms systemd-sysusers.service
    23ms snap-core22-1621.mount
    22ms snap-bare-5.mount
    22ms snap-core22-1663.mount
    22ms systemd-random-seed.service
    22ms systemd-remount-fs.service
    21ms snap-core24-609.mount
    19ms snap-firefox-4848.mount
    18ms proc-sys-fs-binfmt_misc.mount
    17ms snap-gnome\x2d42\x2d2204-176.mount
    16ms snap-gtk\x2dcommon\x2dthemes-1535.mount
    14ms kerneloops.service
    14ms snap-snap\x2dstore-1113.mount
    13ms snap-snap\x2dstore-1216.mount
    13ms dev-hugepages.mount
    12ms boot-efi.mount
    12ms snap-snapd-21759.mount
    12ms plymouth-read-write.service
    12ms dev-mqueue.mount
    11ms sys-kernel-debug.mount
    11ms snap-snapd\x2ddesktop\x2dintegration-178.mount
    10ms sys-kernel-tracing.mount
    10ms systemd-tmpfiles-setup-dev.service
    10ms snap-snapd\x2ddesktop\x2dintegration-253.mount
    8ms systemd-update-utmp.service
    8ms snap-telegram\x2ddesktop-6246.mount
    8ms kmod-static-nodes.service
    8ms user-runtime-dir@1000.service
    7ms snap-telegram\x2ddesktop-6277.mount
    7ms modprobe@configfs.service
    7ms modprobe@drm.service
    7ms systemd-user-sessions.service
    6ms modprobe@fuse.service
    6ms nvidia-persistenced.service
    5ms console-setup.service
    4ms swapfile.swap
    4ms systemd-update-utmp-runlevel.service
    3ms rtkit-daemon.service
    3ms ufw.service
    3ms modprobe@efi_pstore.service
    2ms setvtrgb.service
    2ms sys-fs-fuse-connections.mount
    2ms sys-kernel-config.mount
    980us snapd.socket
    ```
    - System takes approximately 30 seconds to load
    - The longest service to load is "plymouth-quit-wait.service"

2. `uptime`
    ```
    23:07:46 up  1:47,  1 user,  load average: 0,74, 0,78, 0,73
    ```
    - Shows how long it needs for system to load

3. `w`
    ```
    23:08:54 up  1:48,  1 user,  load average: 0,67, 0,76, 0,72
    USER     TTY      FROM             LOGIN@   IDLE   JCPU   PCPU WHAT
    csalvia  :0       :0               21:20   ?xdm?   1:19m  0.00s /usr/libexec/gdm-x-session --run-script env GNO
    ```
    - `w` provides more info than `uptime`

## Task 2
1. traceroute
    ```
    traceroute to google.com (142.250.179.174), 30 hops max, 60 byte packets
    1  * * *
    2  * * *
    3  * * *
    4  * * *
    5  * * *
    6  * * *
    7  * * *
    8  * * *
    9  * * *
    10  * * *
    11  * * *
    12  * * *
    13  * * *
    14  * * *
    15  * * *
    16  * * *
    17  * * *
    18  * * *
    19  * * *
    20  * * *
    21  * * *
    22  * * *
    23  * * *
    24  * * *
    25  * * *
    26  * * *
    27  * * *
    28  * * *
    29  * * *
    30  * * *

2. dig
    ```
    ; <<>> DiG 9.18.28-0ubuntu0.22.04.1-Ubuntu <<>> google.com
    ;; global options: +cmd
    ;; Got answer:
    ;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 15787
    ;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 1
    
    ;; OPT PSEUDOSECTION:
    ; EDNS: version: 0, flags:; udp: 65494
    ;; QUESTION SECTION:
    ;google.com.			IN	A
    
    ;; ANSWER SECTION:
    google.com.		275	IN	A	142.250.179.174
    
    ;; Query time: 0 msec
    ;; SERVER: 127.0.0.53#53(127.0.0.53) (UDP)
    ;; WHEN: Mon Nov 11 23:10:47 MSK 2024
    ;; MSG SIZE  rcvd: 55

    ```
