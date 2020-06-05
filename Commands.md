# List of Command Line Commands ( Linux )

Here’s an appendix of commonly used commands.

###　__INFO__

Similar to man, but often provides more detailed or precise information.

    $info

### __SUDO__

Used to continue the session as a root user which has a lot more privileges than normal system user.

    $ sudo su

### __W__

Tells you who's logged in, and what they're doing. Especially useful: the 'idle' part.

    $ w

### __WHO__

Tells you who's logged on, and where they're coming from.

    $ who

### __WHOAMI__

Returns your username.

    $ whoami

### __UNAME -A__

Provides a wide range of basic information about the system.

    $ uname -a

### __PASSWD__

Change your password

    $ passwd

Change sam_leung's password:

    $ passwd sam_leung

### __PS__

Shows the processes for the current shell

    $ ps

Lists your processes

    $ ps -u ${username}

- `PID` – the unique process ID
- `TTY` – terminal type that the user is logged into
- `TIME` – amount of CPU in minutes and seconds that the process has been running
- `CMD` – name of the command that launched the process.

### __KILL PID__

Kills (ends) the processes with the ID you gave.

    $ kill -9 ${PID}

### __SHUTDOWN__

Immediately shut down the system.

    $ shutdown -h now

### __REBOOT__

Immediately reboot the system.

    $ reboot

### __LAST REBOOT__

Checking your reboot logs

    $ last reboot

### __UPTIME__

Provides information about how long the system has been running

    $ uptime

### __EXIT__

It is used to exit from the system and log out from the current user.

    $ exit

### __WHICH__

Which command in Linux is a command which is used to locate the executable file associated with the given command by searching it in the path environment variable.

    $ which pwd

### __WHEREIS__

The command “whereis” is self-explanatory, as it displays the path where the package for specific built-in Linux command locates.

    $ whereis zip

### __WHATIS__

The command “whatis” is also self-explanatory, as it displays a brief description of what is the functionality of specific built-in Linux command.

    $ whatis

### __CAT__

It is used to display each line of the file starting from the first row and finishing on its last row.

    $ cat hello_world.txt

### __HEAD__

Prints the top N rows of data of the given input or file. By default, it prints the first 10 lines of the specified files.

    $ head -5 hello.world.txt


### __TAIL__

Prints the last N rows of data of the given input or file. By default, it prints the last 10 lines of the specified files.

    $ tail -5 hello_world.txt


### __ECHO__

Used to display any expression that is passed as an argument.

    $ echo $HOME

### __>__

`>` takes the standard output of the command on the left and redirects it to the file on the right.

    $ cat hello.txt > world.txt

### >>

`>>` takes the standard output of the command on the left and appends (adds) it to the file on the right.

    $ cat hello.txt >> world.txt

### __<__

`<` takes the standard input from the file on the right and inputs it into the program on the left.

    $ cat < hello_world.txt


### __|__

`|` is a “pipe”. The `|` takes the standard output of the command on the left, and pipes it as standard input to the command on the right. You can think of this as “command to command” redirection.

    $ cat hello_world.txt | wc


### __~/.BASH_PROFILE__

`~/.bash_profile` is the name of file used to store environment settings. It is commonly called the “bash profile”. When a session starts, it will load the contents of the bash profile before executing commands.

    $ nano ~/.bash_profile

### __ALIAS__

The `alias` command allows you to create keyboard shortcuts, or aliases, for commonly used commands.

    alias pd="pwd"

### __CD__

`cd` takes a directory name as an argument, and switches into that directory.

    $ cd Desktop

#### __CD ..__

To move up one directory, use cd ... Here, cd .. navigates up from .../hello/world/ to .../hello

    $ cd ..

### __CP__

`cp` copies files or directories. Here, we copy the file hello_world.txt and place it in the hello/world directory

    $ cp hello_world.txt hello/world

### __WILDCARDS (*)__

The wildcard `*` selects all of the files in the current directory. The above example will copy all of the files in the current directory to the directory called `satire`. There are other types of wildcards, too, which are beyond the scope of this glossary.

    $ cp * hello/

Here, h*.txt selects all files in the working directory starting with “h” and ending with “.txt”, and copies them to hello/.

    $ cp h*.txt hello/


### __ENV__

The `env` command stands for “environment”, and returns a list of the environment variables for the current user.

    $ env

### __ENV | GREP VARIABLE__

`env | grep PATH` is a command that displays the value of a single environment variable.

    $ env | grep PATH

### PATH

`PATH` is an environment variable that stores a list of directories separated by a colon. Each directory contains scripts for the command line to execute. PATH lists which directories contain scripts.

    $ echo $PATH

### __HOME__

The `HOME` variable is an environment variable that displays the path of the home directory.

    $ echo $HOME

### __EXPORT__

`export` makes the variable to be available to all child sessions initiated from the session you are in. This is a way to make the variable persist across programs.

    $ export USER="sam.leung"

### __GREP__

`grep` stands for “global regular expression print”. It searches files for lines that match a pattern and returns the results. It is case sensitive.

    $ grep "hello" hello_world.txt

### __GREP -I__

`grep -i` enables the command to be case insensitive.

    $ grep -i "hello" hello_world.txt

### __GREP -R__

`grep -R` searches all files in a directory and outputs filenames and lines containing matched results. `-R` stands for “recursive”.

    $ grep -R hello /home/samleung/Desktop/hello

