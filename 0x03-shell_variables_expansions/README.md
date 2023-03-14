## Commands
### export 
```bash
# We can use it to make a variable global 
export my_var
# We can also use it to add any path we want to PATH variable
# Note -> we use : to add a dir
export PATH="$PATH:/Mydir"
```
### dot .
```bash
# We use the . command to execute commands from a specified file in the current shell enviroment. It is also lnown as the "source" command.
# For Example if we want to execute a shell file we use 
. myfile.sh 
# Or
./myfile.sh
# Or 
source myfile.sh
```
### printf
```shell
# We use printf to format our output
# %d -> prints decimal number
# %f -> prints a floating-point number
# %c -> prints a single character
# %s -> prints string
# %x -> hexadecimal
printf "Hello %s \n" "mostafa"

# We can use modifiers to control the output format
# - %-10s -> left justifies a string with 10 characters
# - %10d -> right justifies a string with 10 characters
# - %04d -> pads a decimal integer with leading zeros before him
```

## Shell Initialization Files
### What are the /etc/profile and the /etc/profile.d directory
- The ``/etc/profile`` file is a system wide config file that is executed by the shell whenever a user logs in. this file is typically used to set enviroment variables and define system wide shell settings that apply to all users in the system
- The `/etc/profile.d` directory is a directory that contains additional shell scripts that are wxecuted by the shell when a user logs in. These scripts are typically used to set enviroment variables and define shell settings for specific applications or subsystems
### What is the `~/.bashrc` file
- The ~/.bashrc file is a shell script that is executed by the bash shell whenever a user opens a new terminal window or starts a new interactive shell session. This file is typically used to define user-specific enviroment variables, aliases, and other shell settings.
- The tilde charachter (~) at the beggining of the filename is a shorthand notation for the user home directory, if the user name is **mostafaamine**, the ~/.bashrc will be located at /home/johndoe/.bashrc
## Variables
### What is the difference between a local and a global variable
- A local variable is a variable that is defined within a specific process or shell session. It is only accessible within that process or session, and it is destroyed once the process or session terminates. Local variables are often used to store temprorary values or intermidiate results in a program or script.
```bash
VAR="Hello, World!"
echo $VAR
```
- A global variable is a variable that is defined system-wide and is accessible by all processes and shell sessions running on the system. Global variables are often used to store system-wide settings and confiurations.
- For example the `PATH` enviroment variable in linux and unix systems is a global variable that contains a list of directories where the system searches for executable programs.
### What is a reserved variable
- A reserved variable is a variable that is predifined and reserved by the shell for a pecific purpose. some examples of enviroment variables are `PATH` `HOME`
### How to create, update and delete shell variables
```bash
# To create a shell variable
title="FS WEB"
# To update a shell variable
title="FS WEB201"
# To delete a shell variable 
unset title

# It is important to note that shell variables are local to the current shell session by default. If we want to make it a global variable and an enviroment variable we use export command 
export my_var

# If we want to print all enviroment varibales (global variables) we use the command : 
printenv
# If we want to print all local variables and environment variables, and functions.
declare
```
### What are the roles of the following reserved variables: HOME, PATH, PS1
```bash 
# Home variable stores the absolute path of the user's home directory
echo $HOME
# PATH variable stores a list of directories where the shell searches for executable programs. When a user types a command in the shell, the shell cheks the directories listed in PATH in order to find the coresspending executable program. This variable is critical for running programs and scripts from the command line, as it determines where the system looks for these programs
echo $PATH
```
### What is the special parameter `$?`?
- The special parameter `$?` contains the exit status of the last executed command in the shell.
- The exit status is a numeric value between 0 and 255 that indecates whether a command was successful (exit status 0) or encountred an error (exit status greater than 0)
- You can access the value of `$?` parameter using the echo command. 
## Expansions
### What is expansion and how to use them
- In shell programming, "expansion" refers to a feature that allows you to manipulate strings and variables in various ways. Expansions are essentially shell commands that are processed before any other command is executed.
- To use expamsions read this article: [link](http://linuxcommand.org/lc3_lts0080.php)
### What is the difference between single and double quotes and how to use them properly
- single quotes are used to create a litteral string, where all characters within the quotes are treated as plain text and no expansion is performed. This means that variables and special characters within single quotes are not evaluated and are treated as plan text For example : 
```bash
echo 'info $PATH' # info $PATH
```
- Double quotes. on the other hand allow for expantion of variables and special characters within the quotes
```bash
echo "info $PATH"
# info /usr/local/rvm/gems/ruby-3.1.3/bin:/usr/local/rvm/gems/ruby-3.1.3@global/bin:/usr/local/rvm/rubies/ruby-3.1.3/bin:/vscode/bin/linux-x64/5e805b79fcb6ba4c2d23712967df89a089da575b/bin/remote-cli
```
### How to do command substitution with `$()` and backticks
- Command substitution is a feature in shell scripting that allows the output of a command to be substituted in place of command itself. there are two ways to perform command substitution in shell :
```bash
# using $()
echo "Hello your current working directory is $(pwd)"
# using baskticks
echo "Hello your current working directory is `pwd`"
```
## Shell Arithmetic
### How to perform arithmetic operations with the shell
- We can perform arithmetic operations using the built-in `expr` command, or by using the $(()) syntax.
- For example : 
```bash
a=10
b=20
# Using expr (whitespaces after expr is required)
sum=$(expr $a + $b)
echo $a + $b = `expr $a + $b`
# Using $(())
sum=$(($a + $b))
```
### Converts
- We can also convert like from binary to decimal or from decimal to hexadecimal
```bash
echo "obase=li baghine n7awlo liha; $BINARY" | bc
```