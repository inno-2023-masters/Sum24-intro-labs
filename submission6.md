### Task 1: Operating System Analysis

#### 1.Analyze System Boot Time:
```sh 
## systemd-analyze
root@applewolf:~$ systemd-analyze

Startup finished in 4.161s (kernel) + 4.925s (userspace) = 9.087s
graphical.target reached after 4.886s in userspace

## systemd-analyze blame

root@applewolf:~$ systemd-analyze blame

30.127s apt-daily.service
 2.198s ifupdown-pre.service
 2.178s dev-vda2.device
 1.245s certbot.service
  870ms apt-daily-upgrade.service
  817ms tuned.service
  814ms systemd-timesyncd.service
  751ms networkd-dispatcher.service
  617ms pollinate.service
  572ms docker.service
  491ms keyboard-setup.service
  483ms systemd-udev-trigger.service
  455ms systemd-udevd.service
  427ms systemd-resolved.service
  401ms systemd-logind.service
  329ms apport.service
  319ms systemd-networkd.service
  310ms systemd-journald.service
  204ms containerd.service
  204ms multipathd.service
  202ms apparmor.service
  197ms dev-hugepages.mount
  195ms dev-mqueue.mount
  194ms sys-kernel-debug.mount
  189ms sys-kernel-tracing.mount
  176ms grub-common.service
  176ms polkit.service
  163ms kmod-static-nodes.service

```
#### 2. Check System Load and Uptime:

```sh
## uptime
root@applewolf:~$ uptime
13:10:20 up 35 days, 23:22,  1 user,  load average: 0.02, 0.01, 0.00

## w
root@applewolf:~$ w
 13:11:13 up 35 days, 23:22,  1 user,  load average: 0.01, 0.01, 0.00
USER     TTY      FROM             LOGIN@   IDLE   JCPU   PCPU WHAT
root pts/0    188.130.155.182  13:05    1.00s  0.06s  0.01s w

```
### Task 2: Networking Analysis

#### 1. Traceroute:

```sh
root@applewolf:~$ traceroute youtube.com

- The path to youtube.com involves multiple hops, including local network, ISP’s network, and several routers belonging to OpenAI’s infrastructure.

- Latency increases significantly after hop 7, suggesting potential congestion or bottlenecks in the path between network and OpenAI’s servers.

- The traceroute output shows a considerable number of packet losses starting from hop 5 onward, indicating potential network issues along the path to youtube.com.

- The traceroute successfully resolved youtube.com to IP address 64.233.163.93, indicating successful DNS resolution.

traceroute to youtube.com (64.233.163.93), 30 hops max, 60 byte packets
 1  _gateway (10.0.0.1)  0.145 ms  0.078 ms  0.044 ms
 2  172.31.155.1 (172.31.155.1)  0.887 ms  1.234 ms  1.437 ms
 3  172.17.22.104 (172.17.22.104)  0.318 ms 172.17.23.111 (172.17.23.111)  0.451 ms 172.17.22.104 (172.17.22.104)  0.259 ms
 4  31.135.11.2 (31.135.11.2)  1.701 ms 72.14.223.146 (72.14.223.146)  1.703 ms  1.759 ms
 5  * * *
 6  108.170.226.176 (108.170.226.176)  1.243 ms 172.253.69.88 (172.253.69.88)  1.432 ms 172.253.69.168 (172.253.69.168)  2.016 ms
 7  192.178.241.146 (192.178.241.146)  1.271 ms 192.178.241.70 (192.178.241.70)  1.631 ms 192.178.241.146 (192.178.241.146)  1.187 ms
 8  72.14.234.20 (72.14.234.20)  37.805 ms 142.250.238.214 (142.250.238.214)  18.584 ms 142.251.237.154 (142.251.237.154)  18.627 ms
 9  72.14.232.190 (72.14.232.190)  18.526 ms 172.253.65.159 (172.253.65.159)  13.038 ms 142.251.237.142 (142.251.237.142)  18.472 ms
10  142.250.56.127 (142.250.56.127)  18.449 ms 142.250.57.5 (142.250.57.5)  22.186 ms 216.239.62.13 (216.239.62.13)  15.843 ms
11  * * *
12  * * *
13  * * *
14  * * *
15  * * *
16  * * *
17  * * *
18  * * *
19  * * *
20  lj-in-f93.1e100.net (64.233.163.93)  16.232 ms  15.389 ms  16.323 ms

```

#### 2.Dig:
```sh
root@applewolf:~$ dig youtube.com

- The dig command successfully resolved the domain name youtube.com to four different IP addresses: 64.233.161.93, 64.233.161.91, 64.233.161.136, and 64.233.161.190.
- YouTube uses multiple IP addresses for its service to distribute traffic and improve performance.
- The query took 4 milliseconds to complete, which is relatively fast. This indicates that the local DNS server was able to quickly resolve the domain name.


; <<>> DiG 9.18.18-0ubuntu0.22.04.2-Ubuntu <<>> youtube.com
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 32141
;; flags: qr rd ra; QUERY: 1, ANSWER: 4, AUTHORITY: 0, ADDITIONAL: 1

;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 65494
;; QUESTION SECTION:
;youtube.com.                   IN      A

;; ANSWER SECTION:
youtube.com.            35      IN      A       64.233.161.93
youtube.com.            35      IN      A       64.233.161.91
youtube.com.            35      IN      A       64.233.161.136
youtube.com.            35      IN      A       64.233.161.190

;; Query time: 4 msec
;; SERVER: 127.0.0.53#53(127.0.0.53) (UDP)
;; WHEN: Tue Jul 02 13:30:32 MSK 2024
;; MSG SIZE  rcvd: 104

```