---
description: A guide to basic command line terminal usage on a UNIX based machine.
---

# Command Line Usage

* [What is UNIX?](command-line-usage.md#what-is-unix)
* [Key Concepts](command-line-usage.md#key-concepts)
* [The Shell](command-line-usage.md#the-shell)
* [Command Line Usage](command-line-usage.md#command-line-usage)
* [Current Working Directory and Paths](command-line-usage.md#current-working-directory-and-paths)
* [Useful commands and tips](command-line-usage.md#useful-commands-and-tips)
  * [whoami](command-line-usage.md#whoami)
  * [which](command-line-usage.md#which)
  * [pwd](command-line-usage.md#pwd)
  * [ls](command-line-usage.md#ls)
  * [cd](command-line-usage.md#cd)
  * [mkdir](command-line-usage.md#mkdir)
  * [cp](command-line-usage.md#cp)
  * [mv](command-line-usage.md#mv)
  * [rm](command-line-usage.md#rm)
  * [touch](command-line-usage.md#touch)
  * [echo](command-line-usage.md#echo)
  * [cat](command-line-usage.md#cat)
  * [head](command-line-usage.md#head)
  * [tail](command-line-usage.md#tail)
  * [less](command-line-usage.md#less)
  * [grep](command-line-usage.md#grep)
  * [find](command-line-usage.md#find)
  * [sed](command-line-usage.md#sed)
* [Pretty colors and Text editors](command-line-usage.md#pretty-colors-and-text-editors)

## What is UNIX?

UNIX is an operating system originally developed in the 1960s that is the base for modern operating systems such as macOS X, GNU/Linux, Sun Solaris, and many more. While modern UNIX systems usually have a graphical user interface (GUI) that you can use to interact with the system and run programs, the most direct and powerful way to interact with the <mark style="color:blue;">**kernel**</mark> (operating system core) is through the <mark style="color:blue;">**shell**</mark> (command line).

## Key Concepts

Pretty much everything in UNIX is either a <mark style="color:blue;">**file**</mark> or a <mark style="color:blue;">**process**</mark>. Files are simply collections of data – they can be plain text, programs, binary machine code, or even directories. A process is a program that is being executed by the kernel.

The file-system on UNIX is very simple – it’s a tree that starts at <mark style="color:blue;">**root**</mark>, which is written as /. Everything then branches off of the root with a location specified by a <mark style="color:blue;">**path**</mark> from the root to the file. For example, if there were a user on a UNIX system with the username **unixuser1**, the home directory would typically be located at /home/unixuser1. If this user had written a hello world program in c and put it in a directory called **myprograms** in their home directory, that path would look like /home/unixuser1/myprograms/hello.c. It’s useful to think of the file-system as a tree that you navigate up and down through, and create routes from one spot to another. More on this later!

![](<../.gitbook/assets/image (24).png>)

## The Shell

The shell is the interface between the user and the kernel – it is a command line interpreter (CLI) which takes commands that the user types in and sends them off to the kernel to be carried out. Commands in UNIX are actually programs, which means that they are files on the system. When a user enters a command, the shell goes and finds that program and arranges for it to be executed by the kernel. The shell is configured through some other files that it looks at when it starts up to know where these programs are located so that the user doesn’t have to type out the path each time they want to use them.

## Command Line Usage

When you open your command line terminal, you should see something like this:

![](<../.gitbook/assets/image (45).png>)

This line is called the prompt – it is the shell waiting for the user to enter a command to run. Typically, the prompt will end with a $, meaning the shell is ready to accept a command.

Your prompt will probably look a little bit different, as this system has some customization and configurations set that print some extra information and changes the colors. This will be explained at the end! Just make sure you see a $ at the end of the line.

To execute a command, simply type it out on the command line after the prompt and press enter! Some commands can accept additional arguments or flags that will change the way they print things out or how they execute. Arguments are passed to a command as <mark style="color:red;">**space separated**</mark> strings of text. Because they are space separated, you cannot include spaces in your arguments - they will be interpreted as separate arguments. To pass in a string with spaces, you must either escape the space character by placing a **\\** in front of the space, or put the entire string in double quotes ("). Be careful though, as not all commands behave the same! **It is best practice to not use spaces and other special characters in filenames if it can be helped**. More on passing arguments will be shown in the following examples.

### Current Working Directory and Paths

The shell has a concept of a <mark style="color:blue;">**current working directory**</mark>, which can be thought of as the location in the file-system that the shell is currently “looking” at. When you start a terminal, usually the current working directory is the home directory of the user, typically at /home/username, or /Users/username on mac.

As stated earlier, a path is a string that tells the shell where to look for a specified file. There are two types of paths, <mark style="color:blue;">**absolute paths**</mark> and <mark style="color:blue;">**relative paths**</mark>. An absolute path starts at root (/) and lists out the entire file-system route to a file. For example:

`/home/unixuser1/myprograms/hello.c`

A relative path is the route through the file-system from one location to another. These are useful as they require fewer characters, less typing, and allow programs to be written that interact with the file-system that can run from anywhere and not have to worry about where the current working directory was when it was called.

When writing out paths on the shell, if you do not write an absolute path, the shell will interpret the path as relative **starting from the current working directory**. For example, let’s say a user wants to do something with the hello.c file in their /home/unixuser1/myprograms directory, and their current working directory is their home directory (/home/unixuser1), as in this figure:

![](<../.gitbook/assets/image (11).png>)

The relative path to their c file would be the following:

`myprograms/hello.c`

This would be interpreted the same as the absolute path /home/unixuser1/myprograms/hello.c, but it requires less typing!

It is also possible to write relative paths to things further up or in a different branch of the file-system. For example, if the current working directory is /home/unixuser1/Desktop, and the user wants to reference the same c file as above, visually it would look like this:

![](<../.gitbook/assets/image (5).png>)

and the relative path would be:

`../myprograms/hello.c`

The double dot (..) means up one level in the file-system. You can go up more than one level by stringing them together. For example, given a current working directory of /home/unixuser1/Desktop/another\_directory, to reference the same file the relative path would be

`../../myprograms/hello.c`

## Useful commands and tips

* Double dot .. means the directory above the current one. A single dot . means this current location.
* **Tab** can be to autocomplete a path or filename. Start typing the first letters, then hit **Tab.** <mark style="color:red;">**USE THIS!**</mark> It will prevent you from making typos or looking for something that doesn’t exist, and saves time overall.
  * Hitting **Tab** twice in quick succession will print out all files matching up to the point typed, then allows you to keep typing.

![It would be really annoying to type out that filename! Just use Tab autocomplete!](<../.gitbook/assets/image (36).png>)

* The star character <mark style="color:blue;">\*</mark> matches 0 or more characters in a filename. For example, \*.txt would match all files ending in .txt.
* The tilde character <mark style="color:blue;">\~</mark> stands for the home directory of a user.
* **Ctrl + C**: kills the current foreground running process in the terminal and returns control back to the user (prints a new prompt).
* **Ctrl + L**: Clear the screen. Alternatively, use the <mark style="color:blue;">clear</mark> command.
* **Ctrl + A** or Home: Moves the cursor to the end of the line.
* **Ctrl + E** or End: Moves the cursor to the end of the line.
* **Ctrl + K**: Deletes from the current cursor position to the end of the line. String this together with Ctrl + A to delete everything on the line!
* The **up arrow** and **down arrow** on your keyboard will let you scroll through your recent commands so you don’t have to retype them.
* **Ctrl + R**: Recall the last command matching the characters you provide. Press repeatedly to search past the last matching to previously matching commands.
* <mark style="color:blue;">command > file</mark> redirects the output of a command to a file, overwriting existing content.
* <mark style="color:blue;">command >> file</mark> redirects and appends output of command into a file (does not overwrite).
* <mark style="color:blue;">first\_command | second\_command</mark> is a pipeline, (the | character is called a pipe). This will send the output of the first command as input to the second command.

Here are a few useful commands for navigation, inspection, and basic file manipulation on the command line. This is by far from being exhaustive! Most operating systems will have documentation listing out available commands and how to use them. You can also use the command <mark style="color:blue;">man \<command></mark> to bring up the documentation (or <mark style="color:blue;">man</mark>ual) for a command within the shell. Press q to quit the manual after running. You can type `/<search_string>` to search through the manual.

#### <mark style="color:blue;">whoami</mark>

Displays the username of the current user.

![](<../.gitbook/assets/image (10) (1).png>)

Notice that after executing the command, the shell will print a new prompt for the user to enter another command.

#### <mark style="color:blue;">which</mark>

Identifies the location of an executable. Use this to determine if a command or program is installed on your system, and also to see where it actually resides on the file-system. If the program cannot be found, nothing will be returned.

![](<../.gitbook/assets/image (2) (1) (1).png>)

#### <mark style="color:blue;">pwd</mark>

Stands for **P**rint **W**orking **D**irectory. It prints the absolute path of the current working directory from root. The current working directory is the location on the file-system where the shell is currently focused.

![](<../.gitbook/assets/image (32).png>)

#### <mark style="color:blue;">ls</mark>

Stands for list. This command will list out all files in a given directory.

![](<../.gitbook/assets/image (30).png>)

You can provide a path to ls to list files not in the current working directory. Some useful flags are -l (long listing format), which can show you file permissions, owner, size, and last modified date, and -a (shows all files, including hidden files).

![](<../.gitbook/assets/image (2) (1).png>)

![Notice the .im\_a\_hidden\_file.txt entry that is only in the output when using -a.](<../.gitbook/assets/image (37).png>)

#### <mark style="color:blue;">cd</mark>

Stands for **C**hange **D**irectory. Moves the current working directory to the path specified as an argument to the command. The syntax is `cd <path>`, where \<path> can be any relative or absolute path on the file-system. If the path is invalid, the current working directory will stay the same.

![](<../.gitbook/assets/image (8).png>)

#### <mark style="color:blue;">mkdir</mark>

Stands for make directory. Creates a directory at the stated path if it does not already exist.

![](<../.gitbook/assets/image (35).png>)

#### <mark style="color:blue;">cp</mark>

Stands for copy. Copies file at one path to another specified path. If the path to be copied to is a directory, cp will copy the file and keep the same filename. You can also specify a new filename. The syntax is <mark style="color:blue;">cp \<file\_to\_copy> \<new\_location></mark>

![](<../.gitbook/assets/image (22).png>)

If you want to copy an entire directory, pass the <mark style="color:blue;">**-r**</mark> flag.

![](<../.gitbook/assets/image (33).png>)

#### <mark style="color:blue;">mv</mark>

Stands for move. Works exactly like cp, but will remove (rename) the file from the original location.

![](<../.gitbook/assets/image (42).png>)

{% hint style="danger" %}
Notice in this example that the directory went from having two files to only having one! Be very careful with cp and mv – these commands will overwrite any existing files, and there is no undo or recycle bin!
{% endhint %}

#### <mark style="color:blue;">**rm**</mark>

Stands for remove. Delete a file at a given path. To delete an entire directory, pass the -r flag. You can also pass the -f flag which will not prompt for confirmation regardless of the files permissions. Remember, **there is no undo** when using this command. The syntax is rm \<filename>

![](<../.gitbook/assets/image (14) (1).png>)

#### <mark style="color:blue;">touch</mark>

Updates file timestamp information. Can be used to create an empty file.

![](<../.gitbook/assets/image (26).png>)

#### <mark style="color:blue;">echo</mark>

Outputs the strings being passed to it as arguments. You would usually pipe this command into other commands or use it to write data into a file through a single command. If you pass the -e flag, you can parse escaped characters. You can use this to print out Unicode symbols or different colors.

![](<../.gitbook/assets/image (31).png>)

To append a line into a file:

`echo "This is a string I want to append" >> myfile.txt`

![](<../.gitbook/assets/image (3) (1) (1).png>)

#### <mark style="color:blue;">cat</mark>

Stands for con**cat**enate**.** Displays the contents of a file. You can use it to concatenate by passing it multiple files, and it will print them to some output location.

![](<../.gitbook/assets/image (21).png>)

#### <mark style="color:blue;">head</mark>

Displays the first 10 lines of a file. Pass the -n argument to specify how many lines to display.

![](<../.gitbook/assets/image (39).png>)

#### <mark style="color:blue;">tail</mark>

Displays the last 10 lines of a file. Pass the -n argument to specify how many lines to display. Pass the -f flag to follow, or to not stop when end of file is reached, but rather to wait for additional data to be appended to the input. Press Ctrl + C to quit afterwards. **Useful for watching log files in real time**.

![](<../.gitbook/assets/image (4).png>)

#### <mark style="color:blue;">less</mark>

Like cat, but only displays contents from the beginning up to what will fit on the screen. Use the arrow keys (or j and k) to move the display through the file. Press q to quit.

#### <mark style="color:blue;">grep</mark>

Searches a file or files for lines that match a regular expression or string. There are lots of flags and options for this command depending on what you’re trying to do, run <mark style="color:blue;">man grep</mark> to see everything it can do.

For example, say you have a complicated project with many directories and want to find where a specific variable name or library is used. You could use grep to recursively look through all directories and look for that variable name. Grep will print the filename and contents of the line it found it on. In this example, the -r flag means to look recursively through any directory it finds, the -I means to ignore binary files, the -n will make it also print the line number, and the . means to start the search at this current location (the current working directory).

![](<../.gitbook/assets/image (47) (1).png>)

#### <mark style="color:blue;">find</mark>

Finds files with properties that match a specified pattern. To find a file with a specific name from the current working directory, type the following:

`find . -name "myfilename.txt "`

![](<../.gitbook/assets/image (23).png>)

You can also pass regex patterns to find multiple files that match a certain pattern. To find all c files, try the following:

`find . -name "*.c"`

![](<../.gitbook/assets/image (46).png>)

#### <mark style="color:blue;">sed</mark>

Stands for **S**tream **Ed**itor. Useful for searching, finding and replacing, inserting, or deleting things in files. As an example, maybe you want to replace all the tabs in every file within a directory to four spaces. You could do this all at once with one command:

`sed -i .bak $'s/\t/    /g' *.c`

The -i means to edit the files in-place, and backs up the files with an extension .bak. The characters within the quotes are what we are searching and replacing (basic regular expression), with / as a delimiter between what we are searching for, replacing, and any other options in the regex. So in this case, we are searching for \t (tab), and replacing it with four spaces. The g signifies to do this globally across the entire file and not just on the first occurrence. You can combine commands like <mark style="color:blue;">find</mark> with <mark style="color:blue;">sed</mark> to modify files across your file-system or in specific projects all at once.

If you really want to do some interesting command line text processing, check out the [<mark style="color:blue;">awk</mark>](https://en.wikipedia.org/wiki/AWK) command!

## Pretty colors and text editors

If you want the same coloring scheme I have in my terminal, edit the file \~/.bash\_profile using a simple text editor. If you want to do it in the terminal, try using nano (a very simple text editor) or vim (an extremely powerful editor with a learning curve). Look up the usage of these on google before you open them! If you want to learn vim, you can use the built-in program vimtutor that will guide you through the basics.

To turn on some basic coloring, add this line anywhere in the file:&#x20;

`export CLICOLOR=1`

The export command is setting the value of the environment variable CLICOLOR to 1, turning on colors.  You can change how these colors look by changing some other environment variables. For example:

`export LSCOLORS=GxFxCxDxBxegedabagaced`

This setting makes the ls command print in a different color scheme. You can look up how to customize this on your own.

Lastly, to make your username/hostname on the prompt have different colors or display different things, you can modify the PS1 environment variable, which contains the value of the default prompt:

`export PS1='\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '`

This makes my username (the \u) bold and green, prints an @, then the host name (\h) and a colon, then prints the current working directory in blue (\w) followed by a $ in white.

You can modify the .bash\_profile file to do lots of other useful things as well, such as making aliases for different commands, modifying or appending to environment variables, or setting up other things. Do your own research to see what kinds of things you can do!

Some terminals also have some color settings applied by default, or the ability to load up different profiles. Keep this in mind when trying to modify the appearance of your terminal.
