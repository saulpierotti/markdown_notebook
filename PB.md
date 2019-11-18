% Programming for Bioinformatics
% Saul Pierotti
% \today

# 14/11/19
* 5/12 mid term exam on paper, it is worth 8/32 points
* Finals are on February and march
* This module is about Python
* Textbooks are not required but can be interesting for an in-depth understanding
* Slides are really synthetic
* Tutor: Giacomo Tartari
* The main resource of a computer are RAM and CPU
* The OS allocates resources to programs, and impedes interference among them
* Linux is a kernel, it manages resources for the OS
	* It derives from Unix, like also MacOS
	* It is multithreaded (it can run more than 1 program at the same time) and multiuser
	* The users are isolated from each other, they cannot interfere
	* There are many Distros
* A Linux distro includes an install system for the distro itself, drivers, a package manager, tools
	* Some tools are really specific, and probabily I will never need them
	* A package manager allows to install and remove tools
* One user is root, the superuser
	* It should be used only when needed and with extreme caution
* The shell is the main interface of the OS
* The directory structure is a rooted tree
	* The root directory in linux is called `/`
* A file is the name given to a set of data
* A file needs to be contained in a directory
* An extension is an indication of the filetype, but does not determine it
* Python programs are text files with extension .py
* Some basic shell commands
	* The `Tab`button autocompletes the commands in the shell
	* `cd` is used to enter in a directory
	* `mkdir` creates a directory
	* `ls` lists all files and directories inside the current directory
		* `ls -l` gives more informations on the file, e.g. permissions
	* `.` is a shortcut for the current dir
	* `..` is a shortcut for the parent dir
	* `~` is a shrotcut for the home dir of the current user
	* Starting my path with the root dir `/` makes the path absolute
	* Starting with a directory directly is like starting with `./`
	* Writing `cd` without parameters is like writing `cd ~`
	* `pwd` prints the current dir
	* `cp` and `mv` are the copy and move commands
	* `rm` permanently deletes files
* Files can have different permissions
	* Users can be selectively allowed to read, write and/or execute files
	* The owner of a file can set permissions for everyone, users and groups
	* Permissions can be read as `-rwxrwr--`, where the first 3 charachters refer to user, then group, then others, then all
	* Permissions are added and remove with the `chmod` command
	* `chmod u+x` adds execute permission to user, while `chmod o-w` removes write permisission to others
* A running program is identified by a unique PID (program id)
	* `ps -a` lists all the running processes with PID
	* `kill PID` kills the running process
		* This should be used only as a last option (!)
* A single program can span multiple processes
* `sleep` suspends the current shell for the specified time
* `man` opens the manual of a command
* The argument of a command is the subject of the operation
* The parameter
* The output of a command can be written to a file with the redirect operator `>`
	* `ps -a > output.txt`
	* The error messages will still be printed on screen
	* If the file already exists, it is overwritten (!)
	* If I use the append operator `>>` instead, it adds the output at the end of the file
* To redirect errors we use `2>`, while to redirect both normal output and error `&>` is used
* To show the content of a file we can open it in a text editor, or use the following commands
	* `head` shows the first 10 lines
	* `tail` shows the last 10 lines
	* `cat` shows the whole file, and it is unpractical with long files
	* `more` shows the whole file page by page
	* `less` shows the whole file allowing to scroll
* There is a plethora of text editors
	* `nano` and `pico` are easy to use
	* `vim` and `emacs` are more advanced but less easy
	* Some have a GUI version, like `gvim` and `xemacs`
* A computer is fast, but stupid
	* It does exactly what you tell it to do
* Programming is useful for dealing with complex operations, repetitive tasks, huge amounts of data
* Sometimes I can do things with a PC without knowing how they are done: libraries
* Pyhton is fast to implement, widely used, has many libraries, it is well documented
	* It is not used so much by computer scientists, but a lot by non computer scientists
	* We want to be as efficient as needed, not as efficient as possible (!)
		* Using C can improve efficiency, but not as much as writing a good program
	* It is an imperative language
	* We can use C when we need to work really low-level, but often it is not needed
* A Python program can be written and used in different ways
	* I can create a text file and run it from the shell
	* I can use an IDE to write, execute, access documentation
	* I can write directly in the Python interpreter without creating a file
* Documentation is really useful as a reference, but is not really good for learning
* Things work most of the time, until they do not work once and no one knows why

# 15/11/19
* I can run a script in the background using an & after the command
	* `~ python test.py &`
* The operator / is division in python2, while in python 3 the operator // is integer division
	* The result of intyeger division is itself an integer
	* Floating point division in python3 is done by the operator /
	* In python2 the type of division is determined by the context
		* It is integer division only if both numbers are integers, otherwise it is floating point
		* If I want to do floating point division between integers, I need to first convert one of them to a float
* The operator % is the remainder of an integer division
* The operator * is multiplication, ** is exponentiation, + and - are sum and addition
* There are many built-in functions to perform calculations
* `e` and ` pi` are recognised as the respective constants
* To use functions from libraries I need to use the syntax
	* `from math import *`
		* `*` is a wildcard that means everything
		* I can also import a single command
	* The need to import commands is due to avoid an enormous number of function name clashes when I define a custom function
* A variable is the name of a memory location that can store a value
* Strings can be accessed by charachter by putting the index in parentheses
	* `str[0]`
* Substrings can be extracted as
	* `str[2:5]` extracts 2 included until 5 excluded
	* If I omit beginning or end, it considers the beginning or the end
	* `str[-2:2:-1]` specific to go by jumps of -1 (go backwards)
* String concatenation is done with the operator +
* You cannot change a string by assigning a value to an element of the string, you need to create a new string
* User input is collected with `input("message")` in python3 and `raw_input("message")` in python2
* Some methods for strings
	* `s.upper()`
	* `s.lower()`
	* `s.replace("a","b")`
	* `s.startswith("a")`
