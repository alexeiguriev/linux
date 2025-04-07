Custom commands

Creating a custom persistent command in Linux allows you to define a command (like a script or alias) that you can use across multiple sessions. This involves either writing a shell script or defining an alias and storing it in a configuration file so that it persists after reboots or new terminal sessions.
Here’s how you can create a custom persistent command:

1. Create a Custom Command as a Script

You can create a script file and place it in a directory that is included in your PATH (so you can call it like a regular command). The script file will act as your custom command.

Steps:

1. Create a Script File:

    * Create a new file that will represent your command.
    * For example, let’s create a custom command called mycmd:

```
nano ~/mycmd
```

1. Write Your Command Logic: Inside this file, write whatever you want the command to do. For example:

```
#!/bin/bash
echo "This is my custom command!"
```

1. Make the Script Executable: Make the script file executable using chmod:

```
chmod +x ~/mycmd
```

1. Move the Script to a Directory in Your PATH: To make the command accessible globally, move the script to a directory that is included in your $PATH environment variable (e.g., /usr/local/bin or /usr/bin).

```
sudo mv ~/mycmd /usr/local/bin/
```

1. Run Your Custom Command: Now, you can run the command just by typing its name:

```
mycmd
```

2. Create a Custom Command as an Alias

You can also create a custom command as an alias, which is a shorthand for a longer command. To make it persistent, you need to add the alias to your shell configuration file.

Steps:

1. Define an Alias: You can define an alias in your shell. For example:

```
alias mycmd="echo 'This is my custom command!'"
```

1. Make the Alias Persistent: To make this alias persistent (so it is available every time you open a terminal), you need to add it to your shell’s configuration file:

    * If you use the bash shell, add it to ~/.bashrc:

```
nano ~/.bashrc
```

    * Add the alias definition at the bottom of the file:

```
alias mycmd="echo 'This is my custom command!'"
```

    * Save and close the file.
    * If you use zsh, add it to ~/.zshrc.

1. Reload the Configuration File: After editing the file, reload it to apply the changes:

```
source ~/.bashrc  # or ~/.zshrc
```

1. Run Your Custom Command: Now, the alias mycmd will be available in every terminal session:

```
mycmd
```

3. Adding Functions as Custom Commands

You can also define custom commands as functions in your shell configuration file. This can be useful for more complex commands that require logic.

Example:

1. Open your ```~/.bashrc``` (or ```~/.zshrc```):

```
nano ~/.bashrc
```

1. Define a function:

```
mycmd() {
    echo "This is my custom function-based command!"
    # You can add more complex logic here
}
```

1. Save and close the file, then reload the shell:

```
source ~/.bashrc
```

1. You can now use mycmd as a custom command:
2. 
```
mycmd
```

4. Verify Custom Command Location

To check that your custom command is properly set up and available in the system's $PATH, you can use:

```
which mycmd
```

This will return the path to your custom script if it is accessible.

Summary:

* **Shell Script**: Create a shell script and place it in a directory included in $PATH, such as /usr/local/bin.
* **Alias**: Define a custom alias in your shell’s configuration file (~/.bashrc or ~/.zshrc) to create a shorthand command.
* **Function**: Add a function in your configuration file to create more complex commands with logic.
* Don’t forget to reload the shell configuration file after making changes using source ~/.bashrc (or the relevant file).

By following these methods, you can create persistent custom commands that will be available every time you start a new terminal session.
