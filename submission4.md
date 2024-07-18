# Software Distribution

In this lab, you will explore software distribution strategies and best practices. You will gain insights into the different approaches used to distribute software and understand the importance of effective software distribution in the development lifecycle. Follow the tasks below to complete the lab assignment.

## Task 1: Configure and Use a Local Package Repository

**Objective**: Set up a local package repository and use it to install packages.

The local package used was htop. 

1. **Create a Local Repository**:
   - Create a directory to hold your repository and place some `.deb` files in it.

     ```sh
     mkdir -p ~/local-apt-repo
     cp /path/to/package.deb ~/local-apt-repo/
     ```

2. **Generate the Package Index**:
   - Use `dpkg-scanpackages` to create a `Packages` file. Compress this file into a `Packages.gz` archive.

     ```sh
     dpkg-scanpackages ~/local-apt-repo /dev/null | gzip -9c > ~/local-apt-repo/Packages.gz
     ```

3. **Add the Local Repository to Your Sources List**:
   - Add the repository to your `sources.list`.

     ```sh
     echo "deb [trusted=yes] file:/home/yourusername/local-apt-repo ./" | sudo tee /etc/apt/sources.list.d/local-apt-repo.list
     sudo apt update
     ```


4. **Verify the Contents of the Packages.gz File:**:
   - Check that the Packages.gz file contains the correct paths and metadata for your .deb files, **it must be relative path like `./your_package.deb`**. Also you can see the package name there. Then check the repository of your package, make sure it's local one.

     ```sh
     zcat Packages.gz
     apt policy your-package-name
     ```

The output of the command `zcat Packages.gz` is the following:

```
Package: htop

Version: 3.2.2-2

Architecture: amd64

Maintainer: Daniel Lange <DLange@debian.org>

Installed-Size: 378

Depends: libc6 (>= 2.34), libncursesw6 (>= 6), libnl-3-200 (>= 3.2.7), libnl-genl-3-200 (>= 3.2.7), libtinfo6 (>= 6)

Suggests: lm-sensors, lsof, strace

Filename: /home/rafik/local-apt-repo/htop_3.2.2-2_amd64.deb

Size: 152412

MD5sum: 8c0af9bce7a18ce14ead458dbc97185a

SHA1: ca3e4bb7208ea633f4a863d9337e0242f82a6e1c

SHA256: 03f3b6ed16e96621add9577c92349d7000d13b2ae341faa28a3dfe7f7a0ff7d2

Section: utils

Priority: optional

Homepage: https://htop.dev/

Description: interactive processes viewer

 Htop is an ncursed-based process viewer similar to top, but it

 allows one to scroll the list vertically and horizontally to see

 all processes and their full command lines.

 .

 Tasks related to processes (killing, renicing) can be done without

 entering their PIDs.
```

The output of the command `apt polict htop`:

```
htop:

  Installed: 2.2.0-2build1

  Candidate: 3.2.2-2

  Version table:

     3.2.2-2 990

        990 file:/home/rafik/local-apt-repo ./ Packages

 *** 2.2.0-2build1 500

        500 http://ru.archive.ubuntu.com/ubuntu focal/main amd64 Packages

        100 /var/lib/dpkg/status

```

5. **Install a Package from the Local Repository**:
   - Install a package using `apt` from your local repository.

     ```sh
     sudo apt install your-package-name
     ```

The output of `sudo apt install htop`:

```
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
The following NEW packages will be installed:
  htop
0 upgraded, 1 newly installed, 0 to remove and 218 not upgraded.
Need to get 128 kB of archives.
After this operation, 342 kB of additional disk space will be used.
Get:1 http://ru.archive.ubuntu.com/ubuntu jammy/main amd64 htop amd64 3.0.5-7build2 [128 kB]
Fetched 128 kB in 0s (359 kB/s)
Selecting previously unselected package htop.
(Reading database ... 171752 files and directories currently installed.)
Preparing to unpack .../htop_3.0.5-7build2_amd64.deb ...
Unpacking htop (3.0.5-7build2) ...
Setting up htop (3.0.5-7build2) ...
Processing triggers for mailcap (3.70+nmu1ubuntu1) ...
Processing triggers for desktop-file-utils (0.26-1ubuntu3) ...
Processing triggers for hicolor-icon-theme (0.17-2) ...
Processing triggers for gnome-menus (3.36.0-1ubuntu3) ...
Processing triggers for man-db (2.10.2-1) ...
```

6. **Document the Process**:
   - Create a `submission4.md` file.
   - Provide step-by-step documentation of your setup and installation process in the `submission4.md` file.

