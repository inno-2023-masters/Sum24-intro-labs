
base) kamil@kamil-Predator-G3-571:~/Desktop/MS01/summer/devops/Sum24-intro-labs$ dpkg-scanpackages ~/local-apt-repo /dev/null | gzip -9c > ~/local-apt-repo/Packages.gz
dpkg-scanpackages: warning: Packages in archive but missing from override file:
dpkg-scanpackages: warning:   discord
dpkg-scanpackages: info: Wrote 1 entries to output Packages file.
(base) kamil@kamil-Predator-G3-571:~/Desktop/MS01/summer/devops/Sum24-intro-labs$ echo "deb [trusted=yes] file:/home/yourusername/local-apt-repo ./" | sudo tee /etc/apt/sources.list.d/local-apt-repo.list
sudo apt update
deb [trusted=yes] file:/home/yourusername/local-apt-repo ./
Get:1 file:/home/yourusername/local-apt-repo ./ InRelease
Ign:1 file:/home/yourusername/local-apt-repo ./ InRelease
Get:2 file:/usr/lib/expressvpn/repo_mirror.list Mirrorlist [117 B]
Get:3 file:/home/yourusername/local-apt-repo ./ Release
Ign:3 file:/home/yourusername/local-apt-repo ./ Release
Get:5 file:/home/yourusername/local-apt-repo ./ Packages
Ign:5 file:/home/yourusername/local-apt-repo ./ Packages
Get:6 file:/home/yourusername/local-apt-repo ./ Translation-en_US                                                      
Ign:6 file:/home/yourusername/local-apt-repo ./ Translation-en_US                                                      
Get:7 file:/home/yourusername/local-apt-repo ./ Translation-en                                                         
Ign:7 file:/home/yourusername/local-apt-repo ./ Translation-en                                                         
Get:5 file:/home/yourusername/local-apt-repo ./ Packages                                                               
Ign:5 file:/home/yourusername/local-apt-repo ./ Packages                                                               
Get:6 file:/home/yourusername/local-apt-repo ./ Translation-en_US                                                      
Ign:6 file:/home/yourusername/local-apt-repo ./ Translation-en_US                                                      
Get:7 file:/home/yourusername/local-apt-repo ./ Translation-en                                                         
Ign:7 file:/home/yourusername/local-apt-repo ./ Translation-en                                                         
Get:5 file:/home/yourusername/local-apt-repo ./ Packages                                                               
Ign:5 file:/home/yourusername/local-apt-repo ./ Packages                                                               
Get:6 file:/home/yourusername/local-apt-repo ./ Translation-en_US                                                      
Ign:6 file:/home/yourusername/local-apt-repo ./ Translation-en_US                                                      
Get:7 file:/home/yourusername/local-apt-repo ./ Translation-en                                                         
Ign:7 file:/home/yourusername/local-apt-repo ./ Translation-en                                                         
Get:5 file:/home/yourusername/local-apt-repo ./ Packages                                                               
Ign:5 file:/home/yourusername/local-apt-repo ./ Packages                                                                                
Get:6 file:/home/yourusername/local-apt-repo ./ Translation-en_US                                                                       
Ign:6 file:/home/yourusername/local-apt-repo ./ Translation-en_US                                                                                
Get:7 file:/home/yourusername/local-apt-repo ./ Translation-en                                                                                   
Ign:7 file:/home/yourusername/local-apt-repo ./ Translation-en                                                                                
Get:5 file:/home/yourusername/local-apt-repo ./ Packages                                                                                      
Ign:5 file:/home/yourusername/local-apt-repo ./ Packages                                                                                
Get:6 file:/home/yourusername/local-apt-repo ./ Translation-en_US                                                                       
Ign:6 file:/home/yourusername/local-apt-repo ./ Translation-en_US                                                                                
Get:7 file:/home/yourusername/local-apt-repo ./ Translation-en                                                                                   
Ign:7 file:/home/yourusername/local-apt-repo ./ Translation-en                                                                                
Get:5 file:/home/yourusername/local-apt-repo ./ Packages                                                                                      
Ign:5 file:/home/yourusername/local-apt-repo ./ Packages                                                                                
Get:6 file:/home/yourusername/local-apt-repo ./ Translation-en_US                                                                       
Ign:6 file:/home/yourusername/local-apt-repo ./ Translation-en_US                                                                                
Get:7 file:/home/yourusername/local-apt-repo ./ Translation-en                                                                                   
Ign:7 file:/home/yourusername/local-apt-repo ./ Translation-en                                                         
Get:5 file:/home/yourusername/local-apt-repo ./ Packages                                                               
Err:5 file:/home/yourusername/local-apt-repo ./ Packages                                                               
  File not found - /home/yourusername/local-apt-repo/./Packages (2: No such file or directory)
