---
title: "Web Root Permissions"
date: 2018-10-21T09:59:46-04:00
software: ["Raspbian"]
commands: ["chmod"]
---
```bash
sudo chmod u+rxw,g+rx-w,o-rwx /var/www
```