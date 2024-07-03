# Operating Systems & Networking Lab
## Task 1: Operating System Analysis
### Analyze System Boot Time
```bash
roiven@roiven-MS-7C02:/etc/openvpn/config$ systemd-analyze
Startup finished in 21.186s (firmware) + 9.690s (loader) + 8.611s (kernel) + 15.956s (userspace) = 55.445s 
graphical.target reached after 15.904s in userspace
roiven@roiven-MS-7C02:/etc/openvpn/config$ systemd-analyze blame
13.776s plymouth-quit-wait.service
12.822s vboxdrv.service
11.028s gpu-manager.service
 9.375s apt-daily-upgrade.service
 4.286s fstrim.service
 1.978s NetworkManager-wait-online.service
 1.915s snapd.seeded.service
 1.803s snapd.service
 1.184s e2scrub_reap.service
 1.176s networkd-dispatcher.service
 1.175s docker.service
 1.165s logrotate.service
 1.061s fwupd.service
  960ms udisks2.service
  774ms accounts-daemon.service
  767ms man-db.service
  758ms NetworkManager.service
  753ms grub-common.service
  744ms power-profiles-daemon.service
  740ms polkit.service
  616ms dev-sdb2.device
  551ms containerd.service
  522ms avahi-daemon.service
  490ms switcheroo-control.service
  485ms thermald.service
  485ms systemd-logind.service
  482ms wpa_supplicant.service
  357ms grub-initrd-fallback.service
  350ms dev-loop9.device
  349ms dev-loop10.device
  348ms dev-loop16.device
  344ms dev-loop17.device
  343ms ModemManager.service
  315ms dev-loop13.device
  315ms dev-loop11.device
  315ms dev-loop12.device
  297ms dev-loop8.device
  281ms dev-loop1.device
  273ms rsyslog.service
  271ms secureboot-db.service
```

From the provided information about system boot time and the list of services with the longest startup times, the following slow services can be identified:

1. plymouth-quit-wait.service - 13.776s
2. vboxdrv.service - 12.822s
3. gpu-manager.service - 11.028s
4. apt-daily-upgrade.service - 9.375s
5. fstrim.service - 4.286s

These services take a significant amount of time during system boot.

## Check System Load and Uptime:

```bash
roiven@roiven-MS-7C02:/etc/openvpn/config$ uptime
03:18:33 up  2:35,  1 user,  load average: 0,70, 0,81, 0,66

roiven@roiven-MS-7C02:/etc/openvpn/config$ w
 03:19:35 up  2:36,  1 user,  load average: 0,85, 0,82, 0,67
USER     TTY      FROM             LOGIN@   IDLE   JCPU   PCPU WHAT
roiven   tty2     tty2             01:18     ?     0.01s  0.01s /usr/libexec/gnome-session-binary --session=ubuntu
```

The uptime command provides information about the system's uptime, current time, number of users logged in, and the load average over the last 1, 5, and 15 minutes. In this case:

- The system has been up for 2 hours and 35 minutes.
- There is 1 user logged in.
- The load averages are 0.70, 0.81, and 0.66 for the last 1, 5, and 15 minutes respectively.

The w command displays information about the users currently logged in and their processes. In this case:

- The system has been up for 2 hours and 36 minutes.
- There is 1 user logged in.
- The load averages are 0.85, 0.82, and 0.67 for the last 1, 5, and 15 minutes respectively.
- The user roiven is logged in on tty2 and is running /usr/libexec/gnome-session-binary.

## Task 2: Networking Analysis

### Traceroute:

