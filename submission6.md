# Operating System Analysis

## Systemd Analyze Output
```
Startup finished in 23.412s (kernel) + 14.329s (userspace) = 37.742s 
graphical.target reached after 14.297s in userspace
```

## Systemd Analyze Blame Output
```
15.192s apt-daily.service
12.090s udisks2.service
 8.657s apt-daily-upgrade.service
 7.926s plymouth-quit-wait.service
 6.902s NetworkManager-wait-online.service
 4.387s docker.service
 1.359s snapd.service
  922ms gpu-manager.service
  893ms fwupd-refresh.service
  775ms dev-sda2.device
  708ms snapd.seeded.service
  617ms mullvad-early-boot-blocking.service
  598ms networkd-dispatcher.service
  549ms dev-loop0.device
  527ms man-db.service
  510ms dev-loop1.device
  508ms dev-loop2.device
  507ms dev-loop3.device
  506ms e2scrub_reap.service
  374ms containerd.service
  345ms gdm.service
  236ms accounts-daemon.service
  201ms ModemManager.service
  199ms systemd-resolved.service
  177ms snapd.apparmor.service
  170ms systemd-udev-trigger.service
  156ms user@1000.service
  154ms polkit.service
  153ms systemd-oomd.service
  152ms power-profiles-daemon.service
  152ms avahi-daemon.service
  148ms NetworkManager.service
  147ms apport-autoreport.service
  146ms bluetooth.service
  145ms systemd-timesyncd.service
  134ms dpkg-db-backup.service
  120ms cups.service
  115ms switcheroo-control.service
  113ms update-notifier-download.service
  108ms secureboot-db.service
  107ms thermald.service
  104ms wpa_supplicant.service
  103ms systemd-logind.service
  100ms apparmor.service
   98ms systemd-journald.service
   92ms systemd-modules-load.service
   90ms apport.service
   90ms keyboard-setup.service
   87ms xl2tpd.service
   85ms upower.service
   79ms systemd-sysctl.service
   78ms boot-efi.mount
   74ms systemd-udevd.service
   71ms logrotate.service
   68ms systemd-tmpfiles-clean.service
   67ms modprobe@drm.service
   64ms systemd-remount-fs.service
   61ms snap-bare-5.mount
   61ms snap-core18-2823.mount
   60ms snap-core18-2829.mount
   58ms snap-core20-2105.mount
   58ms snap-core20-2182.mount
   58ms snap-core22-1122.mount
   58ms packagekit.service
   57ms snap-core22-858.mount
   57ms snap-firefox-4033.mount
   56ms snap-firefox-4090.mount
   56ms snap-gaming\x2dgraphics\x2dcore22-154.mount
   56ms setvtrgb.service
   56ms snap-gaming\x2dgraphics\x2dcore22-166.mount
   55ms snap-gnome\x2d3\x2d34\x2d1804-93.mount
   54ms snap-gnome\x2d3\x2d38\x2d2004-143.mount
   54ms snap-gnome\x2d42\x2d2204-141.mount
   52ms rsyslog.service
   52ms snap-gnome\x2d42\x2d2204-172.mount
   51ms snap-gtk\x2dcommon\x2dthemes-1535.mount
   51ms snap-slack-132.mount
   50ms snap-slack-139.mount
   49ms snap-snap\x2dstore-1113.mount
   48ms snap-snap\x2dstore-959.mount
   48ms snap-snapd-20671.mount
   47ms snap-snapd-21184.mount
   46ms snap-snapd-21465.mount
   45ms snap-snapd-21759.mount
   42ms snap-snapd\x2ddesktop\x2dintegration-157.mount
   42ms snap-snapd\x2ddesktop\x2dintegration-83.mount
   41ms snap-steam-171.mount
   40ms snap-vlc-3721.mount
   39ms snap-vlc-3777.mount
   38ms snap-zoom\x2dclient-218.mount
   37ms snap-zoom\x2dclient-225.mount
   36ms kerneloops.service
   34ms var-snap-firefox-common-host\x2dhunspell.mount
   33ms systemd-tmpfiles-setup.service
   27ms systemd-fsck@dev-disk-by\x2duuid-ED5E\x2dE899.service
   27ms docker.socket
   25ms systemd-sysusers.service
   21ms alsa-restore.service
   21ms dev-hugepages.mount
   20ms plymouth-start.service
   20ms dev-mqueue.mount
   20ms colord.service
   20ms systemd-binfmt.service
   19ms sys-kernel-debug.mount
   19ms systemd-random-seed.service
   19ms sys-kernel-tracing.mount
   18ms grub-common.service
   16ms systemd-rfkill.service
   16ms systemd-tmpfiles-setup-dev.service
   15ms kmod-static-nodes.service
   14ms modprobe@configfs.service
   14ms plymouth-read-write.service
   13ms systemd-update-utmp.service
   12ms grub-initrd-fallback.service
   11ms proc-sys-fs-binfmt_misc.mount
   11ms systemd-user-sessions.service
   11ms modprobe@fuse.service
    9ms user-runtime-dir@1000.service
    8ms console-setup.service
    8ms systemd-update-utmp-runlevel.service
    8ms ufw.service
    7ms systemd-journal-flush.service
    7ms openvpn.service
    7ms systemd-backlight@backlight:intel_backlight.service
    7ms swapfile.swap
    5ms nvidia-persistenced.service
    4ms rtkit-daemon.service
    4ms motd-news.service
    3ms sys-fs-fuse-connections.mount
    2ms modprobe@efi_pstore.service
    2ms sys-kernel-config.mount
  910us snapd.socket
```

## Uptime Output
```
 18:55:25 up 1 day,  2:34,  1 user,  load average: 1,93, 1,14, 0,96
```

## W Command Output
```
 18:55:25 up 1 day,  2:34,  1 user,  load average: 1,93, 1,14, 0,96
USER     TTY      FROM             LOGIN@   IDLE   JCPU   PCPU WHAT
kamil    :1       :1               Ср16   ?xdm?   8:23m  0.00s /usr/libexec/gdm-x-session --run-script env GNOME_SHELL_SESSION_MODE=ubuntu /usr/bin/gnome-session --session=ubuntu
```

## Observations and Insights

- Observation regarding system boot time...
- Observation regarding system load...
- Observation regarding system uptime...

# Networking Analysis

## Traceroute Output
```
```

## Dig Output
```

; <<>> DiG 9.18.18-0ubuntu0.22.04.2-Ubuntu <<>> example.com
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 30267
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 1

;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 65494
;; QUESTION SECTION:
;example.com.			IN	A

;; ANSWER SECTION:
example.com.		3521	IN	A	93.184.215.14

;; Query time: 36 msec
;; SERVER: 127.0.0.53#53(127.0.0.53) (UDP)
;; WHEN: Thu Jul 18 18:55:51 MSK 2024
;; MSG SIZE  rcvd: 56

```

## Observations and Insights

- Observation regarding network path...
- Observation regarding latency...
- Observation regarding DNS resolution...
