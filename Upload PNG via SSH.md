# Copying PNG Images From Local To Server via SSH

## Content

- [What is SSH?](#what-is-ssh)
- [Limitations](#limitations)
- [Before you start](#before-you-start)
- [Basic syntax](#basic-syntax)
- [Copy selected files](#copy-selected-files)
- [Copy entire directory](#copy-entire-directory)
- [Copy wildcard files](#copy-wildcard-fies)
- [Related topics](#related-topics)

## What is SSH?<a id="what-is-ssh"></a>

SSH (Secure Shell Protocol) is a secure network protocol that creates a safe channel to transfer data, and `ssh` is the Linux SSH client command. With SSH, you can do the following:

- Secure remote access to resources
- Execute commands remotely
- Automate file transfers

Sending files over SSH relies on the SCP (Secure Copy Protocol), which securely transfers files and folders between two machines. For more information about the syntax and options, consult the manual pages by running these commands:

- For SSH: `man ssh` 
- For SCP: `man scp`

## Limitations<a id="limitations"></a>

This article covers how to copy PNG files from a local host to a remote host, both running on Unix or Linux OS. For other cases, see [Related topics](#related-topics).

## Before you start<a id="before-you-start"></a>

- To be able to copy files, you must have at least read permissions on the source file and write permission on the target system.
- Ensure that you have the password to authenticate on the remote host.

## Basic syntax<a id="basic-syntax"></a>

To specify the location of the source files, use the following syntax:

`source_directory/file1 file2`

- **source_directory** is the name of the source directory containing.
- **file1**, **file2** are the filenames of the files to copy separated by space.

To specify the location to which the source file will be copied, use the following syntax:

`dest_user@dest_host:dest_directory/newfile1 newfile2`

- **dest_user** is the name of the account on the destination machine.
- **dest_host** is the hostname of the machine to which the source file will be copied.
- **dest_directory** is the name of the directory to which the source file will be copied.
- **newfile1**, **newfile2** are the filenames of the copy files separated by space.

To copy files with the original names, omit the filenames from the destination location.

## Copy selected files<a id="copy-selected-files"></a>

The command below will copy the files `map.png` and `screenshot.png` from the directory `png_files` to the directory `/png_files_new` on the remote host `host2.com`. Also, it will rename the files to `map_copy.png` and `screenshot_copy.png`.

`scp /png_files/map.png screenshot.png user2@host2.com:/png_files_new/map_copy.png screenshot_copy.png`

## Copy entire directory<a id="copy-entire-directory"></a>

To copy a directory and all its files, use `scp` with the `-r` option for recursive. The command below will copy the entire directory `png_files` from the local machine `host1.com` to the remote host `host2.com`.

`scp -r /png_files/ user2@host2.com:/png_files_new/png_files/`

## Copy wildcard files<a id="copy-wildcard-fies"></a>

If you need to copy all PNG files from a local folder, you can use an asterisk ( * ) as a wildcard. The command below will copy all PNG files from the directory `images` to the directory `/images_new` on the remote host `host2.com`.

`scp /images/*.png screenshot.png user2@host2.com:/images_new/`

## Related topics<a id="related-topics"></a>

|To                                  |See this   |
| ---------------------------------- | --------- |
|Transfer files between remote hosts |[SCP: Remote to Remote](https://www.google.ru/search?q=SCP+remote+to+remote)|
|Transfer files over 1 GB            |[SCP: Transferring Large Files](https://unix.stackexchange.com/questions/190537/transferring-large-8-gb-files-over-ssh)|
|Use ssp on Windows machines         |[How to use SCP command on Windows](https://success.tanaza.com/s/article/How-to-use-SCP-command-on-Windows)|