Get:6 file:/home/yourusername/local-apt-repo ./ Translation-en_US                                                      
Ign:6 file:/home/yourusername/local-apt-repo ./ Translation-en_US                                                      
Hit:9 https://dl.google.com/linux/chrome/deb stable InRelease                                                                                                                    
Hit:10 https://download.docker.com/linux/ubuntu jammy InRelease                                                                                                                  
Ign:11 https://apt.releases.hashicorp.com jammy InRelease                                                                                                                        
Hit:12 http://archive.ubuntu.com/ubuntu jammy InRelease                                                                                                                          
Err:13 https://apt.releases.hashicorp.com jammy Release                                                              
  404  Not Found [IP: 18.165.140.52 443]
Hit:8 https://packages.microsoft.com/repos/code stable InRelease                                                     
Hit:14 http://archive.ubuntu.com/ubuntu jammy-updates InRelease                           
Ign:15 https://developer.download.nvidia.com/compute/cuda/repos/ubuntu22.04/x86_64  InRelease
Get:4 https://repo.expressvpn.com/public/deb/debian any-version InRelease [4 580 B]
Hit:16 http://archive.ubuntu.com/ubuntu jammy-backports InRelease                    
Hit:17 http://archive.ubuntu.com/ubuntu jammy-security InRelease
Ign:18 https://developer.download.nvidia.com/compute/machine-learning/repos/ubuntu22.04/x86_64  InRelease
Err:19 https://developer.download.nvidia.com/compute/cuda/repos/ubuntu22.04/x86_64  Release
  404  Not Found [IP: 152.199.20.126 443]
Err:20 https://developer.download.nvidia.com/compute/machine-learning/repos/ubuntu22.04/x86_64  Release
  404  Not Found [IP: 152.199.20.126 443]
Reading package lists... Done
E: The repository 'https://apt.releases.hashicorp.com jammy Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'https://developer.download.nvidia.com/compute/cuda/repos/ubuntu22.04/x86_64  Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'https://developer.download.nvidia.com/compute/machine-learning/repos/ubuntu22.04/x86_64  Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
(base) kamil@kamil-Predator-G3-571:~/Desktop/MS01/summer/devops/Sum24-intro-labs$ zcat Packages.gz
apt policy your-package-name
gzip: Packages.gz: No such file or directory
N: Unable to locate package your-package-name
(base) kamil@kamil-Predator-G3-571:~/Desktop/MS01/summer/devops/Sum24-intro-labs$ cd ~/local-apt-repo/
(base) kamil@kamil-Predator-G3-571:~/local-apt-repo$ zcat Pa
gzip: Pa.gz: No such file or directory
(base) kamil@kamil-Predator-G3-571:~/local-apt-repo$ zcat Packages.gz
Package: discord
Version: 0.0.57
Architecture: amd64
Maintainer: Discord Maintainer Team <native-team@discord.com>
Installed-Size: 248448
Depends: libc6, libasound2, libatomic1, libnotify4, libnspr4, libnss3, libstdc++6, libxss1, libxtst6
Recommends: libappindicator1 | libayatana-appindicator1
Filename: /home/kamil/local-apt-repo/discord-0.0.57.deb
Size: 100957642
MD5sum: 247903cc261511fc65ec60d8efae1635
SHA1: eb42c80ba58358a127abfc9e3df46974f982469c
SHA256: 0c5f8ca2a67d6544f6c788ad297a1289319de6a7df1306def926bda1474bdf76
Section: net
Priority: optional
Homepage: https://discord.com
Description: Chat for Communities and Friends
 Discord is the easiest way to communicate over voice, video, and text. Chat,
 hang out, and stay close with your friends and communities.

