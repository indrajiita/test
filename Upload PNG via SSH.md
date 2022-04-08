# How to Upload Multiple PNG Images to Server via SSH

## Content

- 
-
-
-
-
-
-

## What is SSH?

SSH (Secure Shell Protocol) is a secure network protocol that creates a safe channel to transfer data. Sending files over SSH relies on the SCP (Secure Copy Protocol), which securely transfers files and folders between two machines.




, and ssh is the linux SSH client command.

SSH is the general protocol, and ssh is the linux SSH client command.



Does your version of Windows predate Windows 10? A third-party app is necessary to take advantage of SSH, as it only became native with that version. In cases like these, Putty is the most widely used SSH app for Windows. You can find it at https://www.putty.org/.

## Before you start




## Syntax

The location of the source file is specified by username1@source_host:directory1/filename1, which includes the:

Name of the account on the host computer (username1)
Hostname of the computer on which the source file resides (source_host)
Name of the directory containing the source file (directory1)
Filename of the source file (filename1)
The location to which the source file will be copied is specified by username2@destination_host:directory2/filename2, which includes the:

Name of the account on the destination computer (username2)
Hostname of the computer to which the source file will be copied (destination_host)
Name of the directory to which the source file will be copied (directory2)
Filename of the copy (filename2)

## Copy selected files

If you need to copy multiple PDF files from a location. Instead of copying the complete folder we can achieve this by specifying the required files in the same command separated by space. i.e, it should be like,



## Copy wildcard files

If you need to copy all PNG files from a folder, you can use an asterisc ( * ) as a wildcard, like this"


You can use wildcards to transfer multiple files in either direction, like this:

pscp c:\documents\*.doc fred@example.com:docfiles








scp source/file file2 file3 [user@server]/destination
If needed, it is also possible to copy from different locations. We just need to provide them in a space-separated list.

-------------


---------

5.2.1.3 source
One or more source files. Wildcards are allowed. The syntax of wildcards depends on the system to which they apply, so if you are copying from a Windows system to a UNIX system, you should use Windows wildcard syntax (e.g. *.*), but if you are copying from a UNIX system to a Windows system, you would use the wildcard syntax allowed by your UNIX shell (e.g. *).

If the source is a remote server and you do not specify a full pathname (in UNIX, a pathname beginning with a / (slash) character), what you specify as a source will be interpreted relative to your home directory on the remote server.

-----------

Copy multiple files from local to remote using scp.
$ scp myfile.txt myfile2.txt remoteuser@remoteserver:/remote/folder/

