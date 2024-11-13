# Operating Systems & Networking Lab

In this lab, you will explore operating systems and networking fundamentals in a DevOps context. You will gain practical experience in working with operating systems and perform network-related tasks. Follow the tasks below to complete the lab assignment.

## Task 1: Operating System Analysis

**Objective**: Analyze and understand key aspects of the operating system's performance and uptime.

1. **Analyze System Boot Time**:
   - `systemd-analyze`

     Output:
     ```
     Startup finished in 10.688s (firmware) + 3.268s (loader) + 2.463s (kernel) + 11.253s (userspace) = 27.673s 
     graphical.target reached after 11.236s in userspace
     ```
     Interesting observation: I had broken VPN, which worked through stunnel4 service. This service could not start properly and continueusly restarted, making boot not finished for infinite time. On one side, OS was booted and worked properly, on the other side, it showed that it boots infinitely long.

   - `systemd-analyze blame`  
     Output:
     ```
      stepan@stepan-ASUS:~/DO$ systemd-analyze blame
      8.174s NetworkManager-wait-online.service
      4.682s plymouth-quit-wait.service
      3.871s snap.docker.nvidia-container-toolkit.service
      1.184s gpu-manager.service
      813ms fwupd.service
      664ms docker.service
      558ms snapd.seeded.service
      460ms dev-loop4.device
      460ms dev-loop6.device
      460ms dev-loop7.device
      393ms snapd.service
      381ms dev-loop5.device
      372ms dev-loop3.device
      366ms dev-loop0.device
      359ms dev-loop2.device
      359ms dev-loop1.device
      249ms systemd-resolved.service
      237ms dev-nvme0n1p2.device
      234ms systemd-oomd.service
      228ms systemd-timesyncd.service
      148ms dpkg-db-backup.service
      147ms networkd-dispatcher.service
      141ms udisks2.service
      133ms containerd.service
      132ms apport-autoreport.service
      120ms accounts-daemon.service
      114ms qemu-kvm.service
      114ms bolt.service
      113ms bluetooth.service
      108ms apport.service
      105ms user@1000.service
      101ms systemd-logind.service
      96ms power-profiles-daemon.service
      91ms systemd-udev-trigger.service
      91ms systemd-journald.service
      84ms avahi-daemon.service
      79ms upower.service
      78ms dev-loop10.device
      78ms dev-loop15.device
     ```
     Since my OS started quite quickly, I believe that `8.174s NetworkManager-wait-online.service` is the same way as stunnel in the previous step working in the background during booting and does not really affect the booting time.

2. **Check System Load and Uptime**:
   - Use `uptime` and `w` to check system load and uptime.

     ```sh
     uptime
     ```
     Output (pretty strightforward):
     ```
     00:03:39 up 6 min,  2 users,  load average: 0,33, 0,47, 0,26
     ```
     Interesting fact: it shows 2 active users. It looks strange, but we will find the reason by the next command.
     ```sh
     w
     ```
     Output:
     ```
      00:05:10 up 7 min,  2 users,  load average: 1,06, 0,65, 0,34
      USER     TTY      FROM             LOGIN@   IDLE   JCPU   PCPU WHAT
      stepan   :1       :1               23:57   ?xdm?   2:50   0.00s /usr/libexec/gdm-x-session --run-script env GNOME_SHELL_SESSION_MODE=ubuntu /usr/bin/gnome-session --session=ubuntu
      stepan   pts/0    :1               23:57    1.00s  0.01s  0.00s w
     ```
     Here we can see, that the two users are just two instanses of one user:  
     1) The GUI of our OS.
     2) The virtual terminal (GUI terminal is actually a virtual terminal)

3. **Document the Analysis**:
   - Create a `submission6.md` file.
   - Provide the output of `systemd-analyze`, `uptime`, and `w` commands in the `submission6.md` file.
   - Include any observations or insights regarding system boot time, load, and uptime.

## Task 2: Networking Analysis

**Objective**: Perform network diagnostics and analyze DNS resolution to understand network paths and latency.

1. **Traceroute**:
   - Use the appropriate command or tool to perform a traceroute to a specified website or IP address.

     ```sh
     traceroute yandex.ru
     ```
     Output:
     ```
      1   10.248.1.1  1,098ms  0,999ms  0,998ms 
      2   10.250.0.2  0,717ms  0,611ms  0,617ms 
      3   10.252.6.1  1,141ms  0,808ms  0,814ms 
      4   188.170.164.34  6,040ms  4,279ms  4,150ms 
      5   *  *  * 
      6   *  *  * 
      7   83.169.204.176  16,821ms  16,161ms  16,236ms 
      8   93.158.160.149  19,531ms  19,197ms  21,078ms 
      9   *  *  * 
      10   *  *  * 
      11   *  *  * 
      12   *  *  * 
      13   *  *  * 
      14   *  *  * 
      15   *  *  * 
      16   *  *  * 
      17   *  *  * 
      18   *  *  * 
      19   *  *  * 
      20   *  *  * 
      21   * ^C
     ```
     For some reason, on some step of the network (after trying various amount of completely different websites, it seems like the problem is on the side of provider in the university) some middle server is not replying to ICMP.

     ```
     ping yandex.ru
     ```
     Output:
     ```
      PING yandex.ru (213.180.193.56) 56(84) bytes of data.
      64 bytes from familysearch.yandex.ru (213.180.193.56): icmp_seq=1 ttl=53 time=22.2 ms
      64 bytes from familysearch.yandex.ru (213.180.193.56): icmp_seq=2 ttl=53 time=21.6 ms
     ```
     So, the problem is definitely not in connection.

2. **Dig**:
   - Use the appropriate command or tool to perform a DNS lookup for a specified domain name.

     ```sh
     dig yandex.ru
     ```

     ```
      ; <<>> DiG 9.18.28-0ubuntu0.22.04.1-Ubuntu <<>> yandex.ru
      ;; global options: +cmd
      ;; Got answer:
      ;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 55712
      ;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 1

      ;; OPT PSEUDOSECTION:
      ; EDNS: version: 0, flags:; udp: 65494
      ;; QUESTION SECTION:
      ;yandex.ru.                     IN      A

      ;; ANSWER SECTION:
      yandex.ru.              272     IN      A       213.180.193.56

      ;; Query time: 2 msec
      ;; SERVER: 127.0.0.53#53(127.0.0.53) (UDP)
      ;; WHEN: Wed Nov 13 00:16:39 MSK 2024
      ;; MSG SIZE  rcvd: 54
     ```
     From the answer we can find that yandex.ru is 213.180.193.56. This might be the closest (by network) ip of the yandex, not the only one.

3. **Document the Networking Analysis**:
   - Add the output of the `traceroute` and `dig` commands to the `submission6.md` file.
   - Include any observations or insights regarding the network path, latency, and DNS resolution.