(base) kamil@kamil-Predator-G3-571:~/local-apt-repo$ apt policy discord
discord:
  Installed: 0.0.57
  Candidate: 0.0.57
  Version table:
 *** 0.0.57 100
        100 /var/lib/dpkg/status
(base) kamil@kamil-Predator-G3-571:~/local-apt-repo$ sudo apt install discord 
Waiting for cache lock: Could not get lock /var/lib/dpkg/lock-frontend. It is held by process 961504 (apt)      
Waiting for cache lock: Could not get lock /var/lib/dpkg/lock-frontend. It is held by process 961504 (apt)      
Waiting for cache lock: Could not get lock /var/lib/dpkg/lock-frontend. It is held by process 961504 (apt)      
Waiting for cache lock: Could not get lock /var/lib/dpkg/lock-frontend. It is held by process 961504 (apt)      
Waiting for cache lock: Could not get lock /var/lib/dpkg/lock-frontend. It is held by process 961504 (apt)      
Waiting for cache lock: Could not get lock /var/lib/dpkg/lock-frontend. It is held by process 961504 (apt)      
Waiting for cache lock: Could not get lock /var/lib/dpkg/lock-frontend. It is held by process 961504 (apt)      
Waiting for cache lock: Could not get lock /var/lib/dpkg/lock-frontend. It is held by process 961504 (apt)      
^Ziting for cache lock: Could not get lock /var/lib/dpkg/lock-frontend. It is held by process 961504 (apt)... 8s
[4]+  Stopped                 sudo apt install discord
(base) kamil@kamil-Predator-G3-571:~/local-apt-repo$ kill -9 961504
bash: kill: (961504) - Operation not permitted
(base) kamil@kamil-Predator-G3-571:~/local-apt-repo$ sudo kill -9 961504
(base) kamil@kamil-Predator-G3-571:~/local-apt-repo$ apt policy discord
discord:
  Installed: 0.0.57
  Candidate: 0.0.57
  Version table:
 *** 0.0.57 100
        100 /var/lib/dpkg/status
(base) kamil@kamil-Predator-G3-571:~/local-apt-repo$ sudo apt install discord 
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
discord is already the newest version (0.0.57).
The following package was automatically installed and is no longer required:
  dctrl-tools
Use 'sudo apt autoremove' to remove it.
0 upgraded, 0 newly installed, 0 to remove and 5 not upgraded.
14 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] n
Abort.
(base) kamil@kamil-Predator-G3-571:~/local-apt-repo$ ^C
(base) kamil@kamil-Predator-G3-571:~/local-apt-repo$ apt-cache showpkg your-package-name
N: Unable to locate package your-package-name
(base) kamil@kamil-Predator-G3-571:~/local-apt-repo$ apt-cache showpkg discord
Package: discord
Versions: 
0.0.57 (/var/lib/dpkg/status)
 Description Language: 
                 File: /var/lib/dpkg/status
                  MD5: dc48a6c0dd93c5bf26a401011c2383b3


Reverse Depends: 
Dependencies: 
0.0.57 - libc6 (0 (null)) libasound2 (0 (null)) libatomic1 (0 (null)) libnotify4 (0 (null)) libnspr4 (0 (null)) libnss3 (0 (null)) libstdc++6 (0 (null)) libxss1 (0 (null)) libxtst6 (0 (null)) libappindicator1 (16 (null)) libayatana-appindicator1 (0 (null)) 
Provides: 
0.0.57 - 
Reverse Provides: 
(base) kamil@kamil-Predator-G3-571:~/local-apt-repo$ sudo apt-get install -s discord
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
discord is already the newest version (0.0.57).
The following package was automatically installed and is no longer required:
  dctrl-tools
