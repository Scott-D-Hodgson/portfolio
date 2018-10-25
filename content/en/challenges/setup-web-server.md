---
title: "Setup Web Server"
date: 2018-10-20T22:53:10-04:00
hardware: ["Raspberry Pi"]
software: ["Raspbian", "Apache"]
---

## Update the System
In order to prepare the system for the installation of the web server it is always a good idea to ensure that everything is up-to-date.  This is easily done through executing the following commands within a terminal window.
{{% snippet "/snippets/repository-update" %}}
{{% snippet "/snippets/software-upgrade" %}}
{{% snippet "/snippets/distribution-upgrade" %}}

## Install Apache
Now that the system has been updated, we can perform an installation of the web server, Apache.
{{% snippet "/snippets/apt-get-install-apache" %}}
Once installed, the web server will be serve content from the `/var/www/html` folder, which is browseable at `http://localhost/`.  A default page has been created in the folder.

## Setup Web Root Permissions
In order to change the contents in the web site's root foler, the permissions will need to be updated for the pi account to be able to manage the content.

[Source material by forum response by 'pksato'](https://www.raspberrypi.org/forums/viewtopic.php?t=155067)

Initially the rights to the folder `/var/www` needs to be updated so that the pi account is the owner.
{{% snippet "/snippets/web-root-ownership" %}}
In addition, the folder needs to be updated to have the permissions set.
{{% snippet "/snippets/web-root-permissions" %}}
Now to ensure that files created also belong to the same group.
{{% snippet "/snippets/web-root-create-permission" %}}