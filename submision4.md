# Lab 4 : Software Distribution

## Task 1: Configure and Use a Local Package Repository

1. **Creating a Local Repository**:
   - For my pakage i will use Google chrome. I downloaded the `.deb` file and copied it to the `local-apt-repo` directory. 
    ```sh
    suwilanji@SUWILANJI-PCV3:~$ ls
    chrome
    suwilanji@SUWILANJI-PCV3:~$ mkdir -p ~/local-apt-repo
    suwilanji@SUWILANJI-PCV3:~$ cp ~/chrome/google-chrome-stable_current_amd64.deb ~/local-apt-repo/
    suwilanji@SUWILANJI-PCV3:~$ ls
    chrome  local-apt-repo
    ```

2. **Generate the Package Index**:
   - Using `dpkg-scanpackages` creates a `Packages` file and `gzip -9c` compresss this file into a `Packages.gz` archive.

    ```sh
    suwilanji@SUWILANJI-PCV3:~$ dpkg-scanpackages ~/local-apt-repo /dev/null | gzip -9c > ~/local-apt-repo/Packages.gz
    dpkg-scanpackages: warning: Packages in archive but missing from override file:
    dpkg-scanpackages: warning:   google-chrome-stable
    dpkg-scanpackages: info: Wrote 1 entries to output Packages file.
    ```

3. **Add the Local Repository to Your Sources List**:
   - I used the following command to ass the repository to my `sources.list`.
    ```sh
    suwilanji@SUWILANJI-PCV3:~$ echo "deb [trusted=yes] file:/home/suwilanji/local-apt-repo ./" | sudo tee /etc/apt/sources.list.d/local-apt-repo list
    deb [trusted=yes] file:/home/suwilanji/local-apt-repo ./
    ```
    - Before uupdating the reposory I changed the filename genrated in the Pakages.gz to in the following format 
    ```sh
    Filename: ./google-chrome-stable_current_amd64.deb
    ```
    - And i updaded the apt repository by running 
    ```sh
    suwilanji@SUWILANJI-PCV3:~$ sudo apt update
    Get:1 file:/home/suwilanji/local-apt-repo ./ InRelease
    Ign:1 file:/home/suwilanji/local-apt-repo ./ InRelease
    Get:2 file:/home/suwilanji/local-apt-repo ./ Release
    Ign:2 file:/home/suwilanji/local-apt-repo ./ Release
    Get:3 file:/home/suwilanji/local-apt-repo ./ Packages
    Ign:3 file:/home/suwilanji/local-apt-repo ./ Packages
    Get:4 file:/home/suwilanji/local-apt-repo ./ Translation-en
    Ign:4 file:/home/suwilanji/local-apt-repo ./ Translation-en
    Get:3 file:/home/suwilanji/local-apt-repo ./ Packages
    Ign:3 file:/home/suwilanji/local-apt-repo ./ Packages
    Get:4 file:/home/suwilanji/local-apt-repo ./ Translation-en
    Ign:4 file:/home/suwilanji/local-apt-repo ./ Translation-en
    Get:3 file:/home/suwilanji/local-apt-repo ./ Packages
    Ign:3 file:/home/suwilanji/local-apt-repo ./ Packages
    Get:4 file:/home/suwilanji/local-apt-repo ./ Translation-en
    Ign:4 file:/home/suwilanji/local-apt-repo ./ Translation-en
    Get:3 file:/home/suwilanji/local-apt-repo ./ Packages [772 B]
    Hit:3 file:/home/suwilanji/local-apt-repo ./ Packages
    Get:4 file:/home/suwilanji/local-apt-repo ./ Translation-en
    Err:4 file:/home/suwilanji/local-apt-repo ./ Translation-en
    File not found - /home/suwilanji/local-apt-repo/./en.gz (2: No such file or directory)
    Get:4 file:/home/suwilanji/local-apt-repo ./ Translation-en
    Err:4 file:/home/suwilanji/local-apt-repo ./ Translation-en
    File not found - /home/suwilanji/local-apt-repo/./en.lz4 (2: No such file or directory)
    Get:4 file:/home/suwilanji/local-apt-repo ./ Translation-en
    Err:4 file:/home/suwilanji/local-apt-repo ./ Translation-en
    File not found - /home/suwilanji/local-apt-repo/./en.zst (2: No such file or directory)
    Get:4 file:/home/suwilanji/local-apt-repo ./ Translation-en
    Ign:4 file:/home/suwilanji/local-apt-repo ./ Translation-en
    Err:3 file:/home/suwilanji/local-apt-repo ./ Packages
    Could not open file /home/suwilanji/local-apt-repo/./Packages - open (13: Permission denied)
    Get:3 file:/home/suwilanji/local-apt-repo ./ Packages
    Err:3 file:/home/suwilanji/local-apt-repo ./ Packages
    Method gave a blank filename
    Get:3 file:/home/suwilanji/local-apt-repo ./ Packages
    Err:3 file:/home/suwilanji/local-apt-repo ./ Packages
    Method gave a blank filename
    Get:3 file:/home/suwilanji/local-apt-repo ./ Packages [1353 B]
    Get:5 http://security.ubuntu.com/ubuntu jammy-security InRelease [129 kB]
    Get:6 https://dl.google.com/linux/chrome/deb stable InRelease [1825 B]
    Get:7 https://dl.google.com/linux/chrome/deb stable/main amd64 Packages [1087 B]
    Reading package lists... Done
    Building dependency tree... Done
    Reading state information... Done
    2 packages can be upgraded. Run 'apt list --upgradable' to see them.
    ```

