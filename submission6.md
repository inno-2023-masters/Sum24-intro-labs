# Operating Systems & Networking Lab

## Task 1: Operating System Analysis

1. **Analyze System Boot Time**:
   - Use `systemd-analyze` to check the overall boot time and identify slow services.

   -  ```sh
      systemd-analyze
      ``` 
   -  Output:
      ```ruby 
      shahin@shahin-VirtualBox:~$ systemd-analyze
      Startup finished in 2.973s (kernel) + 10.399s (userspace) = 13.373s
      graphical.target reached after 10.348s in userspace
      ```

   -  ```sh
      systemd-analyze blame
      ``` 
   -  Output:
      ``` ruby 
      shahin@shahin-VirtualBox:~$ systemd-analyze blame
      7.043s plymouth-quit-wait.service
      2.867s snapd.service
      1.211s networkd-dispatcher.service
      1.125s dev-sda3.device
      810ms accounts-daemon.service
      779ms NetworkManager-wait-online.service
      634ms udisks2.service
      608ms NetworkManager.service
      525ms apport.service
      523ms ModemManager.service
      507ms dev-loop4.device
      502ms avahi-daemon.service
      500ms dev-loop2.device
      486ms dev-loop1.device
      485ms dev-loop3.device
      481ms dev-loop5.device
      479ms gpu-manager.service
      435ms cups.service
      431ms dev-loop6.device
      394ms dev-loop7.device
      394ms dev-loop0.device
      384ms systemd-logind.service
      377ms polkit.service
      375ms power-profiles-daemon.service
      366ms snapd.apparmor.service
      361ms grub-common.service
      356ms e2scrub_reap.service
      317ms apparmor.service
      298ms switcheroo-control.service
      269ms systemd-resolved.service
      266ms lm-sensors.service
      252ms rsyslog.service
      249ms wpa_supplicant.service
      243ms gdm.service
      233ms alsa-restore.service
      221ms grub-initrd-fallback.service
      195ms snapd.seeded.service
      179ms user@1000.service
      156ms systemd-fsck@dev-disk-by\x2duuid-5282\x2d46A8.service
      155ms systemd-oomd.service
      151ms keyboard-setup.service
      139ms systemd-modules-load.service
      139ms systemd-udev-trigger.service
      138ms systemd-timesyncd.service
      129ms packagekit.service
      115ms systemd-tmpfiles-setup.service
      107ms update-notifier-download.service
      106ms systemd-udevd.service
      103ms systemd-journald.service
      92ms upower.service
      90ms modprobe@fuse.service
      85ms systemd-journal-flush.service
      80ms kmod-static-nodes.service
      80ms modprobe@configfs.service
      79ms dev-hugepages.mount
      79ms systemd-user-sessions.service
      78ms dev-mqueue.mount
      77ms sys-kernel-debug.mount
      77ms modprobe@drm.service
      77ms sys-kernel-tracing.mount
      75ms openvpn.service
      74ms plymouth-read-write.service
      61ms systemd-sysusers.service
      60ms boot-efi.mount
      58ms kerneloops.service
      48ms systemd-binfmt.service
      46ms systemd-sysctl.service
      39ms systemd-random-seed.service
      34ms systemd-update-utmp.service
      33ms systemd-remount-fs.service
      33ms sys-fs-fuse-connections.mount
      33ms sys-kernel-config.mount
      32ms console-setup.service
      31ms colord.service
      31ms snap-snap\x2dstore-959.mount
      29ms snap-snapd\x2ddesktop\x2dintegration-83.mount
      28ms plymouth-start.service
      28ms snap-gtk\x2dcommon\x2dthemes-1535.mount
      24ms snap-bare-5.mount
      23ms user-runtime-dir@1000.service
      23ms proc-sys-fs-binfmt_misc.mount
      23ms snap-core22-1122.mount
      22ms snap-gnome\x2d42\x2d2204-141.mount
      22ms systemd-tmpfiles-setup-dev.service
      22ms ssh.service
      21ms var-snap-firefox-common-host\x2dhunspell.mount
      21ms snap-firefox-3836.mount
      17ms snap-snapd-20671.mount
      15ms swapfile.swap
      14ms snapd.socket
      11ms ufw.service
      10ms systemd-update-utmp-runlevel.service
      6ms setvtrgb.service
      5ms modprobe@efi_pstore.service
      3ms rtkit-daemon.service
      ```




2. **Check System Load and Uptime**:
   - Use `uptime` and `w` to check system load and uptime.

      -   ```sh
          uptime
          ```
      - output : 
         ``` ruby 
         shahin@shahin-VirtualBox:~$ uptime
         18:36:22 up 9 min,  2 users,  load average: 0,02, 0,08, 0,07
         ```
      -   ```sh
          W
          ```
      - output : 
         ``` ruby 
         shahin@shahin-VirtualBox:~$ w
         18:36:23 up 9 min,  2 users,  load average: 0,02, 0,08, 0,07
         USER     TTY      FROM             LOGIN@   IDLE   JCPU   PCPU WHAT
         shahin   tty2     tty2             18:27    9:32   0.02s  0.02s /usr/libexec/gnome-session-binary --session=ubuntu
         shahin   pts/1    10.0.2.2         18:35    3.00s  0.02s  0.00s w
         ```


## Task 2: Networking Analysis

**Objective**: Perform network diagnostics and analyze DNS resolution to understand network paths and latency.

1. **Traceroute**:
   - Perform a traceroute to a specified website or IP address.

   -  ```sh
      shahin@shahin-VirtualBox:~$ sudo apt install traceroute
      traceroute google.com
      ```
   - Output: 
      ``` ruby 
      shahin@shahin-VirtualBox:~$ traceroute google.com
      traceroute to google.com (64.233.162.102), 30 hops max, 60 byte packets
      1  _gateway (10.0.2.2)  0.260 ms  0.218 ms  0.187 ms
      ```   



2. **Dig**:
   - Use the appropriate command or tool to perform a DNS lookup for a specified domain name.

   -   ```sh
       dig google.com
       ```
   - Output: 
    ``` ruby 
      shahin@shahin-VirtualBox:~$ dig google.com

      ; <<>> DiG 9.18.18-0ubuntu0.22.04.2-Ubuntu <<>> google.com
      ;; global options: +cmd
      ;; Got answer:
      ;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 58322
      ;; flags: qr rd ra; QUERY: 1, ANSWER: 6, AUTHORITY: 0, ADDITIONAL: 1

      ;; OPT PSEUDOSECTION:
      ; EDNS: version: 0, flags:; udp: 65494
      ;; QUESTION SECTION:
      ;google.com.                    IN      A

      ;; ANSWER SECTION:
      google.com.             261     IN      A       64.233.163.102
      google.com.             261     IN      A       64.233.163.138
      google.com.             261     IN      A       64.233.163.139
      google.com.             261     IN      A       64.233.163.113
      google.com.             261     IN      A       64.233.163.101
      google.com.             261     IN      A       64.233.163.100

      ;; Query time: 4 msec
      ;; SERVER: 127.0.0.53#53(127.0.0.53) (UDP)
      ;; WHEN: Thu Jul 18 18:37:45 MSK 2024
      ;; MSG SIZE  rcvd: 135
    ```
