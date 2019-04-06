---
title: Format SD Card
date: 2019-04-06T12:27:07.850Z
---
In order to perform tasks, such as installing an image on an SD card (for Raspbian OS, for example), the initial step of formatting the SD card will help with ensuring the subsequent imaging process runs smoothly.

An easy way to do this is through the use of GParted, a formatting utility that is readily available on most linux repositories.  Start by installing GParted from the terminal.

```
$ sudo apt-get install gparted
```

Once installed, the application can be started from desktop.  It will probably request the root account password to be applied because the application will require low-level access to be able to adjust the partitions of the SD card.

Once open, the application will default to the main device, typically `/dev/sda`, which is most likely the main harddisk and is visible in the dropdown at the top-right of the interface.

If the SD card has not been inserted into the computer, insert it, then from within GParted refresh the devices (`CTRL+R`).

Using the devices dropdown, select the SD card to be formatted (if your computer only has one harddisk, it is probably the device `/dev/sdb`, otherwise you will have to look at each device and determine which is the SD card.

If there are any partitions identified on the card, select each one and delete them.  If the option to delete is not available, it is likely that the partition is mounted.  To unmount the partition, simple select to unmount, and once done the partition will be able to be removed.

Once all partitions are removed, select the empty space and choose to format the entire space as a FAT32 partition.  

Finally, select to apply all changes, and GParted will proceed to remove the existing partitions and format the SD Card.
