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

To learn more about scp and ssh, run the following commands respectively:

`man scp`
`man ssh`


, and ssh is the linux SSH client command.

SSH is the general protocol, and ssh is the linux SSH client command.

# Limitations

This article covers how to copy PNG files from a local host to a remote host.

- To learn how to transfer files between remote hosts, see [SCP: Remote to Remote](https://www.google.ru/search?q=SCP+remote+to+remote).
- To transfer large (over 1 GB) files, see [SCP: Transferring Large Files](https://unix.stackexchange.com/questions/190537/transferring-large-8-gb-files-over-ssh)


## Before you start

To be able to copy files, you must have at least read permissions on the source file and write permission on the target system.


Does your version of Windows predate Windows 10? A third-party app is necessary to take advantage of SSH, as it only became native with that version. In cases like these, Putty is the most widely used SSH app for Windows. You can find it at https://www.putty.org/.


## Syntax

To specify the location of the source files, use the following syntax:

`source_directory/file1 file2`

- **source_directory** is the name of the source directory containing.
- **file1**, **file2** are the filenames of the files to copy separated by space.

To specify the location to which the source file will be copied, use the following syntax:

`dest_user@dest_host:dest_directory/newfile1 newfile2`

- **dest_user** is the name of the account on the destination computer.
- **dest_host** is the hostname of the computer to which the source file will be copied.
- **dest_directory** Name of the directory to which the source file will be copied ()
- **newfile1**, **newfile2** are the filenames of the copy files separated by space.

To copy files with the original names, omit the filenames from the destination location.


## Copy selected files

The command below will copy the files `map.png` and `screenshot.png` from the directory `png_files` to the directory `/png_files_new` on the remote host `host2.com`. Also, it will rename the files to `map_copy.png` `screenshot_copy.png`.

`scp /png_files/map.png screenshot.png user2@host2.com:/png_files_new/map_copy.png screenshot_copy.png`

## Copy entire directory

To copy a directory and all its files, use `scp` with the `-r` option for recursive. The command below will copy the entire directory `png_files` from the local machine `host1.com` to the remote host `host2.com`.

`scp -r /png_files/ user2@host2.com:/png_files_new/png_files/`

## Copy wildcard files

If you need to copy all PNG files from a local folder, you can use an asterisc ( * ) as a wildcard. The command below will copy all PNG files from the directory `images` from the local machine to the directory `/images_new` on the remote host `host2.com`.

`scp /images/*.png screenshot.png user2@host2.com:/images_new/`








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

