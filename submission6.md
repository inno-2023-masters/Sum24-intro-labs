# Lab 6: Operating Systems & Networking Lab
## Anton Buguev, a.buguev@innopolis.university, M23-RO-01

### Task 1. Operating System Analysis.

1. Analyze system boot time
```sh
$ systemd-analyze 

Startup finished in 11.128s (firmware) + 2.438s (loader) + 4.514s (kernel) + 27.364s (userspace) = 45.446s 
graphical.target reached after 25.521s in userspace
```

```sh
$ systemd-analyze blame 

21.361s plymouth-quit-wait.service
 6.237s NetworkManager-wait-online.service
 2.799s systemd-timesyncd.service
  943ms docker.service
  893ms snapd.seeded.service
  826ms fwupd.service
  682ms snapd.service
  538ms dev-loop1.device
  538ms dev-loop3.device
  537ms dev-loop4.device
  537ms dev-loop2.device
  537ms dev-loop0.device
  536ms dev-loop7.device
  534ms dev-loop6.device
  534ms dev-loop5.device
  456ms dev-nvme0n1p2.device
  270ms networkd-dispatcher.service
  260ms systemd-udev-trigger.service
  248ms accounts-daemon.service
  238ms systemd-logind.service
  229ms bluetooth.service
  214ms upower.service
  214ms systemd-resolved.service
  193ms user@1000.service
  191ms systemd-oomd.service
  173ms e2scrub_reap.service
  169ms ModemManager.service
```
From these outputs we can analyze how much time it takes to boot the system and which processes took the most of the time.

2. System load and uptime:
```sh
$ uptime 

 17:06:15 up  1:46,  1 user,  load average: 0.53, 0.57, 0.62
```

```sh
$ w

 17:06:16 up  1:46,  1 user,  load average: 0.53, 0.57, 0.62
USER     TTY      FROM             LOGIN@   IDLE   JCPU   PCPU WHAT
anton    tty2     tty2             15:20    1:46m  0.04s  0.04s /usr/libexec/gnome-session-binary --session=
```

From this output we can understand how many users are currently logged in.

### Task 2. Networking Analysis.
1. Perform tracerout for `innopolis.university`:
```sh
$ traceroute innopolis.university

traceroute to innopolis.university (213.159.212.4), 64 hops max
  1   192.168.0.1  6.765ms  4.640ms  2.075ms 
  2   10.16.255.135  10.048ms  3.004ms  3.091ms 
  3   10.16.248.213  6.775ms  7.115ms  6.191ms 
  4   10.16.248.150  3.460ms  3.194ms  4.024ms 
  5   10.16.248.189  4.074ms  4.732ms  7.624ms 
  6   195.208.211.53  17.359ms  17.176ms  17.277ms 
  7   195.208.211.53  19.934ms  18.009ms  17.956ms 
  8   139.45.243.3  30.777ms  36.251ms  34.103ms 
  9   *  *  * 
 10   *  *  * 
 11   213.159.212.4  21.365ms !*  18.682ms !*  21.178ms !* 
 ```

2. Perform DNS lookup for `innopolis.university`:
```sh
$ dig innopolis.university

; <<>> DiG 9.18.24-0ubuntu0.22.04.1-Ubuntu <<>> innopolis.university
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 38928
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 1

;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 65494
;; QUESTION SECTION:
;innopolis.university.		IN	A

;; ANSWER SECTION:
innopolis.university.	448	IN	A	213.159.212.4

;; Query time: 0 msec
;; SERVER: 127.0.0.53#53(127.0.0.53) (UDP)
;; WHEN: Tue Jul 02 18:46:56 MSK 2024
;; MSG SIZE  rcvd: 65
```