## Task 2: Simulate Package Installation and Identify Dependencies

For this task, we used atop.

**Objective**: Use `apt` to simulate package installation and identify dependencies without actually installing the packages.

1. **Choose a Package to Simulate**:
   - Select a package to simulate its installation.

     ```sh
     apt-cache showpkg your-package-name
     ```

The output of `sudo apt-cache showpkg atop`:

```
Package: atop
Versions:
2.7.1-1 (/var/lib/apt/lists/ru.archive.ubuntu.com_ubuntu_dists_jammy_universe_binary-amd64_Packages)
 Description Language:
                 File: /var/lib/apt/lists/ru.archive.ubuntu.com_ubuntu_dists_jammy_universe_binary-amd64_Packages
                  MD5: 2a32ea85feda1b5ec3fb2dbfd516b9ba
 Description Language: en
                 File: /var/lib/apt/lists/ru.archive.ubuntu.com_ubuntu_dists_jammy_universe_i18n_Translation-en
                  MD5: 2a32ea85feda1b5ec3fb2dbfd516b9ba


Reverse Depends:
  hollywood,atop
Dependencies:
2.7.1-1 - init-system-helpers (2 1.54~) libc6 (2 2.34) libncursesw6 (2 6) libtinfo6 (2 6) zlib1g (2 1:1.1.4) lsb-base (2 3.2-14) cron (16 (null)) cron-daemon (0 (null))
Provides:
2.7.1-1 -
Reverse Provides:
```


2. **Simulate the Installation**:
   - Use the `-s` flag to simulate the installation.

     ```sh
     sudo apt-get install -s your-package-name
     ```

The output of `sudo apt-get install -s atop`:

```
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
The following NEW packages will be installed:
  atop
0 upgraded, 1 newly installed, 0 to remove and 218 not upgraded.
Inst atop (2.7.1-1 Ubuntu:22.04/jammy [amd64])
Conf atop (2.7.1-1 Ubuntu:22.04/jammy [amd64])
```

3. **Analyze the Output**:
   - Identify the dependencies and the packages that would be installed.
   - Document the findings in the `submission4.md` file, including which dependencies are required and their versions.

## Task 3: Hold and Unhold Package Versions

The package used in this task is powertop

**Objective**: Prevent a package from being upgraded and then allow it to be upgraded again.

1. **Install a Package**:
   - Install a package that is commonly updated.

     ```sh
     sudo apt install your-package-name
     ```

The output of the command `sudo apt install powertop`:

```
shahin@shahin-VirtualBox:~$ 
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Suggested packages:
  cpufrequtils laptop-mode-tools
The following NEW packages will be installed:
  powertop
0 upgraded, 1 newly installed, 0 to remove and 218 not upgraded.
Need to get 191 kB of archives.
After this operation, 590 kB of additional disk space will be used.
Get:1 http://ru.archive.ubuntu.com/ubuntu jammy/main amd64 powertop amd64 2.14-1build1 [191 kB]
Fetched 191 kB in 0s (483 kB/s)
Selecting previously unselected package powertop.
(Reading database ... 171762 files and directories currently installed.)
Preparing to unpack .../powertop_2.14-1build1_amd64.deb ...
Unpacking powertop (2.14-1build1) ...
Setting up powertop (2.14-1build1) ...
Processing triggers for man-db (2.10.2-1) ...
```

2. **Hold the Package**:
   - Use `apt-mark` to hold the package.

     ```sh
     sudo apt-mark hold your-package-name
     ```

The output of the command `sudo apt-mark hold powertop`:

```
powertop set on hold.
```


3. **Verify the Hold Status**:
   - Check the status of held packages.

     ```sh
     apt-mark showhold
     ```

The output of the command `apt-mark showhold`:

```
powertop
```

4. **Unhold the Package**:
   - Use `apt-mark` to unhold the package.

     ```sh
     sudo apt-mark unhold your-package-name
     ```


The output of the command `sudo apt-mark unhold powertop`:
```
Canceled hold on powertop.
```

5. **Documentation**:
   - Document the steps taken to hold and unhold the package, including any verification commands in the `submission4.md` file.

## Additional Resources

- [Apt Documentation](https://manpages.debian.org/buster/apt/apt.8.en.html)
- [Debian Package Management](https://www.debian.org/doc/manuals/debian-faq/pkg-basics.en.html)

### Guidelines

- Use proper Markdown formatting for documentation files.
- Organize files with appropriate naming conventions.
- Create a Pull Request to the main branch of the repository with your completed lab assignment.

> Note: Actively explore and document your findings to gain hands-on experience with `apt` and software distribution strategies.
