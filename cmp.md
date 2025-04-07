The ```cmp``` command in Linux is used to compare two files byte by byte. It reports the first difference it finds between the two files or reports that the files are identical if no differences are found.

Syntax:

```
cmp [options] file1 file2
```

Common options:

* ```-l```: Outputs the byte number and differing bytes in octal for all differing bytes.
* ```-s```: Silent mode, outputs nothing, and only returns the exit code (useful for scripting).
* ```-i <num>```: Skips the first <num> bytes of both files before comparing.
* ```-n <num>```: Compares only the first <num> bytes of the files.
* ```-b```: Prints the differing bytes in hexadecimal and their ASCII characters.

Exit codes:

* 0: The files are identical.
* 1: The files are different.
* 2: An error occurred (e.g., one of the files does not exist).

Examples:

1. Basic comparison:

```
cmp file1.txt file2.txt
```

If the files are different, it will output something like:

```
file1.txt file2.txt differ: byte 4, line 1
```

This indicates the first difference occurred at byte 4, line 1.

1. Silent comparison:

```
cmp -s file1.txt file2.txt
```

This does not produce any output but uses the exit status to indicate whether the files are the same or different. You can check the exit code with $?.

1. Show all differences in bytes:

cmp -l file1.txt file2.txt

It will list the byte number and the differing byte values in octal.

1. Compare first 100 bytes only:

```
cmp -n 100 file1.txt file2.txt
```

This compares only the first 100 bytes of both files.

1. Skip first 10 bytes and compare:

cmp -i 10 file1.txt file2.txt

This skips the first 10 bytes in both files and compares the rest.

Use cases:

* **File integrity checks**: You can use cmp to ensure two binary or text files are identical.
* **Scripting**: With the -s option, cmp is useful in shell scripts to check for file differences without producing any output.

Example of exit code check in a script:

```
cmp -s file1.txt file2.txt
if [ $? -eq 0 ]; then
  echo "Files are identical"
else
  echo "Files are different"
fi
```
