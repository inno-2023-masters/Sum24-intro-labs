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

2. VPS server already work 35 days
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
## Task 2. Networking Analysis

1. Execute ``traceroute`` command:
- The traceroute shows a total of 7 hops between the user’s machine and the target server
- The first hop goes to the local gateway (10.0.0.1) with very low latency.
- The subsequent hops are through various networks and internet providers, with a slight increase in latency after the first 3 hops.
- The final hop reaches the target server with an IP address of 188.114.99.225, indicating the connection is successful.

```bash
root@dimoninbirsk:~# traceroute www.blender.org
traceroute to www.blender.org (188.114.99.225), 30 hops max, 60 byte packets
 1  _gateway (10.0.0.1)  0.130 ms  0.046 ms  0.040 ms
 2  172.31.155.1 (172.31.155.1)  0.698 ms  1.320 ms  1.262 ms
 3  172.17.23.111 (172.17.23.111)  0.374 ms 172.17.22.104 (172.17.22.104)  0.414 ms 172.17.23.111 (172.17.23.111)  0.331 ms
 4  79.137.154.9 (79.137.154.9)  1.023 ms  1.075 ms  1.064 ms
 5  cloudflare-ic-369088.ip.twelve99-cust.net (80.239.193.241)  3.598 ms  3.502 ms  3.470 ms
 6  ae5.mbr1.ip.di-net.ru (213.248.7.90)  3.759 ms 172.68.8.51 (172.68.8.51)  1.554 ms ae5.mbr1.ip.di-net.ru (213.248.7.90)  1.431 ms
 7  188.114.99.225 (188.114.99.225)  0.865 ms  1.190 ms  1.090 ms
```
2. Execute ``dig`` command:

- The DNS lookup for www.blender.org returns two IP addresses: 188.114.98.229 and 188.114.99.229. This indicates that the domain name is configured for load balancing, distributing traffic across multiple servers.
- The DNS query time is very low (4 milliseconds), indicating a fast and efficient DNS server response.
- The output of dig confirms the IP address from the last hop in the traceroute is one of the resolved IPs for www.blender.org.

```bash
root@dimoninbirsk:~# dig www.blender.org

; <<>> DiG 9.18.18-0ubuntu0.22.04.2-Ubuntu <<>> www.blender.org
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 31938
;; flags: qr rd ra; QUERY: 1, ANSWER: 2, AUTHORITY: 0, ADDITIONAL: 1

;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 65494
;; QUESTION SECTION:
;www.blender.org.               IN      A

;; ANSWER SECTION:
www.blender.org.        150     IN      A       188.114.98.229
www.blender.org.        150     IN      A       188.114.99.229

;; Query time: 4 msec
;; SERVER: 127.0.0.53#53(127.0.0.53) (UDP)
;; WHEN: Tue Jul 02 10:50:21 MSK 2024
;; MSG SIZE  rcvd: 76
```
