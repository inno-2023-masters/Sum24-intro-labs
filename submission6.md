## Task 1: Operating System Analysis

1. **Analyze System Boot Time**:

Let's use `systemd-analyze` to check the overall boot time and identify slow services:

```
systemd-analyze
Startup finished in 10.854s (firmware) + 14.163s (loader) + 5.310s (kernel) + 23.787s (userspace) = 54.115s 
graphical.target reached after 23.735s in userspace
```
Over 10 seconds for firmware start is a bit lengthy, indicating either an extensive POST (Power-On Self-Test) or potential hardware delays. 

Grub is taking 14 seconds. This is pretty slow, but I have Dual Boot system + old PC so it's rather OK. 

Kernel is relatively fast, we can dig in `sudo dmesg --syslog` for more details, but I'll leave it as the task do not says so.

Userspace is taking almost 24 seconds which is really big amount. We can dig deeper with `systemd-analyze blame` to identify and disable or optimize slow services.

Let's analyze some of the outputs:

```
 systemd-analyze blame
21.033s plymouth-quit-wait.service
 9.855s apt-daily-upgrade.service
 8.117s NetworkManager-wait-online.service
 2.985s docker.service
 1.049s snapd.seeded.service
  941ms snapd.service
  880ms networkd-dispatcher.service
  854ms e2scrub_reap.service
  831ms apparmor.service
  665ms udisks2.service
  618ms dev-sda4.device
  456ms accounts-daemon.service
  439ms power-profiles-daemon.service
  430ms polkit.service
  424ms dev-loop10.device
  422ms dev-loop8.device
  413ms dev-loop11.device
  412ms dev-loop19.device
  407ms dev-loop9.device
  398ms dev-loop18.device
  371ms avahi-daemon.service
  370ms NetworkManager.service
  356ms switcheroo-control.service

```

First one handles the splash screen during boot. This service is waiting for Plymouth to quit, which is taking a significant amount of time. I need to investigate more in this problem.

I investigated more and understood that plymouth just holds a boot-up logo and waits until the system is booted. So it co-exists with a boot process and just waits, so this one is not a problem at all.

docker.service (2.985s): I do not have services critical for immediate use after boot, so I might set this service to start later.


2. **Check System Load and Uptime**:

```
uptime
 00:44:19 up  3:22,  1 user,  load average: 0.17, 0.35, 0.28
```

```
w
 00:44:34 up  3:22,  1 user,  load average: 0.21, 0.35, 0.28
USER     TTY      FROM             LOGIN@   IDLE   JCPU   PCPU WHAT
pegasus  :0       :0               00:22   ?xdm?   2:24m  0.00s /usr/libexec/gd
```
I checked my system's uptime, which shows my machine has been running for 3 hours and 22 minutes with a load average of 0.17, 0.35, and 0.28 over the last 1, 5, and 15 minutes. This means my system is relatively idle with low CPU demand. Additionally, when I ran the w command, I saw that I'm the only user logged in, and I've been logged in since 00:22. My graphical session (:0) has been idle, with minimal CPU usage by the /usr/libexec/gd process, indicating that my system is not under heavy load and is performing efficiently.

## Task 2: Networking Analysis

1. **Traceroute**:

```
traceroute worldclown.com
traceroute to worldclown.com (162.241.217.117), 30 hops max, 60 byte packets
 1  SNR-CPE-ME2-Lite.lan (192.168.1.1)  0.624 ms  0.652 ms  0.546 ms
 2  10.16.255.147 (10.16.255.147)  6.420 ms  6.368 ms  6.418 ms
 3  10.16.242.38 (10.16.242.38)  6.397 ms 10.16.242.34 (10.16.242.34)  6.305 ms 10.16.242.54 (10.16.242.54)  6.531 ms
 4  10.16.248.150 (10.16.248.150)  6.544 ms 10.16.248.218 (10.16.248.218)  6.480 ms 10.16.248.170 (10.16.248.170)  7.120 ms
 5  * * 10.16.248.130 (10.16.248.130)  7.462 ms
 6  10.16.248.253 (10.16.248.253)  7.078 ms 10.16.248.130 (10.16.248.130)  6.757 ms 188.170.164.32 (188.170.164.32)  7.893 ms
 7  * 188.170.164.138 (188.170.164.138)  9.304 ms  9.187 ms
 8  10.222.16.54 (10.222.16.54)  51.781 ms 10.222.16.33 (10.222.16.33)  39.071 ms  39.051 ms
 9  10.222.16.50 (10.222.16.50)  39.236 ms *  39.620 ms
10  * * 83.169.204.74 (83.169.204.74)  48.896 ms
11  83.169.204.70 (83.169.204.70)  48.876 ms  49.275 ms 83.169.204.74 (83.169.204.74)  48.796 ms
12  et-0-0-26-101.edge4.Warsaw1.Level3.net (212.133.55.9)  63.567 ms ae1.37.bar4.SaltLakeCity1.level3.net (4.69.219.58)  193.306 ms et-0-0-26-101.edge4.Warsaw1.Level3.net (212.133.55.9)  63.566 ms
13  ae1.37.bar4.SaltLakeCity1.level3.net (4.69.219.58)  188.697 ms  193.288 ms  193.243 ms
14  4.53.7.174 (4.53.7.174)  203.882 ms 69-195-64-111.unifiedlayer.com (69.195.64.111)  201.693 ms  202.126 ms
15  po97.prv-leaf1a.net.unifiedlayer.com (162.144.240.123)  202.025 ms 69-195-64-111.unifiedlayer.com (69.195.64.111)  202.987 ms 69-195-64-113.unifiedlayer.com (69.195.64.113)  201.972 ms
16  box5480.bluehost.com (162.241.217.117)  198.537 ms  197.444 ms po97.prv-leaf1b.net.unifiedlayer.com (162.144.240.131)  199.688 ms

```

I  performed a traceroute to worldclown.com to analyze the network path and latency. The results show that the initial hops within the local network had low latency, averaging around 0.6 to 7.5 ms. As the traceroute progressed through various internal network nodes, the latency remained stable. However, once the packets reached external networks, the latency increased drastically , especially as it traveled through international nodes, with the highest latency reaching around 200 ms. The final hop to the destination server showed consistent response times, indicating a stable connection to worldclown.com

2. **Dig**:

```
dig worldclown.com

; <<>> DiG 9.18.24-0ubuntu0.22.04.1-Ubuntu <<>> worldclown.com
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 62297
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 1

;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 65494
;; QUESTION SECTION:
;worldclown.com.			IN	A

;; ANSWER SECTION:
worldclown.com.		7067	IN	A	162.241.217.117

;; Query time: 0 msec
;; SERVER: 127.0.0.53#53(127.0.0.53) (UDP)
;; WHEN: Thu Jul 11 00:50:28 MSK 2024
;; MSG SIZE  rcvd: 59
```

The IP address returned for worldclown.com is 162.241.217.117. The query was processed instantly with a query time of 0 milliseconds. The DNS server used was 127.0.0.53 on UDP, indicating a local resolver. Overall, the DNS resolution was quick and efficient.