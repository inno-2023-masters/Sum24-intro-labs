## Task 1

1. Create a Local Repository

![](1.png)

2. Generate the Package Index

![](2.png)

3. Add the Local Repository to Your Sources List

![](3.png)

4. Verify the Contents of the Packages.gz File

![](4.png)

5. Install a Package from the Local Repository

![](5.png)

## Task 2

1. Choose a Package to Simulate

![](6.png)

Here, I've chosen ```net-tools``` package, as well as for next task

2. Simulate the Installation

![](7.png)

3. Analyze the Output

![](8.png)

As we can see, as the dependencies this package has libc6 and libselinux1,
and only the package itself would be installed



## Task 3

1. Install a Package, ```sudo apt install your-package-name```

2. Hold the Package, ```sudo apt-mark hold your-package-name```

3. Verify the Hold Status, ```apt-mark showhold```

4. Unhold the Package, ```sudo apt-mark unhold your-package-name```

![](9.png)