---
title: "Fedora Tweaks"
date: 2023-06-02
weight: 5
description: >
  Fedora Tweaks
---

Enabling "tap-to-click" feature for the touchpad at the gdm login screen for Fedora

```shell
machinectl shell gdm@ /bin/bash
gsettings set org.gnome.desktop.peripherals.touchpad tap-to-click true
exit
```

```shell
dnf copr enable starlabs/fwupd
dnf copr enable starlabs/coreboot-configurator
fwupdmgr refresh
fwupdmgr update
```

touchpad drivers?