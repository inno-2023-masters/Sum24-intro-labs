# Submission for Lab 6

## Task 1

### Running `systemd-analyze`

![SA](/Resources/sa.png)

### Running `systemd-analyze blame`

![SAB](/Resources/sab.png)

### Running `uptime` and `w`

![Uptime and W](/Resources/uptime+w.png)

**Notes:**

* I got an error when I tried to run `systemd-analyze` on WSL, so I had to switch to my VM

* From the system the first screenshot we can see that the system booted in ~54s, ~4s of which were for the kernal while the rest were for the userspace.

* Running the `blame` option we can see how long did it take each service to boot.

* From the `uptime` and `w` commands we can see that the system has been up for ~3 hours with only a single user (me) being the main user.

## Task 2

### Running `traceroute`

![traceroute](/Resources/traceroute.png)

### Running `dig`

![dig](/Resources/dig.png)

**Notes:**

* It can be seen from `traceroute` that it took 11 hops starting from my machine to reach the destination.

* It can be seen that it took 4 hops to exit the local network.

* Using `dig` we were able to find the IPv4 address of `example.com` which is `93.184.215.14`
