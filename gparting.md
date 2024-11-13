
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


```txt
user@vbox:~> lsblk
NAME   MAJ:MIN RM  SIZE RO TYPE MOUNTPOINTS
sda      8:0    0   12G  0 disk 
├─sda1   8:1    0  512M  0 part /boot/efi
└─sda2   8:2    0 11.5G  0 part /var
                                /usr/local
                                /root
                                /tmp
                                /home
                                /boot/grub2/i386-pc
                                /boot/grub2/x86_64-efi
                                /opt
                                /srv
                                /
sdb      8:16   0  512M  0 disk 
sdc      8:32   0  512M  0 disk 
sdd      8:48   0  512M  0 disk 
sde      8:64   0  512M  0 disk 
sr0     11:0    1  550M  0 rom  /run/media/user/GParted-live

user@vbox:/mnt> dir
total 0
drwxr-xr-x 1 root root 0 Nov 13 22:42 btrfs
drwxr-xr-x 1 root root 0 Nov 13 22:41 ext4
drwxr-xr-x 1 root root 0 Nov 13 22:38 fat_mount
drwxr-xr-x 1 root root 0 Nov 13 22:41 ntfs

vbox:/mnt # mount | grep "/mnt"
/dev/sdb1 on /mnt/fat type vfat (ro,relatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/sdc1 on /mnt/ext4 type ext4 (rw,relatime)
/dev/sdd1 on /mnt/ntfs type fuseblk (rw,nosuid,nodev,relatime,user_id=0,group_id=0,allow_other,blksize=4096)
/dev/sde1 on /mnt/btrfs type btrfs (rw,nosuid,relatime,space_cache,subvolid=5,subvol=/)
```

```txt
vbox:/mnt # findmnt | grep "/mnt/"
├─/mnt/fat                            /dev/sdb1                           vfat            ro,relatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro
├─/mnt/ext4                           /dev/sdc1                           ext4            rw,relatime
├─/mnt/ntfs                           /dev/sdd1                           fuseblk         rw,nosuid,nodev,relatime,user_id=0,group_id=0,allow_other,blksize=4096
└─/mnt/btrfs                          /dev/sde1                           btrfs           rw,nosuid,relatime,space_cache,subvolid=5,subvol=/
```

```txt
vbox:/mnt # du -sh /mnt/fat /mnt/ext4 /mnt/ntfs /mnt/btrfs
4.0K    /mnt/fat
13K     /mnt/ext4
4.0K    /mnt/ntfs
16K     /mnt/btrfs

vbox:/mnt # df -h /mnt/fat /mnt/ext4 /mnt/ntfs /mnt/btrfs
Filesystem      Size  Used Avail Use% Mounted on
/dev/sdb1       510M  4.0K  510M   1% /mnt/fat
/dev/sdc1       469M   14K  440M   1% /mnt/ext4
/dev/sdd1       511M  3.1M  508M   1% /mnt/ntfs
/dev/sde1       511M  3.5M  430M   1% /mnt/btrfs
```

```txt
vbox:/mnt # 
vbox:/mnt # umount /mnt/fat
vbox:/mnt # umount /mnt/ext4
vbox:/mnt # umount /mnt/ntfs
vbox:/mnt # umount /mnt/btrfs
vbox:/mnt # 
vbox:/mnt # findmnt | grep "/mnt"
vbox:/mnt # 
vbox:/mnt # df | grep "/mnt"
vbox:/mnt #
```

```txt
vbox:/mnt # blkid
/dev/sda1: UUID="CE9E-A09D" BLOCK_SIZE="512" TYPE="vfat" PARTUUID="bc3f902f-e8b2-47da-8d65-12968b27ff00"
/dev/sda2: UUID="f6a24ff6-109d-4863-bb7c-e6581e68daa2" UUID_SUB="80605b53-1b96-45b9-9dd1-6f41b7028cec" BLOCK_SIZE="4096" TYPE="btrfs" PARTUUID="73892896-59b6-4376-9e99-ffb479a56904"
/dev/sdb1: UUID="F9DC-24A1" BLOCK_SIZE="512" TYPE="vfat" PARTUUID="d1bd079c-01"
/dev/sdc1: UUID="25286243-6524-426b-b079-4dad68189e85" BLOCK_SIZE="1024" TYPE="ext4" PARTUUID="e7dfdfd7-01"
/dev/sdd1: BLOCK_SIZE="512" UUID="593ED9B21E0F2C32" TYPE="ntfs" PARTUUID="db9754cc-01"
/dev/sde1: UUID="1ff8e680-0538-4349-84f0-07ec554a5555" UUID_SUB="ccf10b38-f605-475a-9da8-46081ba446b4" BLOCK_SIZE="4096" TYPE="btrfs" PARTUUID="9c58d406-01"
/dev/sr0: BLOCK_SIZE="2048" UUID="2024-09-28-02-37-36-00" LABEL="GParted-live" TYPE="iso9660" PTUUID="2bb2e5d0" PTTYPE="dos"
```

---

# Quiz 2

## Quesrion 1 (50 marks)

Add entries to your /etc/fstab file (yes, edit the actual file) which will mount the three partitions on your second virtual drive when the system boots.

Give them options as follows:

the FAT partition should be mounted read-only
the ext4 partition should have the nosuid option set but be read-write
the third partition should have simply the default options
Paste in your fstab file below.

 

Caution: errors in fstab can render your system unbootable; on a real system, you then have to boot from a USB drive using something like GParted and fix the fstab, or work out how to start the system in "single user" mode and fix it. It's a good idea to copy critical system files like this before editing them so you know what was in the old version and can put it back easily.

SNAPSHOT YOUR VM BEFORE ATTEMPTING THIS PRACTICAL! THAT WAY YOU CAN ROLL BACK THE CHANGES IF IT BREAKS SOMETHING.

## Question 2 (20 marks)

Reboot your system so that the new entries should be applied and the three file systems mounted.

Paste in the output of the mount command below showing the three mounted filesystems.

Hint: Use findmnt or df to see the mounted filesystems

 

Caution: errors in fstab can render your system unbootable; you then have to boot from a CD/USB drive and fix the fstab, or work out how to start the system in "single user" mode and fix it.

IT IS A GOOD IDEA TO TEST THE /etc/fstab BEFORE REBOOTING, AND TO SNAPSHOT THE VM BEFORE CHANGING THE /etc/fstab.
