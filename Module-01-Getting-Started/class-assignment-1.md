## Getting familiar with linux.
In our first class we covered the [Bandit wargame from OverTheWire.org](http://overthewire.org/wargames/bandit/).
The purpose of this exercise was to familiarise students with connecting to a 
remote computer using the `ssh` command.  The bandit wargame then presents a
series of challenges in the form of levels.  To progress to the next level 
students must use the hints given to find the key (password) for the next level.

Connect to bandit with the following command:
```
ssh -p 2220 bandit0@bandit.labs.overthewire.org
```
Breaking down this command, we are using the SSH `ssh` application to make a 
connection over network port 2220 `-p 2220`, and attempting to login as user 
bandit0 on the server name given `bandit0@bandit.labs.overthewire.org`.  
More information about the SSH program and other options it supports can be
found using `man ssh`.
