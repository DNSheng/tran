# tran v 0.1
Transfers files over scp in a graphical(?) way.

# Description

I use the RPi 3 to torrent, and store the all the files into a single folder. After they are complete, I use this script to transfer the files over to either my laptop or desktop. This script utilizes ssh and scp to display and transfer files. This script can only grab files, and is unable to upload.

# Usage

Syntax is the same as getting files using scp.
```
tran user@host:~/location/to/files ~/directory/to/copy/to
```
An example would be:
```
tran pi@raspberrypi:~/torrents ./Videos
```
After signing in to the user@host (uses ssh to display), all the files in the directory are displayed and there is a prompt to enter a selection.
Enter the numbers associated with the files you wish to transfer, seperated by a space "\ "
```
Please enter your selection:
1 2 5 7
```
Another password prompt will appear, still asking for the user@host password (uses scp to download).
Afterwards, the files will be downloaded.

# TODO

- Add an md5 checksum at the end (after downloading) for files on the RPi 3 and other device to check for file integrity.
- Properly align columns in the display
