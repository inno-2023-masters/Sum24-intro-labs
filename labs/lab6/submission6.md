## Task 1

1. Analyze System Boot Time:

![](1.png)

Using ```systemd-analyze``` we can see how much time did it take for system to boot, adding ```blame``` allows us to see that ```plymouth-quit-wait``` service takes longest to boot.

2. Check System Load and Uptime:

![](2.png)

From next commands we can see that system was up for single main user for ~1 hour.

## Task 2

1. Traceroute:

![](3.png)

2. Dig:

![](4.png)

With this command we've found out that ip address of example.com is 93.184.215.14