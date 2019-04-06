---
title: Install Raspbian
date: 2019-04-06T13:51:29.006Z
---
Once the Raspbian image has been downloaded, it can be written to the SD card.  The `dd` command will write an input file (`if`) into an output file (`of`).  Since the SD card appears to the file system as a file, this allows an image file to be written out to the device.

For example, the Raspbian image file `2018-11-13-raspbian-stretch-lite.img` may be used as an input file to write out to the SD card identified as `/dev/sdb`.

```
$ sudo dd bs=1M if=2018-11-13-raspbian-stretch-lite.img of=/dev/sdb
```
