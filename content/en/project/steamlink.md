---
title: 'How to Install: Steamlink'
date: 2019-03-28T18:14:16.399Z
---
The Raspberry Pi can be used as a Steamlink device to enable game streaming from your home computer to another screen in your home.

## Process

The steps to install the Steamlink software on the Raspberry Pi involve primarily the setup command from the default repositories.

```
$ sudo apt-get install steamlink
```

If, however, the base Raspbian operating system on the Raspberry Pi is the lite verion, as opposed to the version with the desktop, an additional install of Zenity is required.

```
$ sudo apt-get install zenity
```

Once done, the Steamlink software can be run by executing it from the command line.

```
$ steamlink
```

## Additional Information

A few additional features, to make the Steamlink experience more smooth to other people, would involve the additional configurations for...

* The automatic login to the device upon boot
* The automatic startup of Steamlink

### Automatic Login

To enable the automatic login, enter into the Raspbian configuration.

```
$ sudo raspi-config
```

Once the menu appears, select **Boot Options**.

On the following menu, select **Desktop / CLI** to identify which boot up process is preferred.

Finally select **Console Autologin**.

The Raspbian configuration utility can be exited (by selecting **Finished**) and will most likely request to reboot.  Next time it boots, the system should have the default Pi user logged in and ready to go.

### Automatic Startup

Content reference: <https://www.techradar.com/how-to/how-to-turn-a-raspberry-pi-into-a-steam-link>

To enable Steamlink to startup automatically, a script file will need to be created to handle the task of opening the application.

```
$ sudo nano steamlink-auto.sh
```

Within the file add the command to identify that the **Bash** shell should be used as the interpreter of the script.

```
#!/bin/bash
```

Following that is the command to execute the Steamlink application.

```
/usr/bin/steamlink %U
```

Once done, close and save the file (in **Nano** this is done by the combination of `CTRL+X` to **Exit**, `Y` to confirm saving the buffer, followed by `ENTER` to accept the same filename).

The script file will need to be set to executable in order to run.

```
$ sudo chmod +x steamlink-auto.sh
```

Finally, the script will have to be added to the Crontab to be called upon boot and this is done through editing it.

```
$ sudo crontab -e
```

If prompted, select to edit using **Nano**, same as earlier.  At the end of the file, add a new line to identify that the script should be run everytime the system boots.

```
@reboot /home/pi/steamlink-auto.sh
```

Close and save the file (again, repeating the combination of `CTRL+X` to **Exit**, `Y` to confirm saving the buffer, followed by `ENTER` to accept the same filename).

Now reboot the Raspberry Pi!

```
$ sudo reboot
```
