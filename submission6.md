# Task 1: Operating System Analysis

## 1. Analyze System Boot Time

Command: `systemd-analyze`:

````bash
timmmich@timmmich-Aspire-A715-43G:~$ systemd-analyze
Startup finished in 3.236s (firmware) + 1min 3.695s (loader) + 1.835s (kernel) + 10.981s (userspace) = 1min 19.748s
graphical.target reached after 10.961s in userspace.```

````

Command: `systemd-analyze blame`

```bash
timmmich@timmmich-Aspire-A715-43G:~$ systemd-analyze blame
6.281s NetworkManager-wait-online.service
6.281s NetworkManager-wait-online.service
5.671s plymouth-quit-wait.service
3.932s systemd-suspend.service
1.460s NetworkManager.service
1.137s gpu-manager.service
 785ms snapd.seeded.service
6.281s NetworkManager-wait-online.service
5.671s plymouth-quit-wait.service
3.932s systemd-suspend.service
1.460s NetworkManager.service
1.137s gpu-manager.service
 785ms snapd.seeded.service
 641ms fwupd.service
 370ms snapd.service
 315ms user@1000.service
 307ms dev-nvme0n1p6.device
 269ms apport.service
 268ms nvidia-suspend.service

```

Observations:

- The overall system boot time is approximately 19.748 seconds.
- The NetworkManager-wait-online.service takes the most time, contributing to a significant portion of the boot process with 6.281 seconds.
- Other services like apt-daily.service and udisks2.service also contribute but are relatively faster.
- Some of the divers like nvidia gpu manager contributing also

## 2. Check System Load and Uptime

Command: `uptime`

```bash
timmmich@timmmich-Aspire-A715-43G:~$ uptime
 16:45:23 up  3:14,  1 user,  load average: 0.45, 0.62, 0.76
```

Command: `w`

```bash
timmmich@timmmich-Aspire-A715-43G:~$ w
 16:46:37 up  3:15,  1 user,  load average: 0.66, 0.64, 0.76
USER     TTY      FROM             LOGIN@   IDLE   JCPU   PCPU WHAT
timmmich tty2     -                13:32    3:15m 12:01   0.07s /usr/libexec/gnome-session
```

Observations:

- The system has been up for 3:15 hours.
- There are 1 user currently logged in.
- The load averages over the last 1, 5, and 15 minutes are 0.66, 0.64, and 0.76 respectively, indicating moderate system load.

# Task 2: Networking Analysiss

Command: `traceroute example.com`

```bash
timmmich@timmmich-Aspire-A715-43G:~$ traceroute example.com
traceroute to example.com (93.184.216.34), 30 hops max, 60 byte packets
 1  router.local (192.168.1.1)  1.123 ms  0.917 ms  0.798 ms
 2  10.0.0.1 (10.0.0.1)  9.512 ms  9.406 ms  9.342 ms
 3  93.184.215.14 (93.184.216.34)  11.891 ms  11.762 ms  11.615 ms

```

Observations:

- The traceroute command shows the path packets take to reach example.com.
- The path involves 3 hops with the IP addresses 192.168.1.1 (local router), 10.0.0.1 (internal network), and 93.184.215.14 (destination server).
- The latency is very low, with the maximum time taken being around 11.891 ms.

Command: `dig example.com`

```bash
timmmich@timmmich-Aspire-A715-43G:~$ dig example.com

; <<>> DiG 9.18.24-0ubuntu5-Ubuntu <<>> example.com
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 55564
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 1

;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 65494
;; QUESTION SECTION:
;example.com.			IN	A

;; ANSWER SECTION:
example.com.		1995	IN	A	93.184.215.14

;; Query time: 53 msec
;; SERVER: 127.0.0.53#53(127.0.0.53) (UDP)
;; WHEN: Wed Jul 10 16:51:24 MSK 2024
;; MSG SIZE  rcvd: 56


```

Observations:

- The DNS lookup for example.com returned an A record with the IP address 93.184.215.14.
- The query time was 53 milliseconds, indicating a quick response from the DNS server.
- The DNS server used for this lookup is 127.0.0.53, which is likely the local network's DNS resolver.

Conclusion for that lab:

This lab exercise provided hands-on experience with analyzing system performance and network diagnostics. Key insights include identifying services that affect boot time, understanding system load and uptime, and performing network path and DNS resolution analysis.
