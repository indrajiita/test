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

For more about scp and ssh, see its manual page

man scp
man ssh


, and ssh is the linux SSH client command.

SSH is the general protocol, and ssh is the linux SSH client command.



Does your version of Windows predate Windows 10? A third-party app is necessary to take advantage of SSH, as it only became native with that version. In cases like these, Putty is the most widely used SSH app for Windows. You can find it at https://www.putty.org/.

## Before you start




## Syntax

To specify the location of the source files, use the following syntax:

`source_user@source_host:source_directory/file1 file2`

- **source_user** is the name of the account on the host computer.
- **source_host** is the hostname of the computer on which the source file resides.
- **source_directory** is the name of the source directory containing.
- **file1**, **file2** are the source file names.

To specify location to which the source file will be copied, use the following syntax:

`dest_user@dest_host:dest_directory/newfile1 newfile2`

- **dest_user** is the name of the account on the destination computer.
- **dest_host** is the hostname of the computer to which the source file will be copied.
- **dest_directory** Name of the directory to which the source file will be copied ()
- **newfile1**, **newfile2** are the copy file names.

?????? Omitting the filename from the destination location copies the file with the original name. If you want to save the file under a different name, you need to specify the new file name.


## Copy selected files

To copy multiple the `map.png` and `screenshot.png` files from a location, specify the files separated by space.

scp -r dvader@deathstar.com:~/revenge ~/revenge


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

