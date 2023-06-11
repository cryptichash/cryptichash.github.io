---
title: "Fedora Config"
date: 2023-06-02
weight: 5
description: >
  Fedora Config for StarBook
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
content/en/docs/Kubernetes/fedora-config.md