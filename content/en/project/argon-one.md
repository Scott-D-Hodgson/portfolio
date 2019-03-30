---
title: 'How to Install: Argon One'
date: 2019-03-28T15:31:51.975Z
---
Here's how to setup the Argon One for the Raspberry Pi.

## Process

The instructions that are provided with the Argon One board identify that the following command should be used to download, and install, the configuration utilities for the system.

```
$ curl https://download.argon40.com/argon1.sh | bash
```

Through a few attempts this way, it seems to fail often enough that I've reverted to the following commands which seem to provide a more reliable process of getting the script and executing it on the device.

First download the script from the Argon 40 site.

```
$ wget https://download.argon40.com/argon1.sh
```

Once downloaded, change the permissions on the script so that it can be executed.

```
$ chmod +x argon1.sh
```

Now the script can be executed to perform the setup.

```
$ sudo ./argon1.sh
```

Let the script run and, once complete, the Argon One will be ready to respond properly to the restart button, shutdown button (long-press), as well as have available configurations for the included cooling fan.

## Additional Information

Upon completion, there will be two commands available via the terminal.

The first is to be able to configure the speed of the fan based on the temperature of the processor.

```
$ argonone-config
```

While the second is to remove the configuration files from the system.

```
$ argonone-uninstall
```
