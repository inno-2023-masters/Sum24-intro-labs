# Task 1
## Analyzing System Boot Time
I used systemd-analyze command to get to know the system boot time. It revealed that it takes ~26s and the lowest service plymouth-quit-wait.service takes ~21s.

$ systemd-analyze
Startup finished in 2.327s (kernel) + 23.742s (userspace) = 26.070s 
graphical.target reached after 23.714s in userspace.

$ systemd-analyze blame
21.344s plymouth-quit-wait.service
 1.707s fwupd.service
  888ms systemd-binfmt.service
  863ms systemd-resolved.service
  842ms snapd.seeded.service
  835ms systemd-oomd.service
  822ms systemd-timesyncd.service
  
## Checking System Load and Uptime
At the time of checking the system uptime was 1h16m. 
According to 'w' and 'uptime' the system load in average was ~0.86.

$ uptime
 02:19:45 up  1:16,  1 user,  load average: 1.26, 0.86, 0.91

$ w
 02:20:19 up  1:16,  1 user,  load average: 0.92, 0.82, 0.90
USER     TTY      FROM             LOGIN@   IDLE   JCPU   PCPU WHAT
user     tty2     -                01:03    1:16m  0.03s  0.03s /usr/libexec/gnome-session-binary --sess

## Task 2: Networking Analysis
## Traceroute
I checked the route taken by the packets to google.com . It revealed 25 intermediate points (routers). From 1st to 9th routers it passed within 40 s and from 9th to 15th routers it took about 45ms in average to pass each.

$ traceroute google.com
traceroute to google.com (216.239.38.120), 30 hops max, 60 byte packets
 1  _gateway (10.0.2.2)  0.525 ms  0.441 ms  0.655 ms
 2  10.91.48.1 (10.91.48.1)  3.037 ms  3.006 ms  2.984 ms
 3  10.252.6.1 (10.252.6.1)  4.870 ms  4.745 ms  5.306 ms
 4  1.123.18.84.in-addr.arpa (84.18.123.1)  16.998 ms  17.039 ms  15.903 ms
 5  188.170.164.138 (188.170.164.138)  13.622 ms  13.533 ms  13.443 ms
 6  * * *
 7  * * *
 8  * * *
 9  83.169.204.113 (83.169.204.113)  23.550 ms 83.169.204.117 (83.169.204.117)  23.512 ms 83.169.204.113 (83.169.204.113)  23.839 ms
10  37.29.3.250 (37.29.3.250)  25.690 ms  24.065 ms 72.14.222.181 (72.14.222.181)  25.186 ms
11  192.178.241.173 (192.178.241.173)  24.867 ms 192.178.241.251 (192.178.241.251)  23.038 ms 108.170.250.34 (108.170.250.34)  23.974 ms
12  142.251.238.82 (142.251.238.82)  39.385 ms 192.178.241.70 (192.178.241.70)  31.588 ms 72.14.234.20 (72.14.234.20)  70.570 ms
13  209.85.254.6 (209.85.254.6)  47.120 ms 142.251.237.144 (142.251.237.144)  46.252 ms 142.251.238.72 (142.251.238.72)  47.020 ms
14  209.85.246.111 (209.85.246.111)  44.199 ms 142.250.235.74 (142.250.235.74)  45.872 ms 172.253.65.82 (172.253.65.82)  58.209 ms
15  216.239.42.21 (216.239.42.21)  42.189 ms 142.250.56.129 (142.250.56.129)  39.155 ms *
16  * * *
17  * * *
18  * * *
19  * * *
20  * * *
21  * * *
22  * * *
23  * * *
24  * * *
25  any-in-2678.1e100.net (216.239.38.120)  42.056 ms  42.025 ms  42.617 ms

## Dig
Using dig I performed a DNS lookup for google.com . It queried the address name of the server and displayed the answer with metadata.

$ dig google.com

; <<>> DiG 9.18.24-0ubuntu5-Ubuntu <<>> google.com
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 46931
;; flags: qr rd ra; QUERY: 1, ANSWER: 2, AUTHORITY: 0, ADDITIONAL: 2

;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 65494
;; QUESTION SECTION:
;google.com.			IN	A

;; ANSWER SECTION:
google.com.		3592	IN	CNAME	forcesafesearch.google.com.
forcesafesearch.google.com. 6449 IN	A	216.239.38.120

;; ADDITIONAL SECTION:
forcesafesearch.google.com. 3592 IN	AAAA	2001:4860:4802:32::78

;; Query time: 0 msec
;; SERVER: 127.0.0.53#53(127.0.0.53) (UDP)
;; WHEN: Wed Jul 03 02:37:29 MSK 2024
;; MSG SIZE  rcvd: 113

