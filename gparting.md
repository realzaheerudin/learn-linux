
# Quiz

## Question 1 

At this point you should have on your virtual machine a second virtual disk partitioned using GPT, with three partitions of 100MB, 2GB, 3GB and whatever space is left. We now want to put filesystems in these and try out the commands for working with them.

We can do this from the usual OpenSuse Linux - no more need for GParted.

Use the mkfs(8) command to create filesystems as follows:

100MB partition - VFAT
2GB partition - ext4
3GB partition - NTFS
Last partition - Btrfs
Then use gdisk(8) to list the partitions on the disk.

Copy the commands and output and paste in below.

Include comments if necessary to explain what you are doing

## 1 Answer 


## Question 2

Use the lsblk(1) command to get a list of all the block devices (disks and similar storage devices) on the system. Paste in the command and output below.

## Answer text Question 2

## Question 3

Use blkid(8) to list the id numbers of all the block devices. Paste in the command and output below.

Hint: what does the (8) above tell you about blkid?

## Answer text Question 3

## Question 4

Use the mount(8) command to mount your new filesystems as follows:

FAT filesystem should be read-only
ext4 filesystem should be normally mounted
NTFS filesystem should be normally mounted
btrfs filesystem should have the nosuid option set
You will need to create four mount points for this using mkdir(1) [we will see this in class].

Then run mount(8) and findmnt(8) to list them.

Paste in the commands and output below.

Include comments to explain what you see.

## Answer Question 4

## Question 5

Use findmnt(8) to list the mounted file systems in a more friendly format than mount(8).

Pater in the command and output below.

## Answer 6

## Question 6

Use du(1) and df(1) commands to examine the amount of space used and available on the new filesystems.

Use appropriate options to the commands to get useful and easy to understand output.

Paste in the commands and results below.

Include comments if necessary.

## Question 7

Unmount the filesystems.

 

Paste in the commands and results below.

Include comments if necessary.