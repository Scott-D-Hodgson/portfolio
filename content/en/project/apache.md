---
title: Install Apache
date: 2019-03-30T11:43:01.481Z
---
The Apache web server is readily available from the standard repositories for the Raspbian OS through the typical terminal command.

```
$ sudo apt-get install apache2
```

Once installed, the web server will be already serving content.  Open a web browser to view the default apache installation page, located at `http://localhost/`.  This page is being served from the web root folder, located at `/var/www/html`, however the default permissions do not allow the content to be updated.

In order to permit the creation of content in the web root, update the permissions for the pi account, and the web root group (`www-data`), to be the owner of the web root.

Content Reference (post by pksato): <https://www.raspberrypi.org/forums/viewtopic.php?t=155067>

```
$ sudo chown -R pi:www-data /var/www
```

In addition, the folder needs to be updated to have the permissions set to allow the pi account to have full control of the folder and the web root group to have only read access.

```
$ sudo chmod u+rxw,g+rx-w,o-rwx /var/www
```

Now it is needed to ensure that files created in the folder also belong the same web root group.

```
$ sudo chmod g+s /var/www
```

If there were pre-existing files/folders in the folder, the following commands will set the permissions the way they are supposed to be:

To set the permissions for files.

```
$ chmod u+rw,g+r-xw,o-rwx
```

To set the permissions for folders.

```
$ chmod u+rwx,g+rx-w,o-rxw
```
