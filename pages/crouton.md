# Linux on ChromeOS with Crouton

> Tutorial tested on Lenovo N21 & Asus Flip Chromebook (ARM chip)

- Switch to developer mode
  - `Esc + Refresh (F3) + Power`
  - `Ctrl + D` out of "Chrome OS is missing `"Enter` until you see "OS verification is OFF", `Ctrl + D` until you see "Your system is transitioning to Developer Modes" and reboot 

- Enable debugging features (lower left on the first login screen)
  - set developer password (all passwords should be the same for rikersbot)

- Change default user password
  - `Ctrl + Alt + F2` to enter the sytem shell
  - log in as `root` and enter the dev password
  - run `chromeos-setdevpasswd` and set to the same as dev password
  - `Ctrl + Alt + F1` to return to the login screen and finish setting up the default account

- Install Crouton
  - install [crouton extension](https://chrome.google.com/webstore/detail/crouton-integration/gcpneefbbnfalgjniomfjknbcgkbijom)
  - download [crouton](https://goo.gl/fd3zc)
  - `Ctrl + Alt + t` to enter crosh
  - launch `shell`
  - `cd /home/user/[tab through long number]/Downloads`

- Install Debian (this will take a while)
  - `sudo sh crouton -r jessie -t xfce -n debian`
  - run `sudo delete-chroot debian` to delete if needed
  - at some point the prompt will ask you to specify username and pass for primary user---use the same credentials as throughout

> `-r` is the release. We need to set this to stretch, which is the testing branch of Debian. If the -r switch is > not passed Ubuntu will be installed.
>
> `-t` is the target command that specifies what GUI interface you want installed by default. Gnome is the 
> default gui for kali however it does not work on my HP Chromebook 14″. KDE works and is a  good alternative to > Gnome.
>
> `-n` is the name parameter. We define the -n switch here so we can give the chroot a custom name of debian.

- launch lxde from crosh
  - `Ctrl+Alt+t` to launch crush, then `shell`, and `sudo startxfce4`
  - make sure to use the default config when offered
  - you can flip through running chroot desktops by pressing `ctrl+alt+shift+Back/Forward`

- prepare the dev environment
  - remove screensaver `sudo apt-get remove xscreensaver*`
  - install leafpad, ipython, and ipython notebook, in the lxde terminal run `sudo apt-get install ipython ipython-notebook leafpad`
