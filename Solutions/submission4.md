# Software Distribution

## Task 1: Configure and Use a Local Package Repository

**Objective**: Set up a local package repository and use it to install packages.

1. **Create a Local Repository**:
   - Create a directory to hold your repository and place some `.deb` files in it.

     ```sh
     mkdir -p ~/local-apt-repo
     cp /path/to/package.deb ~/local-apt-repo/
     ```

     This step is pretty obvious, nothing to document.

2. **Generate the Package Index**:
   - Use `dpkg-scanpackages` to create a `Packages` file. Compress this file into a `Packages.gz` archive.

     ```sh
     dpkg-scanpackages ~/local-apt-repo /dev/null | gzip -9c > ~/local-apt-repo/Packages.gz
     ```

     By this command we scan all the packages in our folder and zip them into one archive (Packages.gz)

3. **Add the Local Repository to Your Sources List**:
   - Add the repository to your `sources.list`.

     ```sh
     echo "deb [trusted=yes] file:/home/yourusername/local-apt-repo ./" | sudo tee /etc/apt/sources.list.d/local-apt-repo.list
     sudo apt update
     ```
     By the tee command we create new source of program sources for apt. Then we add our local source as trusted into apt. Using apt update we make apt update its' list of sources for the packages.

4. **Verify the Contents of the Packages.gz File:**:
   - Check that the Packages.gz file contains the correct paths and metadata for your .deb files, **it must be relative path like `./your_package.deb`**. Also you can see the package name there. Then check the repository of your package, make sure it's local one.

     ```sh
     zcat Packages.gz
     ```

     Output:
     ```
        Package: sdkmanager
        Version: 2.1.0-11698
        Architecture: amd64
        Maintainer: NVIDIA DevTools-SDKManager Team <sdkm-feedback@nvidia.com>
        Installed-Size: 376632
        Depends: libcanberra-gtk-module, locales, libxshmfence1, libnss3, libatk-bridge2.0-0, libdrm2, libgtk-3-0, libgbm1, libcanberra-gtk3-module, libx11-xcb1
        Filename: /home/stepan/local-apt-repo/sdkmanager_2.1.0-11698_amd64.deb
        Size: 88950632
        MD5sum: 2a8558059dabecca4225941f9a6ab112
        SHA1: b291dab5ccc2882f9221cabdd93b01293c186e41
        SHA256: 958d92eb8b7d0af9b213e14819c3d0ee8c0e09ceb8100b54e1281901e557c7a7
        Section: devel
        Priority: optional
        Homepage: https://developer.nvidia.com
        Description: NVIDIA SDK Manager
        The NVIDIA Software Development Kit (SDK) Manager is an all-in-one tool that bundles developer software and provides an end-to-end development environment setup solution for NVIDIA SDKs.
        ```
        Here we can see, that apt now sees our package and it correctly knows its' location on the disk.

        ```sh
        apt policy your-package-name
        ```

        ```
        sdkmanager:
        Installed: 2.1.0-11698
        Candidate: 2.1.0-11698
        Version table:
        *** 2.1.0-11698 100
                100 /var/lib/dpkg/status
            0.5.1-1 500
                500 http://ru.archive.ubuntu.com/ubuntu jammy/universe amd64 Packages
                500 http://ru.archive.ubuntu.com/ubuntu jammy/universe i386 Packages
        ```

5. **Install a Package from the Local Repository**:
   - Install a package using `apt` from your local repository.

     ```sh
     sudo apt install your-package-name
     ```

        The program was already install on the system, but we can still see, that installation process ended correctly:
     ```sh
        Reading package lists... Done
        Building dependency tree... Done
        Reading state information... Done
        sdkmanager is already the newest version (2.1.0-11698).
        The following packages were automatically installed and are no longer required:
        cpu-checker dh-elpa-helper gazebo-common gazebo-plugin-base ipxe-qemu ipxe-qemu-256k-compat-efi-roms libaio1 libcacard0 libdaxctl1 libfdt1 libgfapi0 libgfrpc0 libgfxdr0 libglusterfs0 libiscsi7
        libndctl6 libpmem1 libpmemobj1 librados2 librbd1 librhash0 libspice-server1 liburing2 libusbredirparser1 libvirglrenderer1 libwireshark17 libwiretap14 libwsutil15 linux-headers-6.5.0-18-generic
        linux-hwe-6.5-headers-6.5.0-18 linux-image-6.5.0-18-generic linux-modules-6.5.0-18-generic linux-modules-extra-6.5.0-18-generic linux-modules-nvidia-535-6.5.0-18-generic
        linux-objects-nvidia-535-6.5.0-18-generic linux-signatures-nvidia-6.5.0-18-generic msr-tools ovmf pass qemu-block-extra qemu-system-common qemu-system-data qemu-system-gui qemu-system-x86 qemu-utils
        qrencode seabios tree uidmap xclip
        Use 'sudo apt autoremove' to remove them.
        0 upgraded, 0 newly installed, 0 to remove and 80 not upgraded.
        ```

## Task 2: Simulate Package Installation and Identify Dependencies

**Objective**: Use `apt` to simulate package installation and identify dependencies without actually installing the packages.

