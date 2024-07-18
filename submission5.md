# Key Metrics for SRE and SLAs

## Monitor System Resources

### Top CPU Consuming Applications
```
[?1h=[?25l[H[2J(B[mtop - 19:22:56 up 1 day,  3:01,  1 user,  load average: 1,53, 1,29, 1,14(B[m[39;49m(B[m[39;49m[K
Tasks:(B[m[39;49m[1m 331 (B[m[39;49mtotal,(B[m[39;49m[1m   1 (B[m[39;49mrunning,(B[m[39;49m[1m 328 (B[m[39;49msleeping,(B[m[39;49m[1m   2 (B[m[39;49mstopped,(B[m[39;49m[1m   0 (B[m[39;49mzombie(B[m[39;49m(B[m[39;49m[K
%Cpu(s):(B[m[39;49m[1m  9,0 (B[m[39;49mus,(B[m[39;49m[1m  7,6 (B[m[39;49msy,(B[m[39;49m[1m  0,0 (B[m[39;49mni,(B[m[39;49m[1m 83,3 (B[m[39;49mid,(B[m[39;49m[1m  0,0 (B[m[39;49mwa,(B[m[39;49m[1m  0,0 (B[m[39;49mhi,(B[m[39;49m[1m  0,0 (B[m[39;49msi,(B[m[39;49m[1m  0,0 (B[m[39;49mst(B[m[39;49m(B[m[39;49m[K
MiB Mem :(B[m[39;49m[1m  15866,5 (B[m[39;49mtotal,(B[m[39;49m[1m   5173,6 (B[m[39;49mfree,(B[m[39;49m[1m   4476,6 (B[m[39;49mused,(B[m[39;49m[1m   6216,4 (B[m[39;49mbuff/cache(B[m[39;49m(B[m[39;49m[K
MiB Swap:(B[m[39;49m[1m   2048,0 (B[m[39;49mtotal,(B[m[39;49m[1m   2048,0 (B[m[39;49mfree,(B[m[39;49m[1m      0,0 (B[m[39;49mused.(B[m[39;49m[1m  10195,7 (B[m[39;49mavail Mem (B[m[39;49m(B[m[39;49m[K
[K
[7m    PID USER      PR  NI    VIRT    RES    SHR S  %CPU  %MEM     TIME+ COMMAND                                                                                           (B[m[39;49m[K
(B[m   2162 kamil     20   0   25,7g 188828 115496 S  25,0   1,2  78:10.99 Xorg                                                                                              (B[m[39;49m[K
(B[m   2447 kamil     20   0 6123384 369064 141656 S  12,5   2,3  32:58.58 gnome-shell                                                                                       (B[m[39;49m[K
(B[m 854597 kamil     20   0 1135,4g 286128 105396 S  12,5   1,8   3:35.71 code                                                                                              (B[m[39;49m[K
```

### Top Memory Consuming Applications
```
[?1h=[?25l[H[2J(B[mtop - 19:22:59 up 1 day,  3:02,  1 user,  load average: 1,65, 1,32, 1,15(B[m[39;49m(B[m[39;49m[K
Tasks:(B[m[39;49m[1m 331 (B[m[39;49mtotal,(B[m[39;49m[1m   2 (B[m[39;49mrunning,(B[m[39;49m[1m 327 (B[m[39;49msleeping,(B[m[39;49m[1m   2 (B[m[39;49mstopped,(B[m[39;49m[1m   0 (B[m[39;49mzombie(B[m[39;49m(B[m[39;49m[K
%Cpu(s):(B[m[39;49m[1m 13,4 (B[m[39;49mus,(B[m[39;49m[1m  4,7 (B[m[39;49msy,(B[m[39;49m[1m  0,0 (B[m[39;49mni,(B[m[39;49m[1m 81,2 (B[m[39;49mid,(B[m[39;49m[1m  0,0 (B[m[39;49mwa,(B[m[39;49m[1m  0,0 (B[m[39;49mhi,(B[m[39;49m[1m  0,7 (B[m[39;49msi,(B[m[39;49m[1m  0,0 (B[m[39;49mst(B[m[39;49m(B[m[39;49m[K
MiB Mem :(B[m[39;49m[1m  15866,5 (B[m[39;49mtotal,(B[m[39;49m[1m   5188,9 (B[m[39;49mfree,(B[m[39;49m[1m   4482,4 (B[m[39;49mused,(B[m[39;49m[1m   6195,2 (B[m[39;49mbuff/cache(B[m[39;49m(B[m[39;49m[K
MiB Swap:(B[m[39;49m[1m   2048,0 (B[m[39;49mtotal,(B[m[39;49m[1m   2048,0 (B[m[39;49mfree,(B[m[39;49m[1m      0,0 (B[m[39;49mused.(B[m[39;49m[1m  10211,0 (B[m[39;49mavail Mem (B[m[39;49m(B[m[39;49m[K
[K
[7m    PID USER      PR  NI    VIRT    RES    SHR S  %CPU  %MEM     TIME+ COMMAND                                                                                           (B[m[39;49m[K
(B[m 131275 kamil     20   0 2998752 729880 214576 S   0,0   4,5 233:43.10 Telegram                                                                                          (B[m[39;49m[K
(B[m   3075 kamil     20   0   32,7g 383640 223716 S   0,0   2,4  43:30.98 chrome                                                                                            (B[m[39;49m[K
(B[m   2447 kamil     20   0 6123384 369064 141656 S  11,8   2,3  32:58.84 gnome-shell                                                                                       (B[m[39;49m[K
```

### Top I/O Consuming Applications
```
```

## Disk Space Management

### Disk Usage
```
Filesystem      Size  Used Avail Use% Mounted on
tmpfs           1,6G   18M  1,6G   2% /run
/dev/sda2       234G  182G   41G  82% /
tmpfs           7,8G  166M  7,6G   3% /dev/shm
tmpfs           5,0M  4,0K  5,0M   1% /run/lock
efivarfs        160K   78K   77K  51% /sys/firmware/efi/efivars
/dev/sda1       511M  6,1M  505M   2% /boot/efi
tmpfs           1,6G  132K  1,6G   1% /run/user/1000
```

### Largest Files in /var
```
1012K	/var/lib/fwupd
992K	/var/cache/fontconfig
952K	/var/lib/fwupd/metadata
948K	/var/lib/fwupd/metadata/lvfs
940K	/var/lib/fwupd/metadata/lvfs/metadata.xml.gz
936K	/var/cache/apt/archives/git-man_1%3a2.34.1-1ubuntu1.11_all.deb
908K	/var/snap
900K	/var/log/apt/term.log
900K	/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_jammy_multiverse_binary-amd64_Packages
896K	/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_jammy_restricted_binary-amd64_Packages
```

