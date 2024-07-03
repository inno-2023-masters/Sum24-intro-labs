# Task 1: Key Metrics for SRE and SLAs

## Monitor System Resources:
### Top 3 apps consuming memory:
1. Firefox browser - 3.4% 

![Firefox browser](./Monitor%20System%20Resources/Memory/Снимок%20экрана%20от%202024-07-03%2001-41-48.png)

2. Fgnome shell - 2.5% 

![gnome shell](./Monitor%20System%20Resources/Memory/Снимок%20экрана%20от%202024-07-03%2001-42-02.png)

3. IDE VScode - 1.1% 

![IDE VScode](./Monitor%20System%20Resources/Memory/Снимок%20экрана%20от%202024-07-03%2001-42-22.png)

### Top 3 apps consuming CPU:

1. gnome-shell - 26%
2. gnome-control-center-search-provider 3.9%
3. htop 3.3%

![](./Monitor%20System%20Resources/CPU/Снимок%20экрана%20от%202024-07-03%2001-54-04.png)

### Top 3 apps consuming I/O:

* There are no I/O background operations. I believe that's because I don't use this OS as my main OS, therefore there are no apps

![](./Monitor%20System%20Resources/Input%20Output/Снимок%20экрана%20от%202024-07-03%2002-06-14.png)

## Monitor System Resources:
### the top 3 largest files:
![](./Disk%20Space%20Management/Снимок%20экрана%20от%202024-07-03%2002-17-03.png)

- sudo: Allows the command to be executed as a superuser or another user.
- find /var -type f: Searches for files (-type f) in the /var directory.
- -exec du -Sh {} +: Executes the du -Sh command on each file found, which calculates the disk usage of each file in a human-readable format.
- |: Pipes the output of the previous command to the next command.
- sort -rh: Sorts the output in reverse order (-r) based on human-readable file sizes (-h).
- head -n 3: Displays the first 3 lines of the sorted output, which are the top 3 largest files in the /var directory.

# Task 2: Terraform Installation and Nginx Deployment