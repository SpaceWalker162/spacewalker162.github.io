---
title: Remote Access
date: 2024-06-10
permalink: /posts/2024/fowpkfwijf
excerpt_separator: <!--more-->
toc: true
tags:
  - web-dev
---
Some notes on remote access.
<!--more-->

## samba
Samba can be used to share file systems.

# Server Setup
To set up samba service on a Linux machine, follow
[this](https://adrianmejia.com/how-to-set-up-samba-in-ubuntu-linux-and-access-it-in-mac-os-and-windows/)

# Mount on Linux
If the samba service has setting `public = yes`, we can access it as guest. To do so, option `guest` is used. In case of using `/etc/fstab` for mounting, it requires `sudo` which set the owner of the mounted file system `root`. To assign an desired user as the owner, use option `uid`. Therefore, add this line to `/etc/fstab`

    //server/pub    /home/yufei/Documents/remoteDatabase    cifs    guest,uid=<your-uid>    0   0

where `<your-uid>` should be replaced by the intended owner's `uid`, which can be obtained through `id <username>`.

The file systems specified in `/etc/fstab` will be mounted upon computer
boot

They can also be mounted manually through commands like

    mount /home/yufei/Documents/remoteDatabase

# Mount on MacOS
To mount as a guest user, add this line to `/etc/fstab`

    //guest@server/pub    /home/yufei/Documents/remoteDatabase    smbfs    automounted    0   0

To mount an other intended username on the samba server, use

    //username@server/pub    /home/yufei/Documents/remoteDatabase    smbfs    automounted    0   0

Since `mount_smbfs` on MacOS does not provide the option `uid`, to make `yufei` the intended owner, we need to run

    sudo -u yufei mount /home/yufei/Documents/remoteDatabase

## SSH
to-do
