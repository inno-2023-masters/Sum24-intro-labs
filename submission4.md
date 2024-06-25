# Lab 4: Software Distribution
## Anton Buguev, a.buguev@innopolis.university, M23-RO-01

### Task 1. Configure and Use a Local Package Repository

1. Create folder and copy `.deb` file in it:
```sh
$ mkdir -p ~/local-apt-repo
$ cp Downloads/google-chrome-stable_current_amd64.deb ~/local-apt-repo/
```

2. Create a Packages file
```sh
$ dpkg-scanpackages ~/local-apt-repo /dev/null | gzip -9c > ~/local-apt-repo/Packages.gz

dpkg-scanpackages: warning: Packages in archive but missing from override file:
dpkg-scanpackages: warning:   google-chrome-stable
dpkg-scanpackages: info: Wrote 1 entries to output Packages file.
```

3. Add the repository to `sources.list`:
```sh
$ echo "deb [trusted=yes] file:/home/anton/local-apt-repo ./" | sudo tee /etc/apt/sources.list.d/local-apt-repo.list 

deb [trusted=yes] file:/home/anton/local-apt-repo ./
```

4. Verify the Contents of the Packages.gz File:
```sh
$ zcat local-apt-repo/Packages.gz

Package: google-chrome-stable
Version: 126.0.6478.126-1
Architecture: amd64
Maintainer: Chrome Linux Team <chromium-dev@chromium.org>
Installed-Size: 340311
Pre-Depends: dpkg (>= 1.14.0)
Depends: ca-certificates, fonts-liberation, libasound2 (>= 1.0.17), libatk-bridge2.0-0 (>= 2.5.3), libatk1.0-0 (>= 2.2.0), libatspi2.0-0 (>= 2.9.90), libc6 (>= 2.17), libcairo2 (>= 1.6.0), libcups2 (>= 1.6.0), libcurl3-gnutls | libcurl3-nss | libcurl4 | libcurl3, libdbus-1-3 (>= 1.9.14), libdrm2 (>= 2.4.75), libexpat1 (>= 2.1~beta3), libgbm1 (>= 17.1.0~rc2), libglib2.0-0 (>= 2.39.4), libgtk-3-0 (>= 3.9.10) | libgtk-4-1, libnspr4 (>= 2:4.9-2~), libnss3 (>= 2:3.35), libpango-1.0-0 (>= 1.14.0), libu2f-udev, libvulkan1, libx11-6 (>= 2:1.4.99.1), libxcb1 (>= 1.9.2), libxcomposite1 (>= 1:0.4.4-1), libxdamage1 (>= 1:1.1), libxext6, libxfixes3, libxkbcommon0 (>= 0.5.0), libxrandr2, wget, xdg-utils (>= 1.0.2)
Provides: www-browser
Filename: /home/anton/local-apt-repo/google-chrome-stable_current_amd64.deb
Size: 108773084
MD5sum: d56770acc540af16f377316646dd774a
SHA1: 1d22a19710426f41884f6d2a41415bd70824ff7a
SHA256: 3ec1cadbb55cf66cc51f0421eace324a88836ee2d982b945b8f67a3f131b0924
Section: web
Priority: optional
Description: The web browser from Google
 Google Chrome is a browser that combines a minimal design with sophisticated technology to make the web faster, safer, and easier.

```

```sh
$ apt policy google-chrome-stable

google-chrome-stable:
  Installed: 125.0.6422.141-1
  Candidate: 126.0.6478.126-1
  Version table:
     126.0.6478.126-1 500
        500 https://dl.google.com/linux/chrome/deb stable/main amd64 Packages
        500 file:/home/anton/local-apt-repo ./ Packages
 *** 125.0.6422.141-1 100
        100 /var/lib/dpkg/status
```

5. Install file from local repository
```sh
$ sudo apt install google-chrome-stable

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  python3-cliapp python3-markdown python3-packaging python3-ttystatus
Use 'sudo apt autoremove' to remove them.
The following NEW packages will be installed:
  google-chrome-stable
0 upgraded, 1 newly installed, 0 to remove and 48 not upgraded.
Need to get 109 MB of archives.
After this operation, 348 MB of additional disk space will be used.
Get:1 https://dl.google.com/linux/chrome/deb stable/main amd64 google-chrome-stable amd64 126.0.6478.126-1 [109 MB]
Fetched 109 MB in 11s (9 975 kB/s)                                             
Selecting previously unselected package google-chrome-stable.
(Reading database ... 374917 files and directories currently installed.)
Preparing to unpack .../google-chrome-stable_126.0.6478.126-1_amd64.deb ...
Unpacking google-chrome-stable (126.0.6478.126-1) ...
Setting up google-chrome-stable (126.0.6478.126-1) ...
update-alternatives: using /usr/bin/google-chrome-stable to provide /usr/bin/x-w
ww-browser (x-www-browser) in auto mode
update-alternatives: using /usr/bin/google-chrome-stable to provide /usr/bin/gno
me-www-browser (gnome-www-browser) in auto mode
update-alternatives: using /usr/bin/google-chrome-stable to provide /usr/bin/goo
gle-chrome (google-chrome) in auto mode
Processing triggers for mime-support (3.64ubuntu1) ...
Processing triggers for gnome-menus (3.36.0-1ubuntu1) ...
Processing triggers for man-db (2.9.1-1) ...
Processing triggers for desktop-file-utils (0.24-1ubuntu3) ...
```