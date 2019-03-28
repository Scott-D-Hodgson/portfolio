---
title: Unattended Upgrades
date: 2019-03-28T15:54:12.924Z
---
One of the common aspects of working with the Raspberry Pi is the need to perform regular maintenance to keep the system up and running properly.

This is often done, and frequently found online, through the execution of the following commands.

```
$ sudo apt-get update
```

```
$ sudo apt-get upgrade
```

Optionally, if upgrading the entire distribution of the Raspbian operating system on your machine, is desired the additional distribution upgrade command is required.

```
$ sudo apt-get dist-upgrade
```

There is, however, another way...

Process

In order to permit your Raspberry Pi to perform the update/upgrade process automatically, all that is needed is to install the package for unattended upgrades.

```
$ sudo apt-get install unattended-upgrades
```

Once done, your Raspberry Pi will process the updates/upgrades automatically each day.
