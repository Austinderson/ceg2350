## Lab 01 - Fantastic Files and how to hide them!
Please put all requested output in an file named `answers.txt`, make sure you
name, w#, and class section are the first three lines of this file!  If we have
not covered the content in class then you are expected to research the topic
on your own.

#### Files and links
You may perform the following in any Bash environment.
1. Determine the number of files and directories in `/usr/bin`.  *Hint: use
   `ls`, `wc`, and a pipe `|`.  You may need to use some options for these
   commands.  Rearch them with the `man` command.*  Please include the total
   number of files in `/usr/bin` as well as the command you used to find it.
2. Hard and Soft links.  Create 3 directories in your home directory: `D1`,
   `D2`, and `D3`.  Create a file named lisaRA.txt as follows:  
   `ls -lisaR > lisaRA.txt`.  Using `ln` create two links with the target
   `~/lisaRA.txt`.  The first link should be a hard link `~/D1/ls1.txt`
   and the second link should be a symlink `~/D2/ls2.txt`.  Finally, make a
   symlink `~/D3/ls3.txt` with target `~/D2/ls2.txt`.
   Explain the effects deleting `~/lisaRA.txt` has on each of the other three
   files in your `answers.txt`.  
   To test use the `rm` command.  Be careful when using `rm`!
3. Delete the `D1` `D2` and `D3` directories.  List the command you used in
   `answers.txt`

#### Permissions
Perform the following steps on the systems specified.
1. SSH into thor.cs.wright.edu and make sure you are in your home directory.
2. Create a text file named `myinfo.txt` with the following information on
   separate lines: your name, your date of birth, your mothers maiden name, the
   password to your bank account, any two of your credit card numbers... you
   know what, just put the word `TOP SECRET`after your name and leave the rest
   out.
3. Please be sure you did NOT actually put any private information (besides your
   name) in `myinfo.txt`...
4. Pretend like you DID put private information in `myinfo.txt`.  Use the
   `chmod` command to make sure that ONLY you can read this information.  Verify
   with `ls`.  Paste the commands and output used in this step to your
   `answers.txt`.
5. Using WinSCP.exe on windows (or any sftp application in windows), make a 
   connection to `thor.cs.wright.edu` and pull down your `myinfo.txt`.  Is it
   still secure?  Why or why not?  Would transferring via a USB drive formatted
   with the FAT file system been any different?

#### The CIA
Included in this folder is a top secret file.  To ensure the integrity of this
file, prior to uploading I used `md5sum` on this file to generate a hash:
```
$ md5sum top-secret-document.md 
debe5c32ecbb350eceda7ac8f24b36ed  top-secret-document.md
```
Answer the follwoing in your `answers.txt`:
1. Has this file been tampered with since I created this hash?  How did you 
   verify this.
2. If it has/had been tampered with, could you tell what was changed given the
   md5sums before and after the tampering?  Why or why not?
3. Using the `gpg` encryption program, encrypt your myinfo.txt file.  Record
   the command used in your `answers.txt` file.  Would you be more comfortable
   transferring this file?  Why or why not?

