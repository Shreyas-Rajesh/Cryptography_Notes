When you launch a terminal, it will execute a command line "shell" , the "prompt" is prompting you to enter a command.
Usually the prompt is in the form of ==username@hostname:~\$== (no \ ), where host name is the environment or the machine the shell is running. The "$" denotes non-root user and "#" denotes root user (admin).

##### *Difference between shell  terminal  console*
A shell is a program that puts up a prompt and waits for you to type commands. It executes them and then prints another prompt. So, like "CMD" in Windows, or "Bash" in Unix. It can run in a terminal or on the console. Bash is the shell, or command language interpreter, for the GNU operating system.

A **terminal** refers to a wrapper program which runs a shell. Decades ago, this was a physical device consisting of little more than a monitor and keyboard. As unix/linux systems added better multiprocessing and windowing systems, this terminal concept was abstracted into software.

The **console** is a special sort of _terminal_. Historically, the console was a single keyboard and monitor plugged into a dedicated serial console port on a computer used for direct communication at a low level with the operating system.

> [!tip] Shebang (https://bash.cyberciti.biz/guide/Shebang)
> You will always see #!/bin/bash or #!/usr/bin/env bash as the first line when writing or reading bash scripts. The **#!** syntax is used in scripts to indicate an interpreter for execution under UNIX / Linux operating systems.
> !/usr/bin/python3 is for python
> If you do not specify an interpreter line, the default is usually the /bin/sh.


1. whoami : prints the username
2. echo "string" : is a simple command that "echoes" all of its arguments back out onto the terminal
3. history : to see the history of all the commands used 
	- -c flag is used to clear
	- -d offset deletes the history at the offset value.

>[!tip] Use "!!" as a history expanding command, ie it will copy paste the last executed command (even if it resulted in an error) on where it is written

4. cd : to change directory
	- - takes you to the previous directory
	- .. goes up one level
	- ~ takes you to the home directory (same if you give no arg to cd)

5. cat :  to concatenate
	- -n show the line numbers
	- -b show line number for non-empty lines
	- cat file1 file 2 > merge.txt (both files together)
	- cat >> file will let user input and store in file

6. grep SEARCH_STRING /path/to/file : searches text for patterns (strings or regex) and prints matching lines.
	- -i makes the search text case insensitive
	- -r can be used to find recursively in a directory (so instead of filename give dir name)
	- -n shows the number line too
	- -c count of matching lines
	- -v shows lines that do not match

7. diff : Compare files line by line
	After the output shows NcM, where N is the line number of the change in file1 nd M is the line number of the change in file2. < is first file and > is second file
	- -q to show nothing if no difference
	- -y side by side comaprison
	- -r dir1 dir 2 compares 2 directories recursively

8. ls : To list all the files and folders in the directory
	- -l  shows the long format 
	- -a all files
	- ![[PWN_LS_types.png]]
	- For pipe refer down

>[!info] Symbolic links are files or dir that reference to another files or dir
>ln -s dir_to_link_to dir_that_will_point_to_link
>this does relative linking if relative path is given, so the other file should be present in the same dir and changing the position of either file will cause an error

9. touch : to create new file
	no file extension mean it creates a regular file(t’s basically a container for data—like text, code, images, or binaries.)
	- -a access time only

10. rm : to remove files and remove directories
	- -i asks if you want to delete
	- -f force ignores all warning
	- -r remove directories recursively (if the dir has files then this is used)
	- -v show what is being removed

11. rmdir : to delete empty directories
	- -p dir/subdir removes the parent folder if the sibdir becomes empty

12. mv : to move files from place to place
	This is used to rename files and also if there are multiple files, all the files will be moved to the last given dir

> [!tip] To create hidden files give "." before the filename

13. mkdir : to make directories
	- -p creates the parent directories if they do not exist. Used when a file needs to be created within a dir and the parent dir doesnt exist.
	- -m NNNN hex code for permission

14. find : searches the directory recursively for files, directories and other criteria
	If the directory isnt given it will find in the cwd
	- -name
	- -type (f for files and d for dir)
	- -size (can specify +/- for greater or less than the size) (b bytesblock 512, c byte, k KB, M MB, G GB )
	- -user
	- -group

> [!info] "HELP" vs "MAN"
>Help is only for shell-built in functions only
>Man is for shell-built in or external functions (more detailed) 

When the shell sees a glob, it will perform _pathname expansion_ and replace the glob with matching filenames when it invokes the program.

15.  * ? []
	- asterisk is matches **zero or more characters** in a filename.
	- question mark matches exactly one
	- \[abc] matches any characters inside
	- \[a-z] matches characters from a to z
	- \[^abc] matches everything except abc

16. > >> 2> 2>> 2>&1  <
	- Sends **stdout** to a file (overwrites file). ">"
	- Sends **stdout** to a file (appends, doesn’t overwrite). ">>"
	- Sends **stderr** (errors) to a file. "2>"
	- combine stdout and stderr into one file. 2>&1
	- Reads input for a command from a file instead of the keyboard.

>[!info] There are 3 types of standard streams
>std0 is standard input
>std1 is standard output
>std2 is errors

17. | 
	Standard output from the command to the left of the pipe will be connected to (_piped into_) the standard input of the command to the right of the pipe. It cannot pipe errors.

18. tee : read from stdin and write to stdout and file simultaneously (T-splitter)
	- `command | tee file` → write output to file and display on terminal.
	- `command | tee -a file` → append to file instead of overwriting.

>[!tip] <(commad) can be used to give the executed command as input to another command

17. >(command)
	To read as input
	
	>[!example] echo HACK | tee >(rev)
	>in this echo HACK then the value is piped to tee, which std1 as output and then a file gets created, something like `/dev/fd/63` . This file is used by the rev and then it is outputted to rev

18. mkfifo : create your own _persistent_ named pipes
	Are called **FIFOs**.
	1. **No disk storage:** FIFOs pass data directly between processes in memory - nothing is saved to disk
	2.  **Ephemeral data:** Once data is read from a FIFO, it's gone (unlike files where data persists)
	>[!example] 
hacker@dojo:~$ mkfifo myfifo
hacker@dojo:~$ echo pwn > myfifo
To service `echo pwn > myfifo`, bash will open the `myfifo` file in write mode. However, this operation will hang until something _also_ opens the file in read mode (thus completing the pipe).

>[!info] You can assign variables in a shell by using VAR=Number, there should be no spaces
>

19. $ : variable expansion
	This can be used before a variable that is used to expand the value of the variable (ie access the value rather than the variable name).
	Surprisingly, the source of many potential vulnerabilities
	If the value has multiple char, use quotes

20. $ : command substitution
	FLAG=$(cat /flag) here the file "flag" is catted and its value is substituted as the value of the flag.

>[!warning] By default, variables that you set in a shell session are local to that shell process. That is, other commands you run won't inherit them.
>![[PWN_VariableExpansion.png]]
>In the output above, the `$` prompt is the prompt of `sh`, a minimal shell implementation that is invoked as a _child_ of the main shell process.
>If you need this value to be accessed you *export* the variable, `export VAR` 
>When you export your variables, they are passed into the _environment variables_ of child processes

21. `env` : Show or run with modified environment variables
	It can be used to run a command with a temporary environment.
	- Without any argument it will display all the current environment variables (ie exported)
	- `env VAR=value command` → run command with VAR temporarily set.
		 env PATH=/tmp myscript.sh here path will be temporarily set

22. read : Read a line of input from stdin
	- read VAR to read variable
	- read -p "Prompt" VAR
	- reas -s VAR to hide the input (silent)
	- read -n N VAR to read N bytes 
		- Note if you press enter or enter a newline before N character, newline will also be considered as a character
	-read -t T VAR to timeout input
>[!info] Instead of using cat you can use redirecting stdin to give value to a variable (uselessness of cat).

23. tr : to translate characters or delete
	- `tr 'a-z' 'A-Z'` → convert lowercase to uppercase.
	- `tr 'A-Z' 'a-z'` → convert uppercase to lowercase.
	- `tr -d 'x'` → delete all occurrences of x.\
	- you can use "\n" for new line

24.  head tail : to show the first few lines and last few lines respectively
	- By default both shows 10 chars
	- -n N to specify N number of chars for HEAD and TAIL

25. cut : Extract sections of each line from a file or stdin, useful for working with columns/fields
	- -d " " is used to specify the delimiter.  ie it will split into columns based on the delimiter.
	- -f N specify the column/field number.
	- default delimiter is TAB

26. sort : sort lines alphabetically 
	- `-r`: reverse order (Z to A)
	- `-n`: numeric sort (for numbers)
	- `-u`: unique lines only (remove duplicates)
	- `-R`: random order
	Uniq command only removes adjacent duplicate lines. While sorted -u sorts the file then removes the duplicates ensuring only the true uniq stays.

27. xxd : versatile CLI utility
	- `xxd <binary>` shows the hexdump of binary
	- `echo "hex" | xxd -r -p` to convert form hex  -r -> reverse

28. base64 : Command line utility to manipulate base64
	- `echo "" | base64` - encode into base64
	- `echo "" | base64 -d" - decode from base64



