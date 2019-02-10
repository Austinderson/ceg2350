# CEG-2350 Development Toolchain
This document outlines the recommended tools for students working in CEG-2350.

The basic tools consist of a linux shell, an SSH client, a SFTP client, the Git
version control system, and a linux VM where the student has root privileges 
(is an administrator).

## Bash (Linux Shell)
Most any linux shell will do, but the student will be responsible for
transposing all commands if they chose a shell other than [Bash](https://en.wikipedia.org/wiki/Bash_(Unix_shell)).
If you are using linux or MacOS the built in shell should be bash-like enough
for most of this class.  
Windows users can install Bash using the Windows Subsystem for Linux.
Instalation instructions can be found [here.](https://docs.microsoft.com/en-us/windows/wsl/install-win10)

## Secure Shell (SSH)
SSH provides and an encrypted secure channel over an otherwise unsecured
network.  The most commong application to use over this tunnel is a shell (bash
or similar) but any network service can be secured over SSH.

In this course we will be using SSH to connect to remote servers to perform
labs.  If you have a Bash shell installed SSH should already be installed and
can be tested with `man ssh` inside of bash.

If you would prefer a windows client for making SSH connections you can choose
one of the following:
* Putty: a graphical ssh client that works well enough and is installed in most
  of our labs.  You can [download putty here](https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html).
* SSH for windows: There is now a beta ssh client for windows that can be used
  from within PowerShell.  [Find out more here](https://www.howtogeek.com/336775/how-to-enable-and-use-windows-10s-built-in-ssh-commands/)

## SFTP (secure file transfer protocol)
Similar to ssh, if you have bash installed you likely have sftp installed as
well.  We will be using sftp to transfer files between computers.
* [WinSCP](https://winscp.net/eng/index.php) is a somewhat good file transfer
  application that has a GUI and supports SFTP transfers.

## Git
To install Git in windows download it from [here](https://git-scm.com/download/win).
To install git in linux run one of the following commands:
* For Debian based systems (most common, includes ubuntu): `sudo apt install git`
* For Red Hat based systems: `yum install git`

## Campus VPN
In order to access WSU systems from home you will need the campus VPN.  Instructions to install it can be found on the [CaTS vpn website](http://www.wright.edu/information-technology/security/virtual-private-networks-software-overview).
Before attempting to SSH into thor.cs.wright.edu from off campus, be sure to start the VPN client and follow all instructions to make a secure connection to campus.

## Amazon Web Services (AWS)
Work in progress.
