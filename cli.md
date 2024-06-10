---
title: 'Command line interfaces'
teaching: 10
exercises: 2
---

:::::::::::::::::::::::::::::::::::::: questions 

- What is a command-line interface (CLI)?
- Why are they useful for making software easier to use for researchers?
- How do I create a <acronym title="command-line interface">CLI</acronym> for my research code?

::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::: objectives

- Learn what a command-line interface is
- Understand the benefits of <acronym title="command-line interfaces">CLIs</acronym>  for making research code more accessible?
- Gain a basic familiarity with the `argparse` module in Python

::::::::::::::::::::::::::::::::::::::::::::::::

## Command line interfaces

A command-line interface, usually abbreviated to CLI, is a terminal or prompt that accepts text input that instructs a computer what to do. They are used to start programs and perform actions within the computer's operating system.

In this section, we'll introduce the concept of providing a command-line interface to our research code to make it easier to use and provide a well-documented "entry point" to our software.

### Advantages

Command lines are a way of interacting with a digital system that go back to the early history of computing. They might seem old-fashioned because typing out commands means that there is no graphical component. It may seem restrictive because your mouse isn't used, but terminals have a lot of power because we can formulate our instructions to the computer by writing commands. We have a direct line to control our computer's operating system.

It's a great way to talk to your computer because you can record the commands that you've run to provide a documented history of a research process. (We could record a video screen capture of your working procedure, but that's much less efficient.)

Terminals are more efficient for running repetitive tasks and provide extra functionality for advanced users. They are an cost-effective way to provide a user interface for research software, as research teams often lack the resources and know-how to produce sophisticated graphical user interfaces.

## Using the terminal

There's a lot of powerful commands that can be learned to take full advantage of the command line, but here we'll just address the basics to help us make our research software easier to use by providing a well-documented CLI.

For an introduction to using the command line, please study the [Unix Shell](https://swcarpentry.github.io/shell-novice/) Software Carpentry course.

### How to open the command line

Each operating system has a slightly different terminal interface, but they work in basically the same way.

::: group-tab

### Windows

On Windows operating systems, press the Windows key and type in "command". The start menu will find the "Command Prompt" app. Press <kbd>Enter</kbd> or click on the Command Prompt icon to launch the terminal.

You can also launch the command prompt by pressing <kbd>Windows + R</kbd> and typing `cmd`.

The command prompt tool will open a black terminal window that looks something like this:

```bash
Microsoft Windows [Version 10.0.19045.4412]
(c) Microsoft Corporation. All rights reserved.

C:\Users\bob>
```

For more information, see the [Windows Commands](https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/windows-commands) page on the Windows Server documentation.

### Linux

On Ubuntu, press <kbd>Ctrl + Alt + T</kbd> to open a terminal.

You can also open Dash and search for "Terminal". For detailed instructions, please read [Opening a terminal](https://ubuntu.com/tutorials/command-line-for-beginners#3-opening-a-terminal) section in the [The Linux command line for beginners](https://ubuntu.com/tutorials/command-line-for-beginners#1-overview) tutorial in the official Ubuntu documentation.

The terminal on an Ubuntu computer will look something like this, where the dollar sign `$` means "type here".

```bash
bob@myUbuntuPC:~$
```

### Mac OS

Please read [Open or quit Terminal on Mac](https://support.apple.com/en-gb/guide/terminal/apd5265185d-f365-44cb-8b09-71a064a42125/mac) on the [Terminal User Guide](https://support.apple.com/en-gb/guide/terminal/welcome/mac) for macOS.

:::

### Example commands

An example of a CLI command is a simple text command that performs some action or interacts with the computer operating system. 

Let's examine a simple one-word command that lists the files in the current directory.

::: group-tab

### Windows

On Windows, the [dir](https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/dir) command is used to list the contents of a directory. When you enter this command and press <kbd>Enter</kbd>

```bash
> dir
```

The result of this command will be printed to the screen.

```output
C:\temp\my_data>dir
 Volume in drive C has no label.
 Volume Serial Number is Y72W-9DA1

 Directory of C:\temp\my_data

30/05/2024  14:06    <DIR>          .
30/05/2024  14:06    <DIR>          ..
30/05/2024  14:06                12 README.txt
               1 File(s)             12 bytes
               2 Dir(s)  171,395,805,184 bytes free
```

This means that in the folder `C:\temp\my_data` there is a single file called `README.txt`. The date and time that each file was last modified is shown, along with the file size, which is 12 bytes in this case.

### Linux

To show the contents of a directory on a Linux system, we use the [`ls` command](https://manpages.ubuntu.com/manpages/noble/man1/ls.1plan9.html) which lists information about the files in the current location.

```bash
bob@myUbuntuPC:/tmp/my_data$ ls
```

The output is a simple list of the names of all the files in that folder.

```output
README.txt
```

### Mac OS

The macOS terminal is very similar to the Linux one. To show the contents of a directory on a Linux system, we use the [`ls` command](https://support.apple.com/en-gb/guide/terminal/apdb66b5242-0d18-49fc-9c47-a2498b7c91d5/2.14/mac/14.0) which lists information about the files in the current location.

```bash
ls
```

The output is a simple list of the names of all the files in that folder.

```output
README.txt
```

For more information, please read [Get started with Terminal on Mac](https://support.apple.com/en-gb/guide/terminal/pht23b129fed/mac)

:::

### Arguments

Commands have options that allow the user to choose what the tool will do.

:::::::::::::::::::::::::::::::::::::::::: spoiler

### What are arguments?

When using shell commands, we use the words option, flag, and arguments to describe parameters that we can use to modify the operation of that command.

::::::::::::::::::::::::::::::::::::::::::::::::::

::: group-tab

### Windows

In the Windows command line, we use the `/?` argument to instruct the computer to print the help information that that command. To see helpful reference information for using the `dir` command, run:

```bash
> dir /?
```

The result of this command will be printed to the screen.

```output
Displays a list of files and subdirectories in a directory.

DIR [drive:][path][filename] [/A[[:]attributes]] [/B] [/C] [/D] [/L] [/N]
  [/O[[:]sortorder]] [/P] [/Q] [/R] [/S] [/T[[:]timefield]] [/W] [/X] [/4]

  [drive:][path][filename]
              Specifies drive, directory, and/or files to list.

  /A          Displays files with specified attributes.
  attributes   D  Directories                R  Read-only files
               H  Hidden files               A  Files ready for archiving
               S  System files               I  Not content indexed files
               L  Reparse Points             O  Offline files
               -  Prefix meaning not
  /B          Uses bare format (no heading information or summary).
...
```

The output is a description of the `dir` command, instructions for using it, and a reference to each of the options or arguments available.

### Linux

In the Linux command line, we use the `--help` argument to instruct the computer to print the help information that that command. To see helpful reference information for using the `ls` command, run:

```bash
$ ls --help
```

The result of this command will be printed to the screen.

```output
Usage: ls [OPTION]... [FILE]...
List information about the FILEs (the current directory by default).
Sort entries alphabetically if none of -cftuvSUX nor --sort is specified.

Mandatory arguments to long options are mandatory for short options too.
  -a, --all                  do not ignore entries starting with .
  -A, --almost-all           do not list implied . and ..
      --author               with -l, print the author of each file
  -b, --escape               print C-style escapes for nongraphic characters
...
```

The output is a description of the `ls` command, instructions for using it, and a reference to each of the options or arguments available.


### Mac OS

In the macOS command line, we use the `--help` argument to instruct the computer to print the help information that that command. To see helpful reference information for using the `ls` command, run:

```bash
$ ls --help
```

The result of this command will be printed to the screen.

```output
Usage: ls [OPTION]... [FILE]...
List information about the FILEs (the current directory by default).
Sort entries alphabetically if none of -cftuvSUX nor --sort is specified.

Mandatory arguments to long options are mandatory for short options too.
  -a, --all                  do not ignore entries starting with .
  -A, --almost-all           do not list implied . and ..
      --author               with -l, print the author of each file
  -b, --escape               print C-style escapes for nongraphic characters
...
```

The output is a description of the `ls` command, instructions for using it, and a reference to each of the options or arguments available.

:::

## CLIs in Python

We can add a command-line interface to our Python code using the methods and tools that are included in Python programming language.

### Getting started

Let's continue working on our birdsong identification software project and create an entry-point to our code.

To create an executable script that will run from the command line, create a file called `oddsong/__main__.py`.
When a user runs our code from the terminal, this `__main__.py` file will be executed first.

:::::::::::::::::::::::::::::::::::::::::: spoiler

### Why must our file be named `__main__.py`?

This is a mechanism that tells Python how we want users to interact with our software.

To find out more, please read the [__main__.py](https://docs.python.org/3/library/__main__.html#main-py-in-python-packages) section in the Python documentation.

::::::::::::::::::::::::::::::::::::::::::::::::::

Let's check if this works by writing a simple `print()` command in the `__main__.py` script.

```python
print("Hello, world!")
```

Run your code

```bash
$ python -m oddsong
Hello, world!

```

### `main()` functions

`main` functions are used to as the primary "starting point" for a command-line interface, otherwise known as an "entry point" for our scripted sequence of commands.

Inside this file, create a function called `main()` and an `if` statement as shown below.

```python
def main():
    print("Identifying bird vocalisation...")

if __name__ == "__main__":
    main()
```

When the user executes our CLI, Python will know to run the `main()` function and execute our research code.

The logical statement `if __name__ == "__main__"` means that the `main()` function will *only* run when the code is run from the comand line as the [top-level code environment](https://docs.python.org/3/library/__main__.html#what-is-the-top-level-code-environment).

### CLI documentation

Python has a useful inbuilt module called [argparse](https://docs.python.org/3/howto/argparse.html) to quickly create a command line interface that follows the standard conventions of the Linux software ecosystem.

To get started, let's create an 

#### Description

#### Usage

#### options

Help text

#### Using CLIs

TODO

::::::::::::::::::::::::::::::::::::: keypoints 

- Command line interfaces (CLIs) are terminal commands that provide an easy-to-use entry point to a software package.
- Researchers can use CLIs to make their research code easier to use by providing well-documented options, hiding the complexity of the software.
- Most programming languages offer frameworks for creating CLIs. In Python, we do this using the `argparse` library.

::::::::::::::::::::::::::::::::::::::::::::::::