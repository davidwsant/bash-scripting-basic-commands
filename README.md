# Bash Scripting Basic Commands
Bash scripting is a Unix shell command language that allows you to send commands directly to your operating system. It was created by [Brian Fox in 1989](https://en.wikipedia.org/wiki/Bash_(Unix_shell)) to be a free software replacement of the bourne shell, and bash actually stands for “Bourne Again Shell”.

Both Linux and MacOS operating systems are based on Unix operating systems, and command terminals for both generally default to the bash shell. Although there are minor differences between the two operating systems, the syntax for bash scripting is near identical. Note that bash is not the only shell that can be used. Others include *ksh*, *csh*, *zsh*, and *tcsh*. There are some slight differences in the commands from different shells, so I am going to focus on bash as it is usually the default shell.

## The Command Line:
To open the terminal, you can search in the "Applications" folder or something similar and find a program called "terminal" or find an icon that looks like this: ![Mac_Terminal_Icon.png](attachment:Mac_Terminal_Icon.png)

If you have a Windows computer this can be a little more difficult, as Windows does not generally have a built-in terminal. If you have access to a Linux server setup somewhere, you can log in to that computer remotely using [PuTTY](https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html) or you can install a terminal with a [Ubuntu](https://itsfoss.com/install-bash-on-windows/) environment that will allow you to use Linux on your Windows computer.

When you first open your command terminal, you will get a page that will probably contain information about your login (when you opened the terminal), and the final line will end in a "$" followed by a space. It is important to note that this is an indication of the line where you can type your commands. It will probably look something like this login picture I found on [Google](https://www.howtogeek.com/howto/ubuntu/keyboard-shortcuts-for-bash-command-shell-for-ubuntu-debian-suse-redhat-linux-etc/): ![Linux_Login.png](attachment:Linux_Login.png)

Note that it is common to write training documents where a "$" is an indication of a command that you should type, but you will not type the dollar sign symbol at the beginning of your command. This will be true in the documents relating to this git repository.

## Directories
The setup of directories in the terminal resembles what you see in Finder on macOS or in Windows Explorer on a Windows operating system, except that what most people refer to as “folders” will be called “directories”.

When you are working from the command line, you are always working from a directory. Wherever you are working from is called your “working directory”. It is possible to switch your working location and to see where you are working from, but first you need to know the setup of how it is going to be displayed.

The path of a directory is displayed where a “/” at the end of a name indicates that it is a directory, and whatever follows is a sub-directory. For example, a working path of “/Users/David/Documents/Dave_Documents/Classes/Class1/” tells you that whatever I did was in the directory “Class1”, and if I were using Finder I could get to this location by clicking on “Users”, then finding the sub-folder called “David”, then finding the sub-folder called “Documents”, then finding the sub-folder called “Dave_Documents”, then finding the sub-folder called “Classes”, then finding the sub-folder called “Class1”. You can see how writing this out with slashes makes it much simpler than writing it over multiple lines to indicate different levels, or writing it out in a sentence such as I just did.

There are also a couple of other things that tell you a location without using the entire path. In locations, a “.” indicates the current directory. Another one is two dots, “..” which indicates up one level. Another common abbreviation is the tilde “~” (top left, above tab key) which represents your home directory. So I could write out my current directory the way I did, or I could shorten it to “~/Documents/Dave_Documents/Classes/Class1/”. Another important thing to note is the top folder which is not named, but shown by the first / in the pathway. This folder is referred to as the "root" directory. It is usually important to not mess with things in root because you can accidentally delete your operating system or other important elements of the operating system. Remember these abreviations as they make moving around in directories much simpler.

Character(s) | Indicates
--- | ---
`.` | Current Directory
`..` | Up One Level to Parent Directory
`~` | Home Directory

## Manipulating Your Working Path

Now for how to move around in bash and how to make, move, rename or move folders.

The first command is `pwd`. This stands for "Present Working Directory". If you type this at the command line and hit enter, it will show you the path to the directory that you are currently in.

The next command is `cd`. This stands for "change directory". There are usually many ways to get to the path you want to use. You can use the absolute path (where you specify the path from root). For example, `cd ~/Documents/Dave_Documents/Classes/Class2/` means to move into the directory Class2 using the given path. Alternately, `cd ../Class2/` means to move up to the parent directory, then back down to a directory called Class2. This only works if you type the path relative to where you are currently working, but can save a lot of hassle.

Another important task is making directories. If you start a new project, it is likely that you want to make a new directory to work in where you will save all of your files related to the project. The command is mkdir, which stands for make directory. If you are operating from the “~/Documents/Dave_Documents/Classes/” directory and you want to make a new directory in your current working folder called “Class3” you could use either of the following:
<br>`mkdir ~/Documents/Dave_Documents/Classes/Class3` or `mkdir Class3` Now you can cd into the directory and work from there.

Another important task is deleting directories. Although not used quite as much as making a directory, this is still important. You can use one of two commands, `rmdir` or `rm -r`. Rmdir stands for remove directory, and rm -r stands for remove recursively. To remove the directory Class3 you can move into the ~/Documents/Dave_Documents/Classes directory and type `rm -r Class3` or you can move to any higher level folder and type `rm -r ~/Documents/Dave_Documents/Classes/Class3`

Moving the location of directories. You can move a directory by using the `mv` command, which stands for "move". You simply type mv, followed by the name of the directory you want to move, a space and then the new path. Suppose you created a directory "~/Documents/Dave_Documents/Classes/New_Classes", but you meant to have it up one level higher.  You can use `mv New_Classes ../` which means move it up into the parent directory. Although I used a relative path here, it might be wise to use the full path for moving directories.

Renaming directories can also be important. Suppose you named your new directory Class23 instead of Class3 because you accidentally hit two buttons at once. To rename the directory, you use the `mv` command, but you give the new name of the directory for the final bit. You can use this `mv Class23 Class3`. As long as Class3/ doesn't already exist, it will simply rename the directory.

Copying directories can also be important. You use the `cp` command, which stands for copy. You will have to use the -r to make it recursive and copy everything inside the directory. If I wanted to copy my directory Class3 up one level, I could use `cp -r Class3/ ../`

Another thing you are going to want to know at this point is how to list the directories and files in your current directory. This uses the `ls` command. Like pwd, you simply type ls and hit enter. There are multiple options on how to list these, and these can be added by using a dash followed by the symbol. Things included are (followed by what they stand for): l(long), a(all), r(reverse order), t(time), and h(human readable). `ls -l` means list long, which will give you information about the directory or files, including if it is a directory or not, who has rights to read or execute the file (more info on this later), as well as info on who created the file, the size of the file, the time that the file was created, and then the files. Often computers are set to have an alias of `ll` so typing "ll" is the same as typing "ls -l". If you instead use -a, you are calling all files. There are some files that are "invisible" that start with a ".". These are usually ones you won't want to edit and are usually used by the operating system. The -r means reverse order and the -t option says to sort by time. These are often used together. `ls -rt` means list by time they were created in reverse order, meaning to show the most recent files and directories on top. The -h option says to change the size of the files to a human readable format. In other words, instead of showing the number of bits, show it in KB, MB, GB, TB, etc. It is common to use these all together, commonly referred to as "larth" because that includes all of these: `ls -larth`. The output of `ls -la` looks something like this:
![ll_Screenshot.png](attachment:ll_Screenshot.png)

In this screenshot, note that this is a list of all files and directories in this directory. The left most column is info on whether or not it is a directory as well as who can access it. The column that says "david" simply mentions the user name of the person that created the files (me). The column that says "staff" just says the group that I am in. The next column of numbers is the file sizes (in bits, not human readable). The next three columns give the month, day, and time that the files were created. The final column is the name of the files or directories. Note that the files that start with a "." are present, indicating that I used "ls -la".


Here is a simple table that explains these commands:

Command | Indicates | Example
--- | --- | ---
`pwd` | Present Working Directory | `pwd`
`cd` | Change Directory | `cd ../Class2/`
`mkdir` | Make Directory | `mkdir Class3`
`rmdir` | Remove Directory | `rmdir Class3/`
`rm -r` | Remove Recursively | `rm -r Class3/`
`mv` | Move | `mv New_Classes ../`
`mv` | Rename (using move) | `mv Class23 Class3`
`cp -r` | Copy Recursively | `cp -r Class3/ ../`
`ls` | List | `ls`
`ls -la` | List all, long | `ls -la`

## Spaces
Another important thing that you may have noticed is that none of the directories used yet have a space in the name. It is possible to use directories that have a space in the name, but it is a pain because the space actually means something on the command line. It generally represents a separation between things. In other words, using `cd Class3` would be taken as change directory into a directory called "Class3". However, using `cd Class 3` would mean change directories into one called "Class" and then a random 3 at the end, which would be taken as if you were trying to say there is another directory and it is called 3. To get around spaces, it is common to use dashes and underscores. If you have created a directory or file previously and it has a space in the name, to call it you can use a backslash `\`. For instance, if you have a directory called "Class 3" you could enter it using `cd Class\ 3`

## Tab completion
Will update this later with info about tab-completion.

## Using the Mouse to Click
Will update this later with info about how you can't use mouse clicks, but there are ways to get to what you need.
