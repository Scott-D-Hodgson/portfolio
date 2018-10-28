---
title: "Setup Go"
date: 2018-10-25T18:53:10-04:00
tags: ["Raspberry Pi", "Raspbian", "Go"]
---

In order to prepare the system for the installation of Go it is always a good idea to ensure that everything is up-to-date.  This is easily done through executing the following commands within a terminal window.
```bash 
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

{{% credit "simoncos" "https://gist.github.com/simoncos/49463a8b781d63b5fb8a3b666e566bb5" %}}
The source for Go is located on the [Go Programming Language Download Page](https://golange.org/dl/) and, in order to install on the Raspberry Pi, we need to locate the download for the `armv6` processor specifically.  At the time of this writing, the current build is [Go 1.11.1](https://golang.org/doc/install?download=go1.11.1.linux-armv6l.tar.gz).

```bash
wget https://storage.googleapis.com/golang/go1.11.1.linux-armv6l.tar.gz
sudo tar -C /usr/local -xzf go1.11.1.linux-armv6l.tar.gz
```

The files will now be located in the folder `/usr/local/go` folder.

The path to the exectable needs to be added to the path so that Go can be called regardless of location in the file structure.

```bash
export PATH=$PATH:/usr/local/go/bin
```

This will create the path during this session however it needs to be added to the profile to be available in all subsequent sessions.  To do this, the `~/.profile` file needs to be edited.

```bash
sudo nano ~/.profile
```

At the end of the file, add the same command to setup the path variable.

```bash
export PATH=$PATH:/usr/local/go/bin
```

{{% alert type="info" heading="Note:" %}}
If Go (golang) has been installed earlier via `apt-get` then it is best to remove it.

```bash
sudo apt remove golang
sudo apt-get autoremove
source .profile
```
{{% /alert %}}

The installation can now be tested.

```bash
go version
```