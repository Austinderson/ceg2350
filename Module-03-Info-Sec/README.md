# Information Security
Information Security (often shortened to InfoSec) is the practice of defending
information from unauthorized access, use, disclosure, disruption, modification,
recording, or destruction.

How do we defend information?  Enter the CIA triad.

![The CIA Triad][cia]

The three tenets of the CIA triad are:
* Confidentiality
* Integrity
* Availability

### Confidentiality
To keep confidential means to keep something secret.  Confidentiality in terms
of information security is the process of allowing data to be read ONLY by those
whow are allowed to read it.  There are three main tools for keeping files and
data confidential:
* File Permissions
* Access Control Lists
* Encryption

#### File Permissions
> In Linux and Unix, everything is a file. Directories are files, files are files
> and devices are files.  All of the files on a system have permissions that allow
> or prevent others from viewing, modifying or executing. If the file is of type
> Directory then it restricts different actions than ordinary files and device
> files.   The super user "root" has the ability to access any file on the system.
> Each file has access restrictions with permissions, user restrictions with
> owner/group association. Permissions are referred to as bits. From [the Ubuntu
> page on File Permissions](https://help.ubuntu.com/community/FilePermissions).

There are three types of access restrictions: read, write, and execute.

There are also three types of user restrictions: User, Group, and All.

When running an `ls -l` of a directory we can see the permissions all the way on
the left.  Here is an example output of the above command:
```
drwxrwxr-x 2 mkijowski mkijowski 4096 Feb 10 20:35 sample-dir
-rw-rw-r-- 1 mkijowski mkijowski    0 Feb 10 20:34 sample-file
```

The permissions for these files are the first ten characters of each line and
are organized as follows:

The first bit identifies if the file in question is a directory `d`, or a
normal file `-`.

The next three bits are the read, write, execute bits for the owner of a file.
```
-rwx------
```

Followed by the read, write, execute bits for the group,
```
----rwx---
```

Which are then followed by the read, write execute bits for all users on the
system,
```
-------rwx
```

Going back to our original example, seeing that the both `sample-file` and
`sample-dir` are owned by the user mkijowski and the group mkijowski gives us
the following:
```
drwxrwxr-x 2 mkijowski mkijowski 4096 Feb 10 20:35 sample-dir
```
`sample-dir` is a directory `d`.  The user mkijowski and all members of the
group mkijowski all have read, write, and execute permisions, and every other
user on the system has only read and execute permissions.

#### Access Control Lists
Both Windows and Linux support using file permissions via Access Control Lists
(ACL).  ACL's offer a more fine-tuned approach to assigning permissions by
allowing for mor ethan one user and group to be assigned to each file.  You can
think of an ACL as a table of two columns, a list of users and groups each with
a corresponding permission set.

#### Encryption
Data encryption translates data into another form, or code, so that only people
with access to a secret key can read it (by decrypting it).  The key can take
several forms including a password, or a special file created via an algorithm.

There are two types of encryption:
* Symmetric encryption uses the same key for both the encryption and decrpytion
  process.
* Asymmetric encryption uses different (but related) keys for encryption and
  decryption

Symmetric key example: we can encrpyt an arbitrary file with the gpg program.
`gpg -c filename` will prompt the user for a password that will be used to
encrypt the data in `filename`.  We can then decrypt the data with `gpg
filename`.

Asymmetric key ilustration:
![Asymmetric key example][pki]

### Integrity
We may know the the standard definition of integrity: the quality of being
honest.  In computing integrity involves maintaining the consistency and
trustworthiness of data, or in other words trusting that our data has not been
tampered with.  While we can hope that our access controls are enought to
protect our data from unwanted writes, we need a way to validate that the data
has not been changed.  Enter checksums.

#### Checksums (hashes)
A checksum is a fixed-size piece of information that is the result of data being
put through a checksum function.  A good checksum function will output a
drastically different value with only a minor change to the input.  A simple way
to tell if a file has been changed is to check its current checksum against the
checksum of the file in a trusted state.  If the checksums are different, the
file has been changed.

Checksums operate on a files data, which does not include either the file name,
location on the file system, or any of the files meta-data.

While great for verifying whether a file has been tampered with, a checksum
alone does not guarantee authenticity of a file (who the file actually came
from).  For that we need to combine some of our tools.

#### Digital signature
![Digital Signature][digital signature]

### Availability
Ensuring authorized parties have access to information.  How?
* Redundancy
* Backups
* Redundancy


[cia]: https://upload.wikimedia.org/wikipedia/commons/9/9a/CIAJMK1209.png
[pki]: https://upload.wikimedia.org/wikipedia/commons/f/f9/Public_key_encryption.svg
[digital signature]: https://upload.wikimedia.org/wikipedia/commons/a/a7/Private_key_signing.png
