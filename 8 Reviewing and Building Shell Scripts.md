**8 Reviewing and Building Shell Scripts**

**Objective: By the end of this week, you will be able to create shell scripts to automate common system tasks. You will also learn how to structure, debug, and optimize shell scripts.**

**Topics to Cover:**

1. **Basics of Shell Scripting:**

    * Understand what a shell script is and why it's useful for automation.
    * Basic structure of a shell script: shebang (```#!/bin/bash```) and comments.
    * **Variables and Control Structures:**
        * Declare and use variables in a script.
        * Use control structures like ```if-else```, ```for```, ```while```, and ```case```.
        * Example:

```
#!/bin/bash
name="Eli"
if [ "$name" = "Eli" ]; then
echo "Hello, $name!"fi
```


1. **User Input and Arguments:**

    * **Using read for user input:**
        * Example:

```
read -p "Enter your name: " nameecho "Hello, $name!"
```

    * **Positional Parameters ($1, $2, etc.)**: Handle arguments passed to the script from the command line.
        * Example:

```
#!/bin/bash
echo "First argument: $1"echo "Second argument: $2"
```

1. **File Manipulation in Scripts:**

    * **Working with Files**: Create, read, append, and manipulate files within a script.
    * Use redirection (```>```, ```>>```) and pipes (```|```).
        * Example: Write output to a file:

```
echo "This is a test" > testfile.txt
```

1. Conditionals and Loops:

    * Learn to use loops (for, while) to perform repeated tasks.
        * Example:

```
for i in {1..5}; do
echo "Iteration $i"done
```


    * Understand conditionals and exit statuses (```if```, ```else```, ```elif```).

1. **Script Debugging:**

    * Enable script debugging with the ```-x``` option (```bash -x script.sh```).
    * Learn how to debug scripts by adding ```set -x``` to your script to trace its execution.
    * Use echo statements to check the values of variables at different stages.

1. Handling Errors and Exit Codes:

    * Understand how exit statuses work and how to check them with ```$?```.
    * Handle errors and provide user feedback using ```exit``` with different codes.
    * Example:

```
if [ -d "/path/to/dir" ]; then
echo "Directory exists"
else
echo "Directory does not exist"
exit 1fi
```

1. **Automating Tasks:**

    * Use ```cron``` jobs to automate your scripts.
    * Example: Schedule a backup script to run daily.
        * Add the script to the crontab with ```crontab -e```:

```
0 2 * * * /path/to/backup.sh
```

1. **Using Functions in Shell Scripts:**

    * Create reusable blocks of code in shell scripts using functions.
    * Example:

```
my_function() {
  echo "This is a function"
}
my_function
```

1. **Real-World Scripting Projects:**

    * Build a script to automate a backup process (e.g., backup files to a directory or remote location).
    * Create a monitoring script to check system resource usage (CPU, memory) and log it to a file or send alerts.

**Practice Exercises**:

* Write a script to find and delete files older than a certain number of days.
* Create a script that takes a list of filenames as arguments and compresses them into a .tar.gz archive.
* Automate network-related tasks like checking if a service is running and restarting it if necessary.


**Resources for Shell Scripting**:

* **Books**:
    * "The Linux Command Line: A Complete Introduction" by William Shotts.
    * "Classic Shell Scripting" by Arnold Robbins.
* **Online Resources**:
    * Shell scripting tutorial
    * Advanced Bash-Scripting Guide

**Final Project**:

* Write a comprehensive shell script that automates a multi-step process, such as:
    * Checking system status (CPU, memory, storage).
    * Backing up logs or important files.
    * Sending a notification or report when the process is completed.
    * 1. Understanding the Linux CLI and Basics (Week 1)
    * Objective: Familiarize yourself with essential Linux commands and navigating the system.
    * Topics to Cover:
    * Basic command-line usage: ls, cd, pwd, man, echo, clear
    * Understanding the file system structure: /, /home, /etc, /usr, /var, /tmp
    * Navigating directories and files
    * File and directory permissions: chmod, chown
    * Using the manual (man) and help (--help) commands to learn about command usage
    * Practice:
    * Navigate through directories, create folders and files, and modify permissions.
    * Use man pages to explore options for basic commands.
    * Objective: Familiarize yourself with essential Linux commands and navigating the system.
    * Topics to Cover:
    * Basic command-line usage: ls, cd, pwd, man, echo, clear
    * Understanding the file system structure: /, /home, /etc, /usr, /var, /tmp
    * Navigating directories and files
    * File and directory permissions: chmod, chown
    * Using the manual (man) and help (--help) commands to learn about command usage
    * Practice:
    * Navigate through directories, create folders and files, and modify permissions.
    * Use man pages to explore options for basic commands.