1. **Choose a Package to Simulate**:
   - Select a package to simulate its installation.

     ```sh
     apt-cache showpkg your-package-name
     ```

     Output:
     ```sh
        Package: sdkmanager
        Versions: 
        2.1.0-11698 (/var/lib/dpkg/status)
        Description Language: 
                        File: /var/lib/dpkg/status
                        MD5: 049028167858a29a8f6c84633ed01aa7

        0.5.1-1 (/var/lib/apt/lists/ru.archive.ubuntu.com_ubuntu_dists_jammy_universe_binary-amd64_Packages) (/var/lib/apt/lists/ru.archive.ubuntu.com_ubuntu_dists_jammy_universe_binary-i386_Packages)
        Description Language: 
                        File: /var/lib/apt/lists/ru.archive.ubuntu.com_ubuntu_dists_jammy_universe_binary-amd64_Packages
                        MD5: f993bf7dd5056277c240fce64114e044
        Description Language: en
                        File: /var/lib/apt/lists/ru.archive.ubuntu.com_ubuntu_dists_jammy_universe_i18n_Translation-en
                        MD5: f993bf7dd5056277c240fce64114e044


        Reverse Depends: 
        Dependencies: 
        2.1.0-11698 - libcanberra-gtk-module (0 (null)) locales (0 (null)) libxshmfence1 (0 (null)) libnss3 (0 (null)) libatk-bridge2.0-0 (0 (null)) libdrm2 (0 (null)) libgtk-3-0 (0 (null)) libgbm1 (0 (null)) libcanberra-gtk3-module (0 (null)) libx11-xcb1 (0 (null)) 
        0.5.1-1 - python3-argcomplete (0 (null)) python3-requests (0 (null)) python3:any (0 (null)) 
        Provides: 
        2.1.0-11698 - 
        0.5.1-1 - 
        Reverse Provides:
     ```

     Here we can see, that package have 2 versions: one is local and other (quite old) is from archive.ubuntu.com. Our .deb package has multiple dependencies, all of them are necessary and for all of them NVidia decideded not to define minimal verison(if we had any we would see something like `libxshmfence1 (>= 1.0)`).  
     Also we can see, that Providers and Reverse Providers are clear. That means, that this package cannot be replaced by any other known and at the same time package itself cannot replace any other package fully.

2. **Simulate the Installation**:
   - Firstly we need to remove our package from system
    ```
    sudo apt remove sdkmanager
    ```

   - Use the `-s` flag to simulate the installation.

    ```sh
    sudo apt-get install -s your-package-name
    ```

    ```
    Reading package lists... Done
    Building dependency tree... Done
    Reading state information... Done
    The following packages were automatically installed and are no longer required:
        cpu-checker dh-elpa-helper gazebo-common gazebo-plugin-base ipxe-qemu ipxe-qemu-256k-compat-efi-roms libaio1 libcacard0 libdaxctl1 libfdt1 libgfapi0 libgfrpc0 libgfxdr0 libglusterfs0 libiscsi7
        libndctl6 libpmem1 libpmemobj1 librados2 librbd1 librhash0 libspice-server1 liburing2 libusbredirparser1 libvirglrenderer1 libwireshark17 libwiretap14 libwsutil15 linux-headers-6.5.0-18-generic
        linux-hwe-6.5-headers-6.5.0-18 linux-image-6.5.0-18-generic linux-modules-6.5.0-18-generic linux-modules-extra-6.5.0-18-generic linux-modules-nvidia-535-6.5.0-18-generic
        linux-objects-nvidia-535-6.5.0-18-generic linux-signatures-nvidia-6.5.0-18-generic msr-tools ovmf pass qemu-block-extra qemu-system-common qemu-system-data qemu-system-gui qemu-system-x86 qemu-utils
        qrencode seabios tree uidmap xclip
    Use 'sudo apt autoremove' to remove them.
    The following additional packages will be installed:
    python3-argcomplete
    The following NEW packages will be installed:
    python3-argcomplete sdkmanager
    0 upgraded, 2 newly installed, 0 to remove and 80 not upgraded.
    Inst python3-argcomplete (1.8.1-1.5 Ubuntu:22.04/jammy [all])
    Inst sdkmanager (0.5.1-1 Ubuntu:22.04/jammy [all])
    Conf python3-argcomplete (1.8.1-1.5 Ubuntu:22.04/jammy [all])
    Conf sdkmanager (0.5.1-1 Ubuntu:22.04/jammy [all])
    ```
    Here we can see, that apt will install one dependency, which is not currently installed in our system and then install our package itself.

3. **Analyze the Output**:
   - Identify the dependencies and the packages that would be installed.
   - Document the findings in the `submission4.md` file, including which dependencies are required and their versions.

## Task 3: Hold and Unhold Package Versions

**Objective**: Prevent a package from being upgraded and then allow it to be upgraded again.

1. **Install a Package**:
   - Install a package that is commonly updated.

     ```sh
     sudo apt install your-package-name
     ```

2. **Hold the Package**:
   - Use `apt-mark` to hold the package.

     ```sh
     sudo apt-mark hold code
     ```

    Output:
     ```
     code set on hold.
     ```

3. **Verify the Hold Status**:
   - Check the status of held packages.

     ```sh
     apt-mark showhold
     ```
    Output:
     ```
     code
     ```

4. **Unhold the Package**:   - Use `apt-mark` to unhold the package.

     ```sh
     sudo apt-mark unhold your-package-name
     ```

     After this step we can check using the 3rd step, that package is no longer on hold.

     I do not really understand what to document here. We just used an apt tool which allows us to stop some packages from updating. In robotics, for example, we use ROS, which is quite hard to install and very easy to break. Usually after we install it, we do not use apt anymore on an embedded devices. Now I know, that we can just write script to make all ROS packages and their dependencies be on hold and use apt as usual.