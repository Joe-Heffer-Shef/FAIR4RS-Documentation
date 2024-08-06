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

### Advantages of CLIs for research tools

Command lines are a way of interacting with a digital system that go back to the early history of computing. They might seem old-fashioned because typing out commands means that there is no graphical component. It may seem restrictive because your mouse isn't used, but terminals have a lot of power because we can formulate our instructions to the computer by writing commands. We have a direct line to control our computer's operating system.

It's a great way to talk to your computer because you can record the commands that you've run to provide a documented history of a research process. (We could record a video screen capture of your working procedure, but that's much less efficient.)

Terminals are more efficient for running repetitive tasks and provide extra functionality for advanced users. They are an cost-effective way to provide a user interface for research software, as research teams often lack the resources and know-how to produce sophisticated graphical user interfaces.

## Using the terminal

There's a lot of powerful commands that can be learned to take full advantage of the command line, but here we'll just address the basics to help us make our research software easier to use by providing a well-documented CLI.

This section will briefly introduce you to using the terminal to achieve simple tasks. For an an in-depth course on using the command line, please study the [The Unix Shell](https://swcarpentry.github.io/shell-novice/) Software Carpentry course.

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

When using shell commands, we use the words **option**, **flag**, and **arguments** to describe **parameters** that we can use to modify the operation of that command and the inputs used to initialise our code.

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

We can add a command-line interface to our Python code using the methods and tools that are included in the Python programming language.

### Getting started

Let's continue working on our birdsong identification software project and create an entry-point to our code.

To create an executable script that will run from the command line, create a file called `oddsong/__main__.py`.
When a user runs our code from the terminal, this `__main__.py` file will be executed first.

:::::::::::::::::::::::::::::::::::::::::: spoiler

### Why must our file be named `__main__.py`?

This is a mechanism that tells Python how we want users to interact with our software.

To find out more, please read the [\_\_main\_\_.py](https://docs.python.org/3/library/__main__.html#main-py-in-python-packages) section in the Python documentation.

To run our code *as a script* we use the Python `-m` option that runs a module as a script. 

```bash
python -m oddsong
```

This will execute the `oddsong` module by running our `oddsong/__main__.py` file.

::::::::::::::::::::::::::::::::::::::::::::::::::

:::: challenge

Let's check if this works by writing a simple `print()` command in the `__main__.py` script.

```python
# Show the text on the screen
print("Hello, world!")
```

Add this `print` statement to `__main__.py`. Run this script from the command line. What happens when you run `python -m oddsong`?

::: solution

When you run the `python -m oddsong` command, Python runs the *main module as a script*.

You should see the following output in your terminal.

```bash
$ python -m oddsong
Hello, world!

```

:::

::::

### `main()` functions

`main` functions are used to as the primary "starting point" for a command-line interface, otherwise known as an "entry point" for our scripted sequence of commands.

Inside this file, create a function called `main()` and an `if` statement as shown below.

```python
def main():
    print("Identifying bird vocalisation...")

if __name__ == "__main__":
    main()
```

When the user executes our CLI, Python will know to run the `main()` function and execute our research code. In this case, our research code hasn't been written yet, so we'll just show a message on the screen for now.

The logical statement `if __name__ == "__main__"` means that the `main()` function will *only* run when the code is run from the comand line as the [top-level code environment](https://docs.python.org/3/library/__main__.html#what-is-the-top-level-code-environment).

### CLI documentation

Python has a useful inbuilt module called [argparse](https://docs.python.org/3/howto/argparse.html) to quickly create a command line interface that follows the standard conventions of the Linux software ecosystem.

To get started, attempt the challenge below.

:::: challenge

In this exercise, we'll create an instance of the [argument parser](https://docs.python.org/3/howto/argparse.html#the-basics) tool. Let's edit our Python script.

First, load the `argparse` library using the [`import` keyword](https://docs.python.org/3/reference/import.html), which is conventionally done at the top of the script. Then, we'll add the argument parser to our `main()` function so it loads when the script runs.

```python
import argparse

def main():
    # Define command-line interface
    parser = argparse.ArgumentParser()
    parser.parse_args()

    print("Identifying bird vocalisation...")

if __name__ == "__main__":
    main()
```

This creates a basic command line interface. Let's try it out.

```bash
python -m oddsong
```

What do expect to see? What actually happens?

Now let's ask for help! Run the following command to view the usage instructions:

```bash
python -m oddsong --help
```

What should we see when using the `--help` flag? What happens in your temrinal?

::: solution

When we run our script as before, it will run like normal with no change in behaviour.

```bash
$ python -m oddsong
Identifying bird vocalisation...
```

But, if we invoke the command-line interface using any *arguments*, then this new functionality kicks in.

```bash
$ python -m oddsong --help
usage: test.py [-h]

options:
  -h, --help  show this help message and exit
```

This is the default output of a CLI with no additional arguments specified. The first line displays the usage instructions. This means that we may execute `test.py` with an optional help option using `--help` or `-h`  for short. Optional flags are denoted with square brackets like this `[-h]`.

:::

::::

The `parse_args()` method runs the parser and makes our arguments available to the user on the command line. This makes the default `--help` flag available which displays instructions and notes that we can customise. As we continue to develop our CLI by adding arguments, each one will be listed and described in this help page. This is an excellent way to document our software and make it available to researchers!

#### Arguments

But what if we want to take an input from the user? We add arguments to our CLI using the following syntax.

```python
# Add the category argument
parser.add_argument('-c', '--category')
```

This will create an argument called `args.file` that the user can specify when they run our script, and that we can use in our code to do something useful.

:::: challenge

Add this argument to our script and note the changes to the user interface.

::: solution

The code now looks something like that shown below.

```python
import argparse

def main():
    # Define command-line interface
    parser = argparse.ArgumentParser()
    parser.add_argument('-c', '--category')
    parser.parse_args()

    print("Identifying bird vocalisation...")

if __name__ == "__main__":
    main()
```

Note that we add the argument *before* we parse them, which makes them available to use.

Now, when we invoke the help screen, we see our new "category" argument listed.

```bash
$ python -m oddsong --help
usage: oddsong.py [-h] [-c CATEGORY]

options:
  -h, --help            show this help message and exit
  -c CATEGORY, --category CATEGORY
```

The layout of this text is done for us and follows the standard conventions of terminal tools.

:::

::::

Of course, if you've imbibed the spirit of the course, you'll notice that our new category parameter is completely undocumented! It's unclear what it is or how to use this option.

#### Argument descriptions

To provide a concise explanation for each parameter we use the `help` argument of the [`add_argument()` function](https://docs.python.org/3/library/argparse.html#the-add-argument-method) as shown below.

```python
# Add the category argument
parser.add_argument('-c', '--category', 
    help="The type of bird call e.g. alarm, contact, flight")
```

This text should briefly describe the purpose of the argument, without going into too much detail (which should be covered in the user guide.)

:::: challenge

Add a description of the `--category` argument using the `add_argument()` function. What change do you expect to happen in your CLI?

::: solution

We can achieve this in our example script by adding a `help` string.

```python
import argparse

def main():
    # Define command-line interface
    parser = argparse.ArgumentParser()
    parser.add_argument('-c', '--category',
        help="The type of bird call e.g. alarm, contact, flight")
    parser.parse_args()

    print("Identifying bird vocalisation...")

if __name__ == "__main__":
    main()

```

Now, when we call the `--help` option, we see this description as an annotation to that argument.

```bash
$ python -m oddsong --help
usage: oddsong.py [-h] [-c CATEGORY]

options:
  -h, --help            show this help message and exit
  -c CATEGORY, --category CATEGORY
                        The type of bird call e.g. alarm, contact, flight
```

:::

::::

There's [a lot more to learn](https://docs.python.org/3/howto/argparse.html) about command line arguments, including several powerful features of the `argparse` library, but these are beyond the scope of this course.

#### Description

We can provide a simple summary of the software that will be displayed on the `--help` screen of our CLI by using the [`description` argument](https://docs.python.org/3/library/argparse.html#description) when creating our argument parser object. This should concisely inform the user about the purpose of the tool and how it works.

```python
# Describe the software
parser = argparse.ArgumentParser(
    description="A tool to identify bird vocalisations.")
```

:::: challenge

Write your own description for our software. Where does it display on our help screen?

::: solution

We define the description when creating our argument parser object.

```python
import argparse

def main():
    # Define command-line interface
    parser = argparse.ArgumentParser(
        description="A tool to identify bird vocalisations.")
    parser.add_argument('-c', '--category',
        help="The type of bird call e.g. alarm, contact, flight")
    parser.parse_args()

    print("Identifying bird vocalisation...")

if __name__ == "__main__":
    main()

```

This text is displayed after the usage instruction.

```bash
$ python -m oddsong --help
usage: oddsong.py [-h] [-c CATEGORY]

A tool to identify bird vocalisations.

options:
  -h, --help            show this help message and exit
  -c CATEGORY, --category CATEGORY
                        The type of bird call e.g. alarm, contact, flight
```

:::

::::

#### Usage

By default, the usage message is generated automatically based on the arguments of our script. For our example, the usage instructions look like this:

```
usage: oddsong.py [-h] [-c CATEGORY]
```

In most cases, this will do the job. If you want to overwrite this message then use the [`usage` parameter](https://docs.python.org/3/library/argparse.html#usage) when creating the argument parser object.

There are several [other options](https://docs.python.org/3/library/argparse.html#argparse.ArgumentParser) to customise your CLI, but we've covered here the primary ways to document your research software to make it easier to use by your collaborators and other researchers.

::::::::::::::::::::::::::::::::::::: keypoints 

- Command line interfaces (CLIs) are terminal commands that provide an easy-to-use entry point to a software package.
- Researchers can use CLIs to make their research code easier to use by providing well-documented options, hiding the complexity of the software.
- Most programming languages offer frameworks for creating CLIs. In Python, we do this using the `argparse` library.

::::::::::::::::::::::::::::::::::::::::::::::::

## Further resources

To find out more about command-line interfaces and using the terminal to improve your productivity for research computing, please refer to the following resources:

- Learn more about using the terminal in the Software Carpentry [Unix Shell](https://swcarpentry.github.io/shell-novice/) course.
- There are Python packages such as [Click](https://click.palletsprojects.com/) that provide a framework for building bigger, more complex command-line interfaces.
- To learn about distributing your CLI so others can easily install and use it, please see the packaging module in this course series.
