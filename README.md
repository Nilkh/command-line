# The Command Line Interface

## Objectives
- View files within a directory.
- Create a directory (folder) to store a project.
- Create subdirectories to organize a project.
- Create files to hold project information.
- Edit and delete files.
- Navigate within a project.
- Get help from user manuals.

## Introduction to the Bash Terminal
What is a Bash terminal? It is a tool that allows us to interact with our computer using commands. Normally, we interact with our computer through a program's interface, such as a file explorer application. However, the terminal provides an alternative way to interact with our computer.

To open your file explorer application, you can click on its icon. Take note of the files you see there.

Note: On Mac, new windows don't open to the Home directory by default. To find this directory, click on "Go" and then "Home" at the top left of the computer screen.

## Exploring the Home Directory

When you open your terminal, you will notice that you start in your Home directory by default. You can see the files in this directory by using the `ls` command (mnemonic: "list"). The files and directories listed in the terminal will be the same as the ones in the file explorer application.

So, the terminal provides an alternative way to interact with our computer.

## User Manuals
The terminal offers commands that allow us to interact with it. Fortunately, the terminal also comes with a manual that provides information about these commands.

To access the manual, use the `man` command followed by the name of the command you want to learn more about. Let's see how this works.

Inside your terminal, type the following command:

`man rm`


You will receive the following information:

```sh
NAME
     rm, unlink -- remove directory entries

SYNOPSIS
     rm [-dfiPRrvW] file ...
     unlink file

DESCRIPTION
     ...
     The options are as follows:
     -d Attempt to remove directories as well as other types of files.
     ...
```
Let's break down each section on this manual page:

- **Name:** The name of the command, followed by a brief description of what it does.
- **Synopsis:** A formal description of how to run the command and what command line options it accepts.
- **Description:** A textual description of how the command works.

In the Synopsis section, you can see how to use the rm command. Let's use this information to remove a directory called "removeMe":

`rm -d removeMe`
Here's the breakdown of the command:

- Start with the command, `rm`.
- Use the option or flag, `-d`, because this is a directory. By default, the `rm` command only removes files.
- Provide the name of the directory you want to remove.
*Note: In the Synopsis section, you see `[-dfiPRrvW]`. These are commonly called flags. You can find the description of each flag in the Description section of the manual.*

## Cheat Sheet
### Group Activity

Let's familiarize ourselves with some common commands and create a cheat sheet for reference throughout this lesson.
Open [cheatSheet.md](cheatSheet.md) and complete each section. We already went over rm so it's already completed for you.

## Exploring the File System
You're probably used to creating files and folders using your operating system's "explorer" program. The common explorer programs found on each OS are:

Mac: Finder
Windows: File Explorer
Ubuntu: Files
On unix-like systems (sometimes referred to as *nix or POSIX), all your files are stored in your home folder. On Windows, your files are usually stored in "My Documents".

You might see `~` or `$HOME` used to refer to your home folder on unix-like systems.

## Directories and Paths
Directories (and subdirectories) are typically referred to as "folders" in your file explorer. They serve as convenient ways to group files together. Paths are textual representations of your current location in the file hierarchy or "tree".

Examine this path: `/Users/Zomia`. The leading slash (/) represents the root of the file system. The "Users" part indicates the presence of a directory (or folder) named "Users" within the root of the file system. Inside the "Users" directory, there is another directory called Zomia. Therefore, the string `/Users/Zomia` is an absolute path to the home directory of the current user.

## Absolute Paths
An absolute path provides the unique location of files and directories within the file system. No other files can have the same absolute path.

*Note: It can be helpful to think of the path as the full name of the file, especially when moving or renaming files from the command line.*

## Absolute paths:
- Always start with a leading slash, `'/'`.
- Are relative to the root directory of the file system.
- The root directory is the highest-level directory in the file system's tree structure. When we refer to absolute paths, we are considering paths relative to the topmost path of the file system.

## Explore the Root Path
### Group Activity
In your terminal session, determine your current directory by using the `pwd` command (mnemonic: "print working directory"). What is the topmost directory in this path? What is the root of the file system?

Open the Finder and navigate to the root directory of your file system. You can do this by using the `⌘ + ⇧ + g` shortcut in Finder, typing `/` and clicking `Go`. Take a look at the contents of the root directory.

Now, back in your terminal, change your current working directory to the root of the file system using the `cd` command (mnemonic: "change directory"). What happens if you type `cd` and then press the "Return" or "Enter" key? Let's wait before answering that question.

To change to the root directory, type `cd /`. In this case, we are providing the `cd` command with an absolute path. You can confirm that you are in the root directory by using the `pwd` command.

To return to your home directory, you can type `cd ~`, `cd $HOME`, or simply `cd`. Give it a try!

## Relative Paths
Relative paths are paths described in relation to the current working directory. To determine the current working directory, we use the `pwd` command.