```bash
roiven@roiven-MS-7C02:/etc/openvpn/config$ traceroute google.com
traceroute to google.com (216.239.38.120), 30 hops max, 60 byte packets
 1  XiaoQiang (192.168.31.1)  0.363 ms  0.445 ms  0.540 ms
 2  10.242.1.1 (10.242.1.1)  1.967 ms  2.190 ms  2.171 ms
 3  10.250.0.2 (10.250.0.2)  2.150 ms  2.177 ms  2.224 ms
 4  10.252.6.1 (10.252.6.1)  2.484 ms  2.518 ms  2.557 ms
 5  1.123.18.84.in-addr.arpa (84.18.123.1)  17.294 ms  17.572 ms  17.449 ms
 6  188.170.164.138 (188.170.164.138)  12.068 ms  9.419 ms  8.968 ms
 7  * * *
 8  * * *
 9  * * *
10  83.169.204.117 (83.169.204.117)  21.310 ms 83.169.204.115 (83.169.204.115)  20.589 ms  31.652 ms
11  37.29.3.250 (37.29.3.250)  28.417 ms 72.14.222.181 (72.14.222.181)  22.286 ms  21.642 ms
12  108.170.250.34 (108.170.250.34)  21.676 ms * 192.178.241.251 (192.178.241.251)  21.315 ms
13  * 192.178.241.70 (192.178.241.70)  21.960 ms *
14  142.250.238.214 (142.250.238.214)  37.978 ms 142.251.237.146 (142.251.237.146)  38.524 ms 142.250.238.214 (142.250.238.214)  38.793 ms
15  108.170.235.204 (108.170.235.204)  38.260 ms 142.250.235.62 (142.250.235.62)  40.094 ms 142.251.238.70 (142.251.238.70)  40.877 ms
16  142.250.233.27 (142.250.233.27)  36.492 ms * *
17  * * *
18  * * *
19  * * *
20  * * *
21  * * *
22  * * *
23  * * *
24  * * *
25  * any-in-2678.1e100.net (216.239.38.120)  37.837 ms  37.405 ms
```

The traceroute command was used to track the route packets take from the local machine to the destination server google.com with the IP address 216.239.38.120. Here are some comments on the output:

1. The initial hops (192.168.31.1, 10.242.1.1, 10.250.0.2, 10.252.6.1) show internal network addresses, indicating that the packets are passing through local network devices like routers or gateways.

2. Hop 5 shows an IP address 84.18.123.1, which suggests that the packets are now outside of the local network and are traversing public internet infrastructure.

3. Hops 6 to 10 show successful responses with varying latency times, indicating the packets are moving through different network nodes.

4. The subsequent hops (7 to 23) show timeouts (* * *), which could be due to network configurations blocking certain types of traffic or intermediate routers not responding to the traceroute requests.

5. The final hop successfully reaches the destination server google.com (216.239.38.120) after multiple intermediate nodes.

### Dig:

```bash
roiven@roiven-MS-7C02:/etc/openvpn/config$ dig google.com

; <<>> DiG 9.18.18-0ubuntu0.22.04.2-Ubuntu <<>> google.com
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 17751
;; flags: qr rd ra; QUERY: 1, ANSWER: 2, AUTHORITY: 0, ADDITIONAL: 2

;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 65494
;; QUESTION SECTION:
;google.com.			IN	A

;; ANSWER SECTION:
google.com.		184	IN	CNAME	forcesafesearch.google.com.
forcesafesearch.google.com. 227	IN	A	216.239.38.120

;; ADDITIONAL SECTION:
forcesafesearch.google.com. 184	IN	AAAA	2001:4860:4802:32::78

;; Query time: 0 msec
;; SERVER: 127.0.0.53#53(127.0.0.53) (UDP)
;; WHEN: Wed Jul 03 03:26:56 MSK 2024
;; MSG SIZE  rcvd: 113
```

The dig command was used to query the DNS records for google.com. Here are some comments on the output:

1. The query was successful (status: NOERROR), indicating that the DNS resolution for google.com was completed without errors.

2. The query requested the IPv4 address (IN A) of google.com, and the response provided two answers:
   - forcesafesearch.google.com. is a CNAME (canonical name) record pointing to forcesafesearch.google.com.
   - The IPv4 address of forcesafesearch.google.com is 216.239.38.120.

3. Additionally, an IPv6 address (AAAA record) for forcesafesearch.google.com is provided: 2001:4860:4802:32::78.

4. The query time was very fast (0 msec), indicating a quick response from the DNS server.

5. The response was received from the local DNS resolver (127.0.0.53#53) running on the machine.


