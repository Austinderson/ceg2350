# File Systems
A [File System](Reference http://en.wikipedia.org/wiki/File_system) controls how information is stored and retrieved on a computer.
* Without a file system, information placed in a storage area would be one 
  large body of information with no way to tell where one piece of information
  stops and the next begins.
* Each separate collection of information is called a *file*. The structure and
  logic rules used to manage the collections of information and their names is
  called a *file system*.
* There are many different kinds of file systems, each having their own 
  structure, logic, or targeted storage medium.

### i-Node revisited
Although humans typically think of files (including directories) by their
names, the operating system does not.  Forthis course we will be using the term
*i-node* to refer to the concept of a unique identifier for a file.  Not all file
systems have i-nodes but they typically have a similar concept, for instance
NTFS, the file system used by windows has a file identifier or FileID for each
file that works in much the same fashion as an i-node.

An i-node store two pieces of information:
1. Meta-data, or information about the file's data (size, last modified time,
   whether the file is actually a folder, etc.)
2. Where exactly in the filesystem the file content is located (this file's data
   can be found in blocks 1455, 263, 7134, and 562)

When a file system is first created a table of inodes is created.  After this
point no new inodes can be allocated.  This table can be thought of as an array
having an *i-number* or array index an an *inode*.

For those paying a *very* close attention you might wonder "what happens if my
file needs more blocks than can be stored in my inode?".  Well that easy,
instead of a direct mapping to the data inodes can use indirect blocks of
storage to store the map to the data.  There can even be two or more layers of
indirect blocks, each indirect block only storing location information or where
the operating systems needs to fetch the files contents from.

![inode map to data][inode]

### Directories revisited
As previously mentioned directories perform two primary functions:
1. Organize files into a collection
2. Store file names and their associated i-number

Every file (including directories) has a parent directory.  This fails at the
top most directory (in linux referred to as root or just `/`) so we just make
the parent of `/` point to itself.

### Common File Systems
#### Linux
* ext3
* ext4
* zfs
* xfs
* nfs (network)
#### Windows
* ntfs
* smb/cifs (network)
#### MacOS
* HFS+ (old)
* APFS (new)
* AFP (network)
#### Portable storage media (USB)
* FAT32
* exFAT

A note on portable storage media.  Windows systems can use USB or other storage
devices with an NTFS file system just fine.  Using the same NTFS file system on
linux or mac introduces a problem.  I only listed FAT as a portable storage
medium because it is supported by most modern operating systems
(Windows/Mac/Linux).  This is due to it being old and mostly awful...  For
instance:
* FAT32 filesystems do NOT support file permissions
* FAT32 filesystems do NOT support files over 4GB in size
* FAT32 filesystems do NOT support filesystems over 32GB
Note: some operating systems have support for up to 2TB FAT file systems, but
not all do.

### Special File Systems and Files
In linux everything is a file!  To make it easier to get process related data
there exists a `/proc` file system.  The user can list and interact with process
inforamtion via a familiar file/filder structure.

What about devices?  Yep, files too.  Check out `/dev`.  Here you can find all
sorts of intersting devices:
* `/dev/input/mice` mouse input
* `/dev/nvidia0` nvidia graphics card (must have drivers installed)
* `/dev/sda` hard drive 
* `/dev/sda1` first partition on hard drive sda
* `/dev/random` and `/dev/urandom` are special files that output random data for
  use in other applications (often cryptography related)

### Links
A *link* is a reference to another file.  The most common link is a *symbolic 
link* also called a *symlink* or *soft link*.  A *symbolic link* is a new file
that contains a reference or path to another file.  This path is simply a text 
string containing the path to another file or directory that is automatically 
followed by the operating system.  This other file or directroy is called the
*target*.  In Windows soft links may sound like a *shortcut* but there are some
specific differences, primarily *shortcuts* are special types of files and 
require every program to understand a shortcut.  *Symbolic links* do not 
require any special knowledge on the part of the program but are instead handled
by the underlying file system (windows supports both *symbolic links* and
*shortcuts*).

Another type of link is a *hard link*.  A *hard link* is simply a directory
entry which associates a name and an i-node's i-number.  In linux, all files
must have at least one hard link specifying the name of a file. The term *hard
link* typically does not refer to this initial entry, but instead is used when a
file system supports more than one hard link for a given file.  By creating a
hard link you are giving one file multiple names (a different name/directroy
mapping to the same i-number).

![hard vs soft links][links]

These two types of links have some significant differences:
* Deleting a file that is hard linked in another location does NOT actually
  delete the data or free up the i-node (its still in use elsewhere).
* Deleting a symlink does not delete the file, but deleting a symlink target
  DOES delete the file AND leaves a hanging symlink somewhere.
* A Hard link cannot be created for a *directory*, if that were allowed it would
  break the parent structure (directories contain a link to their parent, if a
  directory were hard linked it could have two different parents, which would
  break things)
* A hard link cannot span file systems.  Since a hard link is created by
  storing the same i-number under a different name (possibly in a different 
  directory), a hard link spanning two different file systems would actually
  reference two different files.
* A soft link can span multiple file systems so long as they are still
  accessible via the path stored in the soft link.

[inode]: http://www.linux-mag.com/s/i/articles/8658/Ext2-inode.gif
[links]: https://mlvnt.com/img/posts/links/links_diagram.png

