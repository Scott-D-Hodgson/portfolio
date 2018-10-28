---
title: "Setup Hugo"
date: 2018-10-25T18:53:10-04:00
tags: ["Raspberry Pi", "Raspbian", "Hugo", "Go"]
---
This challenge was the result of trying to setup a Raspberry Pi to automatically download from a [GitHub](https://github.com) repository, build a Hugo site's public output, and update the hosted site.

{{% alert type="info" heading="Prerequisites" %}}
In order to successfully complete this challenge, the following items need to be setup:

- Git
- Go

{{% /alert %}}

In order to prepare the system for the installation of Go it is always a good idea to ensure that everything is up-to-date.  This is easily done through executing the following commands within a terminal window.
```bash 
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

{{% credit "gohugo.io" "https://gohugo.io/getting-started/installing/" %}}
Retrieve the source cdoe from the [GitHub](https://github.com) for building Hugo.  At the time of this writing, the current build is 

```bash
mkdir ~/src
cd ~/src
git clone https://github.com/gohugoio/hugo.git
cd hugo
```

If support is needed for Sass/SCSS support, include the extended tags as an installer option.

```bash
go install --tags extended
```

Otherwise omit them entirely.

```bash
go install
```

The installation can now be tested.

```bash
hugo help
```