Use 'sudo apt autoremove' to remove it.
0 upgraded, 0 newly installed, 0 to remove and 5 not upgraded.
14 not fully installed or removed.
Conf lsb-release (11.1.0ubuntu4 Ubuntu:22.04/jammy [all])
Conf zoom (6.0.2.4680  [amd64])
Conf python3-gi (3.42.1-0ubuntu1 Ubuntu:22.04/jammy-updates [amd64])
Conf python3-ibus-1.0 (1.5.26-4 Ubuntu:22.04/jammy [all])
Conf python3 (3.10.6-1~22.04 Ubuntu:22.04/jammy-updates, Ubuntu:22.04/jammy-security [amd64])
Conf onboard-common (1.4.1-5build5 Ubuntu:22.04/jammy [all])
Conf python3-cairo (1.20.1-3build1 Ubuntu:22.04/jammy [amd64])
Conf python3-apt (2.4.0ubuntu3 Ubuntu:22.04/jammy-updates [amd64])
Conf onboard-data (1.4.1-5build5 Ubuntu:22.04/jammy [all])
Conf steam-launcher (1:1.0.0.79  [all])
Conf ibus (1.5.26-4 Ubuntu:22.04/jammy [amd64])
Conf onboard (1.4.1-5build5 Ubuntu:22.04/jammy [amd64])
Conf python3-dbus (1.2.18-3build1 Ubuntu:22.04/jammy [amd64])
Conf python3-gi-cairo (3.42.1-0ubuntu1 Ubuntu:22.04/jammy-updates [amd64])
(base) kamil@kamil-Predator-G3-571:~/local-apt-repo$ sudo apt install vim
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
The following package was automatically installed and is no longer required:
  dctrl-tools
Use 'sudo apt autoremove' to remove it.
The following additional packages will be installed:
  libpython3.10 libsodium23 vim-common vim-runtime xxd
Suggested packages:
  ctags vim-doc vim-scripts
The following NEW packages will be installed:
  libpython3.10 libsodium23 vim vim-common vim-runtime xxd
