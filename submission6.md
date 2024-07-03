# Task 1

## systemd-analyze
![](/screens/systemd-analyze.png)
![](/screens/systemd-analyze%20blame.png)

Longest Startup Services:
```shell
    apt-daily.service
    snapd.seeded.service
    plymouth-quit-wait.service
```
## uptime & w
![](/screens/up_w.png)

Uptime: The system has been up for 1 day and 11 hours 

Load Average: The load average values indicate the system load over the last 1, 5, and 15 minutes.

User Activity: There is one user "aslan".

# Task 2

## traceroute
![](/screens/traceroute.png)

The traceroute to google.com (216.239.38.120) shows the path through various network routers with differing latency levels, indicating potential geographic distances and network congestion. Some routers along the route do not respond to ICMP packets, likely due to firewall settings or packet filtering.

## dig
![](/screens/dig.png)

The dig command for google.com shows it resolves to forcesafesearch.google.com with IP 216.239.38.120, processed quickly (0 msec). This is local DNS resolution.