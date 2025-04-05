* Objective: Learn how to monitor system performance, resources, and storage.

Topics to Cover:

* CPU usage:
    * ```top``` real-time CPU usage by processes
    *  ```htop```,  offering a more interactive and user-friendly interface
    * Checking CPU load and usage
* Memory (RAM) usage:
    * ```free``` - check the ram. Call ```free -h``` to have the information in GB
    *  ```vmstat``` command provides more detailed information about memory, processes, and CPU activity.
        * ```vmstat 1 5``` Prints statistics every 1 second, 5 times.
    *  ```top```
* Storage:
    * df (disk usage by filesystem), du (disk usage by directory/file)
        * ```df -h``` Human-readable format (e.g., MB, GB).
    * Checking mounted devices 
        * ```lsblk```, 
        * ```mount``` check the mounted devices
            * ```mount | column -t```
    * Disk space analysis with ncdu
* System-wide statistics:
    * ```uptime``` check how long the system is running
    * ```dmesg```, 
    * ```iostat```

Practice:

* Monitor your system in real-time using ```top``` or ```htop```.
* Check disk usage using df -h and analyze memory status with ```free -h```.
* Generate CPU and memory usage reports using ```mpstat``` and ```vmstat```.

