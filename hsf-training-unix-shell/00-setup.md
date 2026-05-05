# Summary and Setup

The Unix shell has been around longer than most of its users have been alive. It has survived because it’s a powerful tool that allows users to perform complex and powerful tasks, often with just a few keystrokes or lines of code. It helps users automate repetitive tasks and easily combine smaller tasks into larger, more powerful workflows.

Use of the shell is fundamental to a wide range of advanced computing tasks, including high-performance computing. These lessons will introduce you to this powerful tool.

```{admonition} HSF Training

This training module is part of the [HSF Training Center](https://hsf-training.org/training-center/), a series of training modules that serves HEP newcomers the software skills needed as they enter the field, and in parallel, instill best practices for writing software.
```

Copyright notice: This lesson is a derivative of the [carpentries](https://swcarpentry.github.io/shell-novice/index.html) lesson on the same topic. Currently, the main change is that we use jupyterbook.


::::::::::::::::::::::::::::::::::::::::::  prereq

## Prerequisites

This lesson guides you through the basics of file systems and the
shell. If you have stored files on a computer at all and recognize
the word "file" and either "directory" or "folder" (two common words
for the same thing), you're ready for this lesson.

If you're already comfortable manipulating files and directories,
searching for files with `grep` and `find`, and writing simple loops
and scripts, you probably want to explore the next lesson:
[shell-extras](https://carpentries-incubator.github.io/shell-extras/).


::::::::::::::::::::::::::::::::::::::::::::::::::

## Download files

You need to download some files to follow this lesson.

1. Download [shell-lesson-data.zip][zip-file] and move the file to your Desktop.
2. Unzip/extract the file.
  **Let your instructor know if you need help with this step**.
  You should end up with a new folder called **`shell-lesson-data`** on your Desktop.

## Install software

If you do not already have the shell software installed, you will need to
[download and install][install_shell] it.

## Open a new shell

After installing the software

3. Open a terminal.
  If you're not sure how to open a terminal on your operating system, see the instructions below.
4. In the terminal type `cd` then press the <kbd>Return</kbd> key.
  This step will make sure you start with your home folder as your working directory.

In the lesson, you will find out how to access the data files in this folder.

:::::::::::::::::::::::::::::::::::::::::  callout

## Where to type commands: How to open a new shell

The shell is a program that enables us to send commands to the computer and receive output.
It is also referred to as the terminal or command line.

Some computers include a default Unix Shell program.
The steps below describe some methods for identifying and opening
a Unix Shell program if you already have one installed.
There are also options for identifying and downloading a Unix Shell program,
a Linux/UNIX emulator, or a program to access a Unix Shell on a server.

If none of the options below address your circumstances,
try an online search for: Unix shell [your computer model] [your operating system].


::::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::: solution

### Windows

Computers with Windows operating systems do not automatically have a Unix Shell program
installed.
In this lesson, we encourage you to use an emulator included in [Git for Windows][install_shell],
which gives you access to both Bash shell commands and Git.

Once installed, you can open a terminal by running the program Git Bash from the Windows start
menu.

**For advanced users:**

As an alternative to Git for Windows you may wish to [Install the Windows Subsystem for Linux][wsl]
which gives access to a Bash shell command-line tool in Windows 10 and above.

Please note that commands in the Windows Subsystem for Linux (WSL) may differ slightly
from those shown in the lesson or presented in the workshop.

::::::::::::

:::::::::::: solution

### MacOS

For a Mac computer running macOS Mojave or earlier releases, the default Unix Shell is Bash.
For a Mac computer running macOS Catalina or later releases, the default Unix Shell is Zsh.
Your default shell is available via the Terminal program within your Utilities folder.

To open Terminal, try one or both of the following:

- In Finder, select the Go menu, then select Utilities.
  Locate Terminal in the Utilities folder and open it.
- Use the Mac 'Spotlight' computer search function.
  Search for: `Terminal` and press <kbd>Return</kbd>.

To check if your machine is set up to use something other than Bash,
type `echo $SHELL` in your terminal window.

If your machine is set up to use something other than Bash,
you can run it by opening a terminal and typing `bash`.

[How to Use Terminal on a Mac][mac-terminal]

::::::::::::

:::::::::::: solution

### Linux

The default Unix Shell for Linux operating systems is usually Bash.
On most versions of Linux, it is accessible by running the
[Gnome Terminal][gnome-terminal] or [KDE Konsole][kde-konsole] or [xterm],
which can be found via the applications menu or the search bar.
If your machine is set up to use something other than Bash,
you can run it by opening a terminal and typing `bash`.



::::::::::::

:::::::::::::::::::::::::::::::::::::::::  callout
 
## SSH Access to the CMS LPC (cmslpc)
 
The CMS LPC (LHC Physics Center at Fermilab) provides access to the **cmslpc cluster**,
which is widely used for CMS data analysis.
 
Before connecting, make sure you:
* Have a valid **Fermilab (FNAL) account**
* Have access to the **cmslpc cluster**
* Have **Kerberos configured** on your machine
> Account setup can take time, so request access early.
 
### 1. Authenticate with Kerberos
 
CMS LPC uses **Kerberos authentication**, not simple password SSH.
 
```bash
kinit <YOUR_USERNAME>@FNAL.GOV
```
 
* Enter your FNAL password when prompted
* This gives you a valid ticket (~24 hours)
### 2. Connect via SSH
 
Once authenticated, log in with:
 
```bash
ssh -Y <YOUR_USERNAME>@cmslpc-el9.fnal.gov
```
 
* `-Y` enables X11 forwarding (useful for GUIs)
* If successful, you will see a welcome message and a shell prompt
### 3. Typical First Commands
 
```bash
# go to your working area
cd ~/nobackup
 
# create a working directory
mkdir my_work
cd my_work
```
 
### 4. Recommended SSH Config (Optional)
 
To simplify login, add this to your `~/.ssh/config`:
 
```bash
Host cmslpc
    HostName cmslpc-el9.fnal.gov
    User <YOUR_USERNAME>
    ForwardX11 yes
```
 
Then you can simply run:
 
```bash
ssh cmslpc
```
 
### 5. Notes & Tips
 
* You must renew your Kerberos ticket daily:
  ```bash
  kinit <YOUR_USERNAME>@FNAL.GOV
  ```
* If login fails, common issues are:
  * Expired Kerberos ticket
  * Incorrect SSH/Kerberos config
  
::::::::::::::::::::::::::::::::::::::::::::::::::



[zip-file]: data/shell-lesson-data.zip
[install_shell]: https://carpentries.github.io/workshop-template/install_instructions/#shell
[wsl]: https://learn.microsoft.com/en-us/windows/wsl/install
[mac-terminal]: https://www.macworld.co.uk/feature/mac-software/how-use-terminal-on-mac-3608274/
[gnome-terminal]: https://help.gnome.org/users/gnome-terminal/stable/
[kde-konsole]: https://konsole.kde.org/
[xterm]: https://en.wikipedia.org/wiki/Xterm