For example, if I'm in my home directory and I see a folder named "projects" (how would I see that?), I can guess that the full path to the "projects" folder is `/Users/Zomia/projects`. However, since I'm already in the home folder, the `ls` command only shows me the unique part of the name that distinguishes it from other sibling directories. Sibling directories are directories that exist beside other directories, rather than within them (child directories) or above them (parent directories).

This "partial path" is a relative path. It is quite useful because I can use it to change into the directory by using the `cd projects` command. So, in addition to accepting absolute paths, the `cd` command can also take relative paths to navigate through the file system. Pretty cool!


#### There are two special relative directories.

- `..` represents the parent directory.
- `.` represents the current directory.

So, in order to navigate to a grandparent directory (parent of a parent) from the current directory, we would use the command `cd ../..`.

## Tab Complete
File paths can be long and typing them manually can be time-consuming and error-prone. Luckily, your terminal has a feature called tab completion that helps you fill in file and directory names. It works similar to autocorrect on a smartphone, but you need to press the tab key to trigger it.

Tab completion works with both relative and absolute paths. For example, if I have a file named `a-very-very-long-filename.txt` in my current working directory, I can type `a-v` (the first few letters of the filename) and press tab, and it will complete the filename for me.

Let's say I want to type the absolute path to that file, which is `/Users/Zomia/trainings/a-very-very-long-filename.txt`. I can do that quickly with tab completion! I could type `/U`, then press tab, then `G` and tab again, then `t` or `tr` and press tab, then `a-v` or `a-`, just like above.

Not only is this faster, but it also helps you verify if the file or directory you're looking for actually exists, preventing common mistakes. If you try to tab complete a non-existing file or directory, nothing will happen. So, whenever possible, make use of tab completion!

## Make a Subdirectory
### Group Activity
Now that we're back in the home directory, let's create a place to store all the work we'll do in this course. Naming can be challenging, but simple names are best.

Before executing the command in the terminal, bring your explorer window into focus, the one with the home directory open. Resize and position it so that it's visible alongside the terminal. Now, in the terminal, use `cd` to navigate to your `Home` directory.

Use the `mkdir` command to create a new directory called `web-dev`. 

Create the following directories as well. They should be subdirectories of `web-dev`:

- practices
- projects
- tmp
- challenges
- studies

Verify that your directory structure resembles the following:

```sh
~/web-dev
├── challenges
├── projects
├── studies
├── practices
└── tmp
```

Now that we have our `web-dev` directory set up, let's use the `mv` command to move some files into it.

Find where the `command-line` and `local-setup` directories are stored (they may be in the Desktop directory). Then move those directories into the `trainings` directory.

## Files
Let's use the `tmp` directory to experiment. `tmp` directories are conventionally used to store files that can be safely deleted. You should never put anything in them that you want to keep.

## Create/Edit a File
### Group Activity
Move into the `tmp` directory inside `web-dev`. Create a new file using the `touch` command. Let's create a blank text file named `name.txt`: `touch name.txt`.

Next, open that file in VSCode: `code name.txt`. Write your name inside this file and save it. On a Mac, the shortcut to save a file is `⌘ + s`, or `ctrl + s` on Linux. You can also search for the save command (or any command) using the command palette. Try it by bringing up the palette with `⌘ + ⇧ + p` (ctrl + shift + p on Linux). Then search for "Save".

Let's quickly take a peek inside the file we just created in our terminal. Type `cat name.txt`.

Now type `open name.txt` (`xdg-open name.txt` on Linux).

See what happened? The file `name.txt` opens in the default application your computer uses for that file type.

Let's say that we didn't mean to name the file `name.txt`. How would we go about editing the file name to correct it?

## Copying a Hidden File
### Bonus Topic: Group Activity
Hidden files in your file system are denoted by a leading dot (`.`). You can see these files using the command `ls -a`. Create a hidden file named `.env`. Copy this file to a new file named `.newEnv` using the command `cp <original_name> <new_name>`. Check your work by typing `ls -a`.

## Deleting a File
### Bonus Topic
How do we get rid of this file? We'll use the `rm` command. But first, a warning. This is a very dangerous command. Do not press enter after typing `rm` without being absolutely certain you're targeting the right file. There's no way to recover files deleted with `rm`. The same advice applies double to flags like `-r` or other flags. Flags are options that occur after dashes when issuing commands.

To delete a file or directory, use the following command:


`rm -r <file_or_directory> # Will delete all files inside a folder as well as folder`

## Delete a File
### Group Activity
Read the manual entry for `rm`. When you're done reading, you can quit by pressing `q`. Delete the `name.txt` file you created in the previous exercise. Type the command, then check with a colleague before pressing issuing the command.

#Important Note: Closing Your Terminal#
You shouldn't close your terminal by clicking the "X" button. This can leave processes from that terminal session running in the background which can cause problems in the future. Instead, you should use a keyboard shortcut to safely and completely end the terminal session.

On macOS you should first press `CTRL + D` in any tabs that are running continuous processes like servers, then press `CMD + Q`.

On Ubuntu you should use `CTRL + D`. Note that this only is only possible when no process is running in the terminal -- you can end almost any process and clear any entered text with `CTRL + C`.