0 upgraded, 6 newly installed, 0 to remove and 5 not upgraded.
14 not fully installed or removed.
Need to get 10,8 MB of archives.
After this operation, 44,6 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://archive.ubuntu.com/ubuntu jammy-updates/main amd64 xxd amd64 2:8.2.3995-1ubuntu2.17 [53,7 kB]
Get:2 http://archive.ubuntu.com/ubuntu jammy-updates/main amd64 vim-common all 2:8.2.3995-1ubuntu2.17 [81,5 kB]
Get:3 http://archive.ubuntu.com/ubuntu jammy-updates/main amd64 libpython3.10 amd64 3.10.12-1~22.04.4 [1 949 kB]
Get:4 http://archive.ubuntu.com/ubuntu jammy/main amd64 libsodium23 amd64 1.0.18-1build2 [164 kB]
Get:5 http://archive.ubuntu.com/ubuntu jammy-updates/main amd64 vim-runtime all 2:8.2.3995-1ubuntu2.17 [6 827 kB]
Get:6 http://archive.ubuntu.com/ubuntu jammy-updates/main amd64 vim amd64 2:8.2.3995-1ubuntu2.17 [1 734 kB]
Fetched 10,8 MB in 2s (5 477 kB/s)
debconf: unable to initialize frontend: Dialog
debconf: (Dialog frontend requires a screen at least 13 lines tall and 31 columns wide.)
debconf: falling back to frontend: Readline
Selecting previously unselected package xxd.
dpkg: warning: files list file for package 'systemd' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'systemd-hwe-hwdb' missing; assuming package has no files currently installed
(Reading database ... 46397 files and directories currently installed.)
Preparing to unpack .../0-xxd_2%3a8.2.3995-1ubuntu2.17_amd64.deb ...
Unpacking xxd (2:8.2.3995-1ubuntu2.17) ...
Selecting previously unselected package vim-common.
Preparing to unpack .../1-vim-common_2%3a8.2.3995-1ubuntu2.17_all.deb ...
Unpacking vim-common (2:8.2.3995-1ubuntu2.17) ...
Selecting previously unselected package libpython3.10:amd64.
Preparing to unpack .../2-libpython3.10_3.10.12-1~22.04.4_amd64.deb ...
Unpacking libpython3.10:amd64 (3.10.12-1~22.04.4) ...
Selecting previously unselected package libsodium23:amd64.
Preparing to unpack .../3-libsodium23_1.0.18-1build2_amd64.deb ...
Unpacking libsodium23:amd64 (1.0.18-1build2) ...
Selecting previously unselected package vim-runtime.
Preparing to unpack .../4-vim-runtime_2%3a8.2.3995-1ubuntu2.17_all.deb ...
Adding 'diversion of /usr/share/vim/vim82/doc/help.txt to /usr/share/vim/vim82/doc/help.txt.vim-tiny by vim-runtime'
Adding 'diversion of /usr/share/vim/vim82/doc/tags to /usr/share/vim/vim82/doc/tags.vim-tiny by vim-runtime'
Unpacking vim-runtime (2:8.2.3995-1ubuntu2.17) ...
Selecting previously unselected package vim.
Preparing to unpack .../5-vim_2%3a8.2.3995-1ubuntu2.17_amd64.deb ...
Unpacking vim (2:8.2.3995-1ubuntu2.17) ...
Setting up libpython3.10:amd64 (3.10.12-1~22.04.4) ...
Setting up libsodium23:amd64 (1.0.18-1build2) ...
Setting up python3 (3.10.6-1~22.04) ...
running python rtupdate hooks for python3.10...
dpkg-query: package 'gedit' is not installed
Use dpkg --contents (= dpkg-deb --contents) to list archive files contents.
dpkg-query: package 'gedit' is not installed
Use dpkg --contents (= dpkg-deb --contents) to list archive files contents.
dpkg-query: package 'hplip-data' is not installed
Use dpkg --contents (= dpkg-deb --contents) to list archive files contents.
dpkg-query: package 'hplip-data' is not installed
Use dpkg --contents (= dpkg-deb --contents) to list archive files contents.
dpkg-query: package 'ibus-table' is not installed
Use dpkg --contents (= dpkg-deb --contents) to list archive files contents.
dpkg-query: package 'ibus-table' is not installed
Use dpkg --contents (= dpkg-deb --contents) to list archive files contents.
dpkg-query: package 'python3-uno' is not installed
Use dpkg --contents (= dpkg-deb --contents) to list archive files contents.
dpkg-query: package 'python3-uno' is not installed
Use dpkg --contents (= dpkg-deb --contents) to list archive files contents.
dpkg-query: package 'rhythmbox-plugin-alternative-toolbar' is not installed
Use dpkg --contents (= dpkg-deb --contents) to list archive files contents.
dpkg-query: package 'rhythmbox-plugin-alternative-toolbar' is not installed
Use dpkg --contents (= dpkg-deb --contents) to list archive files contents.
dpkg-query: package 'rhythmbox-plugins' is not installed
Use dpkg --contents (= dpkg-deb --contents) to list archive files contents.
dpkg-query: package 'rhythmbox-plugins' is not installed
Use dpkg --contents (= dpkg-deb --contents) to list archive files contents.
dpkg-query: package 'system-config-printer-common' is not installed
Use dpkg --contents (= dpkg-deb --contents) to list archive files contents.
dpkg-query: package 'system-config-printer-common' is not installed
Use dpkg --contents (= dpkg-deb --contents) to list archive files contents.
dpkg-query: package 'system-config-printer' is not installed
Use dpkg --contents (= dpkg-deb --contents) to list archive files contents.
dpkg-query: package 'system-config-printer' is not installed
Use dpkg --contents (= dpkg-deb --contents) to list archive files contents.
dpkg-query: package 'ubuntu-drivers-common' is not installed
Use dpkg --contents (= dpkg-deb --contents) to list archive files contents.
dpkg-query: package 'ubuntu-drivers-common' is not installed
Use dpkg --contents (= dpkg-deb --contents) to list archive files contents.
running python post-rtupdate hooks for python3.10...
  File "/usr/share/python3/python.mk", line 20
    py_sitename = $(if $(filter $(subst python,,$(1)), 2.3 2.4 2.5),site,dist)-packages
                  ^
