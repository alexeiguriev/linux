**6 Advanced File and Process Management (Week 6)**

* **Objective**: Dive deeper into managing files, permissions, and processes.

**Topics to Cover**:

* File permissions and ownership:
    * Modify permissions using ```chmod```
        * ```chmod +x script.sh``` make the file executable
        * ```chmod 644 file.txt``` - owner read and write permissions, and others only read
        * ```chmod 777 script.sh``` make all read, write and executable
        * ```chmod -w file.txt``` Grant execute permissions to the owner and group
    * chown
        * ```sudo chown user1 file.txt``` change the user
        * ```sudo chown user1:group1 file.txt``` change both user and owner
        * ``sudo chown :group1 file.txt``` change the ownership of a file
    * Using ```setfacl``` for access control lists (ACLs)
* Process management:
    * Viewing processes: ```ps```, ```top```, ```htop```
    * Controlling processes: ```kill```, ```pkill```, ```jobs```, ```bg```, ```fg```, ```nohup```
    * Scheduling tasks: ```cron```, ```at```, ```systemd``` timers

**Practice:**

* Change file ownership and permissions and practice using ACLs with ```setfacl```.
* Monitor and control processes using ```ps``` and ```kill```.