### __GREP -RL__

`grep -Rl` searches all files in a directory and outputs only filenames with matched results. `-R` stands for “recursive” and `l` stands for “files with matches”.

    $ grep -Rl hello /home/samleung/Desktop/hello

### __DIR__

Used to display the list of all directories or folder in the current directory.

    $ dir

### __LS__

`ls` lists all files and directories in the working directory

    $ ls

### __LS -A__

`ls -a` lists all contents in the working directory, including hidden files and directories

    $ ls -a

__*OPTIONS*__

| option  | description                                            |
| :------ | :----------------------------------------------------- |
| -a      | list all files including hidden file starting with '.' |
| --color | colored list [=always/never/auto]                      |
| -d      | list directories - with '\*/'                          |
| -F      | add one char of \*/=>@ \| to enteries                  |
| -i      | list file's inode index number                         |
| -l      | list with long format - show permissions               |
| -la     | list long format including hidden files                |
| -lh     | list long format with readable file size               |
| -ls     | list with long format with file size                   |
| -r      | list in reverse order                                  |
| -R      | list recursively directory tree                        |
| -s      | list file size                                         |
| -S      | sort by file size                                      |
| -t      | sort by time & date                                    |
| -X      | sort by extension name                                 |


### __MKDIR__

`mkdir` takes in a directory name as an argument, and then creates a new directory in the current working directory. Here we used mkdir to create a new directory named `hello/`.

    $ mkdir hello

### __MV__

To move a file into a directory, use mv with the source file as the first argument and the destination directory as the second argument. Here we move hello_world.txt into hello/.

    > $ mv hello_world.txt hello/

### __NANO__

nano is a command line text editor. It works just like a desktop text editor like TextEdit or Notepad, except that it is accessible from the the command line and only accepts keyboard input.

“mv” to Move Files

    $ nano hello_world.txt

“mv” to Rename Files

    $ mv hello.txt world.txt

### __PWD__

`pwd` prints the name of the working directory

    $ pwd

### __RM__

rm deletes files. Here we remove the file hello_world.txt from the file system.

    $ rm hello_world.txt

### __RM -R__

`rm -r` deletes a directory and all of its child directories.

    > $ rm -r hello

### ___RMDIR_

Allows users to remove directories/folders from the system.

    $ rmdir ${dir_name}

### __SED__

`sed` stands for “stream editor”. It accepts standard input and modifies it based on an expression, before displaying it as output data.

    $ sed 's/hello/world/' hello_world.txt
    $ echo "hello world" | sed 's/hello/world/'

In the expression 's/hello/world/':

- `s`: stands for “substitution”.
  
- `hello`: the search string, the text to find.
  
- `world`: the replacement string, the text to add in place.

### __SORT__

`sort` takes a filename or standard input and orders each line alphabetically, printing it to standard output.

### __STANDARD ERROR__

standard error, abbreviated as `stderr`, is an error message outputted by a failed process.

### __SOURCE__

source activates the changes in `~/.bash_profile` for the current session. Instead of closing the terminal and needing to start a new session, `source` makes the changes available right away in the session we are in.

    $ source ~/.bash_profile

### __STANDARD INPUT__

standard input, abbreviated as `stdin`, is information inputted into the terminal through the keyboard or input device.

### __STANDARD OUTPUT__

standard output, abbreviated as `stdout`, is the information outputted after a process is run.

### __TOUCH__

`touch` creates a new file inside the working directory. It takes in a file name as an argument, and then creates a new empty file in the current working directory. Here we used touch to create a new file named hello_world.txt inside the hello/world/ directory.

If the file exists, touch is used to update the modification time of the file

    $ touch hello_world.txt

### __UNIQ__

`uniq`, short for “unique”, takes a filename or standard input and prints out every line, removing any exact duplicates.

    $ uniq hello_world.txt

### __FIND__

For instance to search files that start with the word "hello"

    $ find /path/to/file/ -iname hello*

Search for empty files

    $ find /path/to/file/ -iname -empty

To search for files that were accessed less than 2 days ago

    $ find . –atime -2

To search file whose size is larger than 5MB size

    $ find . –size +5M\

To search for a file with the permission of 644

    $ find . –type f –perm 644

### __DF__

Shows the amount of disk space used and disk space available on every file system containing each filesystem’s name and its path.

    $ df

-h: human-readable

    $df -h

### __DU__

Displays the size of a directory and all of its subdirectories.

    $ du

### __FREE__

Displays the amount of free and used memory in the complete system.

    $ free

### __HISTORY__

Displays the list of all commands entered since the user started the session.

    $ history


### __CLEAR__

Clear the screen of Terminal.

    $ clear

### __TOP__

Displays the processes using the most system resources at any given time. “q” can be used to exit.

    $ top

### __MAN__

The command of “man” stands for manual and it is used to display the user manual of any built-in Linux command.

    $ man nano

### __ZIP__

Used to compress one or more files and store them in a new file with .zip extension.

    $ zip Files.zip Check.txt Test.txt Output.txt
    $ zip -r Files.zip hello

### __UNZIP__

 Used to decompress a .zip file and extract all the files within to current directory.

    $ unzip Files.zip

### __DATE__

 shows the current date and time.

    $ date

### __CAL__

shows a calendar of the current month or specify month / year.

    $ cal
    $ cal 2020
    $ cal 06 2020