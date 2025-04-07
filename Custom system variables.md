Custom system variables

You can create your own variables in Linux using shell commands or by adding them to specific configuration files. These variables will be stored either in the current shell session (if you define them temporarily) or in configuration files (for persistent use across sessions).
Here’s how you can create your own variables and where they are stored:

1. **Creating a Temporary Variable in the Current Shell**

**If you create a variable directly in the terminal or in a script, it will be stored in the current shell session.**

**Example:**

```
MY_VAR="Hello, World!"
echo $MY_VAR  # Output: Hello, World!
```

* This creates a shell variable MY_VAR with the value "Hello, World!".
* It is available only in the current session or script and will disappear when the session ends or the script finishes.

To make the variable **global** (so it can be accessed by child processes), you need to export it:

```
export MY_VAR="Hello, World!"
```

Now ```MY_VAR``` is available to any child processes started by the current shell.

2.** Making Variables Persistent (Stored in Configuration Files)

If you want your variable to be available every time you log in or open a terminal session, you need to add it to the appropriate shell configuration files.

For a Single User (User-Specific Variables)

You can add the variable to one of the following files in your home directory:**

* ```~/.bashrc``` (for non-login shells)
* ```~/.bash_profile``` or ```~/.profile``` (for login shells)

Example:

Add the following line to ```~/.bashrc``` or ```~/.bash_profile```:

```
export MY_VAR="Persistent Value"
```

After adding it, reload the file to apply the changes:

```
source ~/.bashrc  # or ~/.bash_profile
```

Now, MY_VAR will be available in every new shell session for that user.

For All Users (System-Wide Variables)

To make the variable available globally to all users, you can define it in system-wide configuration files such as:

* ```/etc/environment```: Used for defining global environment variables.
* ```/etc/profile```: For login shells (all users).
* ```/etc/bash.bashrc```: For non-login shells (all users).

Example:

Edit /etc/environment and add:

```
MY_VAR="Global Value"
```

After a restart or relog, the variable will be available to all users.

3. Scope and Storage of Variables

* Local Variables: Defined in the current shell or script and not exported. These variables are stored in the shell's memory and will disappear when the shell session ends.
    * Example: ```MY_VAR="Temporary"```
* Global Variables (Environment Variables): Variables that are exported and available to all child processes. They are stored in the process’s environment (part of the process memory). These variables exist as long as the session or process exists.
    * Example: ```export MY_VAR="Global"```
* Persistent Variables: Defined in configuration files like ~/.bashrc or /etc/environment and are stored in these files. They are loaded into the shell or process environment every time a new session starts.

How to View the Variables You Created

You can check your variables in several ways:

* For local variables: Simply echo the variable:

```echo $MY_VAR```

* For environment variables: Use env or printenv to see all environment variables:

```env | grep MY_VAR```

* To check all variables (both local and environment), use set:

```set | grep MY_VAR```

Summary:

* **Temporary variables** are created by defining them in the current shell and are lost when the shell ends.
* **Persistent variables** can be stored in configuration files like ~/.bashrc or /etc/environment to be available across sessions.
* **Global variables** are created using export and are available to child processes of the shell.
* You can store variables in memory (for temporary use) or in shell configuration files (for persistent use).