4. **Verify the Contents of the Packages.gz File:**:
   - To verify the contents of my .deb file I used the following command. 

    ```sh
    suwilanji@SUWILANJI-PCV3:~/local-apt-repo$ zcat Packages.gz
    Package: google-chrome-stable
    Version: 126.0.6478.126-1
    Architecture: amd64
    Maintainer: Chrome Linux Team <chromium-dev@chromium.org>
    Installed-Size: 340311
    Pre-Depends: dpkg (>= 1.14.0)
    Depends: ca-certificates, fonts-liberation, libasound2 (>= 1.0.17), libatk-bridge2.0-0 (>= 2.5.3), libatk1.0-0 (>= 2.2.0), libatspi2.0-0 (>= 2.9.90), libc6 (>= 2.17), libcairo2 (>= 1.6.0), libcups2 (>= 1.6.0), libcurl3-gnutls | libcurl3-nss | libcurl4 | libcurl3, libdbus-1-3 (>= 1.9.14), libdrm2 (>= 2.4.75), libexpat1 (>= 2.1~beta3), libgbm1 (>= 17.1.0~rc2), libglib2.0-0 (>= 2.39.4), libgtk-3-0 (>= 3.9.10) | libgtk-4-1, libnspr4 (>= 2:4.9-2~), libnss3 (>= 2:3.35), libpango-1.0-0 (>= 1.14.0), libu2f-udev, libvulkan1, libx11-6 (>= 2:1.4.99.1), libxcb1 (>= 1.9.2), libxcomposite1 (>= 1:0.4.4-1), libxdamage1 (>= 1:1.1), libxext6, libxfixes3, libxkbcommon0 (>= 0.5.0), libxrandr2, wget, xdg-utils (>= 1.0.2)
    Provides: www-browser
    Filename: ./google-chrome-stable_current_amd64.deb
    Size: 108773084
    Installed: (none)
    Candidate: 126.0.6478.126-1
    Version table:
        126.0.6478.126-1 500
            500 https://dl.google.com/linux/chrome/deb stable/main amd64 Packages
            500 file:/home/suwilanji/local-apt-repo ./ Packages
            100 /var/lib/dpkg/status
    ```
    - Since I already had one chrome pakage from google chrome, i removed it first before installing the pakage from my local-apt-repo
    ```sh
    suwilanji@SUWILANJI-PCV3:~/local-apt-repo$ sudo rm /etc/apt/sources.list.d/
    google-chrome.list   local-apt-repo.list
    suwilanji@SUWILANJI-PCV3:~/local-apt-repo$ sudo rm /etc/apt/sources.list.d/google-chrome.list
    ```
    - My chrome pakage apt policy
    ```sh
    suwilanji@SUWILANJI-PCV3:~/local-apt-repo$ apt policy google-chrome-stable
    google-chrome-stable:
    Installed: (none)
    Candidate: 126.0.6478.126-1
    Version table:
        126.0.6478.126-1 500
            500 file:/home/suwilanji/local-apt-repo ./ Packages
            100 /var/lib/dpkg/status
    ```

5. **Install a Package from the Local Repository**:
   - Installing my pakage from my local repository gives the following result

    ```sh
    suwilanji@SUWILANJI-PCV3:~/local-apt-repo$ sudo apt install google-chrome-stable
    Reading package lists... Done
    Building dependency tree... Done
    Reading state information... Done
    The following NEW packages will be installed:
    google-chrome-stable
    0 upgraded, 1 newly installed, 0 to remove and 2 not upgraded.
    Need to get 0 B/109 MB of archives.
    After this operation, 348 MB of additional disk space will be used.
    Get:1 file:/home/suwilanji/local-apt-repo ./ google-chrome-stable 126.0.6478.126-1 [109 MB]
    Selecting previously unselected package google-chrome-stable.
    (Reading database ... 46342 files and directories currently installed.)
    Preparing to unpack .../google-chrome-stable_current_amd64.deb ...
    Unpacking google-chrome-stable (126.0.6478.126-1) ...
    Setting up google-chrome-stable (126.0.6478.126-1) ...
    update-alternatives: using /usr/bin/google-chrome-stable to provide /usr/bin/x-www-browser (x-www-browser) in auto mode
    update-alternatives: using /usr/bin/google-chrome-stable to provide /usr/bin/gnome-www-browser (gnome-www-browser) in auto mode
    update-alternatives: using /usr/bin/google-chrome-stable to provide /usr/bin/google-chrome (google-chrome) in auto mode
    Processing triggers for man-db (2.10.2-1) ...
    suwilanji@SUWILANJI-PCV3:~/local-apt-repo$ google-chrome-stable --version
    Google Chrome 126.0.6478.126
    ```
    ## Task 2: Simulate Package Installation and Identify Dependencies
