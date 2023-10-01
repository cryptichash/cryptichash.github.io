---
title: "Fedora Config"
date: 2023-06-02
weight: 5
description: >
  Fedora Config for StarBook
---

## Touchpad

> <https://help.gnome.org/users/gnome-help/stable/mouse-touchpad-click.html.en>

Enabling "tap-to-click" feature for the touchpad at the gdm login screen for Fedora

```shell
machinectl shell gdm@ /bin/bash
gsettings set org.gnome.desktop.peripherals.touchpad tap-to-click true
exit
```

touchpad drivers?

## Firmware

> <https://support.starlabs.systems/kb/firmware/lvfs-requirements>

```shell
sudo dnf copr enable starlabs/fwupd
sudo dnf copr enable starlabs/coreboot-configurator
sudo fwupdmgr get-devices
sudo fwupdmgr refresh --force
sudo fwupdmgr get-updates
sudo fwupdmgr update
```

## Battery

> Enable Power Percentage

```bash
gsettings set org.gnome.desktop.interface show-battery-percentage true
```
