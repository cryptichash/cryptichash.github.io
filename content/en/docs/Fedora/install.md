---
title: "Install"
date: 2023-06-11
weight: 2
description: >
  Install
---

## Create Bootable USB

### Install Ventoy to USB

> - <https://www.ventoy.net/en/doc_start.html>
> - <https://github.com/ventoy/Ventoy/releases>

### Copy Fedora Image to USB

> <https://fedoraproject.org/workstation/download/>

### Copy SystemRescue to USB

> <https://www.system-rescue.org/Download/>

## Boot from USB and Install Fedora

> <https://ostechnix.com/install-fedora/>

## GRUB2 with EFI

> <https://docs.fedoraproject.org/en-US/quick-docs/bootloading-with-grub2/#installing-grub-2-configuration-on-uefi-system>

### Install Bootloader Files

```bash
sudo dnf reinstall grub2-efi grub2-efi-modules shim
```

### Ensure GRUB2 Menu is Hidden

> <https://hansdegoede.livejournal.com/19081.html>

```bash
sudo grub2-editenv - set menu_auto_hide=2
```

### Create GRUB2 Configuration

```bash
sudo grub2-mkconfig -o /boot/grub2/grub.cfg
```