SyntaxError: invalid syntax
dpkg: error processing package python3 (--configure):
 installed python3 package post-installation script subprocess returned error exit status 1
Setting up xxd (2:8.2.3995-1ubuntu2.17) ...
Setting up vim-common (2:8.2.3995-1ubuntu2.17) ...
dpkg: dependency problems prevent configuration of python3-gi:
 python3-gi depends on python3 (<< 3.11); however:
  Package python3 is not configured yet.
 python3-gi depends on python3 (>= 3.10~); however:
  Package python3 is not configured yet.
 python3-gi depends on python3:any; however:
  Package python3 is not configured yet.

dpkg: error processing package python3-gi (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of onboard-common:
 onboard-common depends on python3; however:
  Package python3 is not configured yet.

dpkg: error processing package onboard-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ibus:
 ibus depends on python3:any; however:
  Package python3 is not configured yet.
 ibus depends on python3-gi; however:
  Package python3-gi is not configured yet.

dpkg: error processing package ibus (--configure):
 dependency problems - leaving unconfigured
Setting up vim-runtime (2:8.2.3995-1ubuntu2.17) ...
dpkg: dependency problems prevent configuration of lsb-release:
 lsb-release depends on python3:any; however:
  Package python3 is not configured yet.

dpkg: error processing package lsb-release (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-ibus-1.0:
 python3-ibus-1.0 depends on python3:any; however:
  Package python3 is not configured yet.
 python3-ibus-1.0 depends on python3-gi (>= 3.8); however:
  Package python3-gi is not configured yet.

dpkg: error processing package python3-ibus-1.0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-gi-cairo:
 python3-gi-cairo depends on python3-gi (= 3.42.1-0ubuntu1); however:
  Package python3-gi is not configured yet.
 python3-gi-cairo depends on python3 (<< 3.11); however:
  Package python3 is not configured yet.
 python3-gi-cairo depends on python3 (>= 3.10~); however:
  Package python3 is not configured yet.

dpkg: error processing package python3-gi-cairo (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of steam-launcher:
 steam-launcher depends on python3 (>= 3.4); however:
  Package python3 is not configured yet.

dpkg: error processing package steam-launcher (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of zoom:
 zoom depends on ibus; however:
  Package ibus is not configured yet.

dpkg: error processing package zoom (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-dbus:
 python3-dbus depends on python3 (<< 3.11); however:
  Package python3 is not configured yet.
 python3-dbus depends on python3 (>= 3.10~); however:
  Package python3 is not configured yet.
 python3-dbus depends on python3:any; however:
  Package python3 is not configured yet.

dpkg: error processing package python3-dbus (--configure):
 dependency problems - leaving unconfigured
Setting up vim (2:8.2.3995-1ubuntu2.17) ...
update-alternatives: using /usr/bin/vim.basic to provide /usr/bin/vim (vim) in auto mode
update-alternatives: using /usr/bin/vim.basic to provide /usr/bin/vimdiff (vimdiff) in auto mode
update-alternatives: using /usr/bin/vim.basic to provide /usr/bin/rvim (rvim) in auto mode
update-alternatives: warning: /etc/alternatives/rview has been changed (manually or by a script); switching to manual updates only
update-alternatives: using /usr/bin/vim.basic to provide /usr/bin/rview (rview) in auto mode
update-alternatives: warning: /etc/alternatives/vi has been changed (manually or by a script); switching to manual updates only
update-alternatives: using /usr/bin/vim.basic to provide /usr/bin/vi (vi) in auto mode
update-alternatives: warning: /etc/alternatives/view has been changed (manually or by a script); switching to manual updates only
update-alternatives: using /usr/bin/vim.basic to provide /usr/bin/view (view) in auto mode
update-alternatives: warning: /etc/alternatives/ex has been changed (manually or by a script); switching to manual updates only
update-alternatives: using /usr/bin/vim.basic to provide /usr/bin/ex (ex) in auto mode
update-alternatives: using /usr/bin/vim.basic to provide /usr/bin/editor (editor) in auto mode
dpkg: dependency problems prevent configuration of python3-cairo:amd64:
 python3-cairo:amd64 depends on python3 (<< 3.11); however:
  Package python3 is not configured yet.
 python3-cairo:amd64 depends on python3 (>= 3.10~); however:
  Package python3 is not configured yet.
 python3-cairo:amd64 depends on python3:any; however:
  Package python3 is not configured yet.

dpkg: error processing package python3-cairo:amd64 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-apt:
 python3-apt depends on python3 (<< 3.11); however:
  Package python3 is not configured yet.
 python3-apt depends on python3 (>= 3.10~); however:
  Package python3 is not configured yet.
 python3-apt depends on python3:any; however:
  Package python3 is not configured yet.

dpkg: error processing package python3-apt (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of onboard:
 onboard depends on onboard-common (<< 1.4.1-5build5.1); however:
  Package onboard-common is not configured yet.
 onboard depends on onboard-common (>= 1.4.1-5build5); however:
  Package onboard-common is not configured yet.
 onboard depends on python3-cairo; however:
  Package python3-cairo:amd64 is not configured yet.
 onboard depends on python3-dbus; however:
  Package python3-dbus is not configured yet.
 onboard depends on python3-gi-cairo; however:
  Package python3-gi-cairo is not configured yet.
 onboard depends on python3 (<< 3.11); however:
  Package python3 is not configured yet.
 onboard depends on python3 (>= 3.10~); however:
  Package python3 is not configured yet.
 onboard depends on python3:any; however:
  Package python3 is not configured yet.

dpkg: error processing package onboard (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of onboard-data:
 onboard-data depends on onboard (<< 1.4.1-5build5.1); however:
  Package onboard is not configured yet.
 onboard-data depends on onboard (>= 1.4.1-5build5); however:
  Package onboard is not configured yet.

dpkg: error processing package onboard-data (--configure):
 dependency problems - leaving unconfigured
Processing triggers for hicolor-icon-theme (0.17-2) ...
Processing triggers for libc-bin (2.35-0ubuntu3.8) ...
Processing triggers for desktop-file-utils (0.26-1ubuntu3) ...
Errors were encountered while processing:
 python3
 python3-gi
 onboard-common
 ibus
 lsb-release
 python3-ibus-1.0
 python3-gi-cairo
 steam-launcher
 zoom
 python3-dbus
 python3-cairo:amd64
 python3-apt
 onboard
 onboard-data
E: Sub-process /usr/bin/dpkg returned an error code (1)
(base) kamil@kamil-Predator-G3-571:~/local-apt-repo$ sudo apt-mark hold vim
vim set on hold.
(base) kamil@kamil-Predator-G3-571:~/local-apt-repo$ apt-mark showhold
vim
(base) kamil@kamil-Predator-G3-571:~/local-apt-repo$ apt-mark showhold
vim
(base) kamil@kamil-Predator-G3-571:~/local-apt-repo$ apt-mark showhold
vim
(base) kamil@kamil-Predator-G3-571:~/local-apt-repo$ sudo apt-mark unhold 
E: No packages found
di(base) kamil@kamil-Predator-G3-571:~/local-apt-repo$ sudo apt-mark unhold vim
Canceled hold on vim.
