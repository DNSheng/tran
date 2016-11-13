# tran v 0.14b
Transfers files over scp in a graphical(?) way.

# Description

I use the RPi 3 to torrent, and store the all the files into a single folder. After they are downloaded, I use this script to transfer the files over to either my laptop or desktop. This script utilizes ssh and scp to display and transfer multiple files and folders in an easy way for me. This script can only grab files and folders from remote to local. Uploading is not a function.

# Usage

Syntax is the same as getting files using scp.
```
tran user@host:~/location/to/files ~/directory/to/copy/to
```
An example would be:
```
tran pi@raspberrypi:~/torrents ./Videos
```
After signing in to the user@host (uses ssh to display), all the files in the directory are displayed. Listed is the number given to the file, the type of file, its name, size, and creation date.
The each file either has the type [F] for file, or [D] for directory. The number given to each file is used in the next part for identification and selection.
After the display, there is a prompt to enter a selection.
Enter the numbers associated with the files you wish to transfer, seperated by a space " ", or select a range using the "-" between two numbers. Combinations of the two are allowed.
The following selects the files numbered: 1, 2, 5, 7, 9, 10, 11, 12, and 13.
```
Please enter your selection:
1 2 5 7 9-13
```
Another password prompt will appear, again asking for the user@host password (uses scp to download).
Afterwards, the files will be downloaded.
A local md5 checksum file can be created if the flag "--md5" is used when the program is run.
```
tran --md5 pi@raspberrypi:~ ./Folder
```

# TODO

- Let an md5sum be created for files that include spaces (ex. "File\ Name.txt")
- Deleting temp file after SIGKILL or SIGTERM
	- Maybe not necessary
- Navigation around folders in the remote host
	- This is hard and will come late (if at all)
- Clean up garbage code (unlikely, I may be the only one who will ever see and use this)
- Replace loops and usage of the "cut" command with sed
- Create a help menu?
- Randomize name of tempfile created to prevent accidental overwrites

# Versions

## 0.14

- Added flag for creating a local md5 checksum (creation disabled by default)
	- Rewrote command line argument parsing as a result
	- Now room/easier for more arguments

## 0.14b

- Attempting to create md5sum for transferred files
	- Files with spaces in the name do not work
		- "No such file or directory"
- Formatted date columns

## 0.13.1

- Fixed critical bug with downloading (would retrieve wrong files)
	- Caused due to altering temp file with name of remote directory

## 0.13

- Better displays the remote directory
- Better displays the local directory

## 0.12

- Now allows for selecting a range of files/folders
- Displays the type of file in the remote folder (directory or normal file)
- Rewrote the "dashed" line in the display to be more elegant
- Removed bits of useless code, reformatted
- Fixed problem with counter incrementing an extra time
- Now displays time (previously had wrong variable printed)
- Size is correctly displayed

## 0.11

- Aligned text, should work for most file names (provided they aren't too long)
- Can now transfer entire folders (like transfering files, but selecting a folder instead)
- Removes the temp file if program ends before transferring files
	- This does NOT count SIGKILL and SIGTERM, thus manual deletion is required
- Remote and local directories are displayed in the list for user

## 0.1

- Initial release
