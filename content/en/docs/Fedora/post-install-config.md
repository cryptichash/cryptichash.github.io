---
title: "Post Install Config"
date: 2023-06-03
weight: 3
description: >
  Post Install Config for Fedora
---

> - <https://www.hackingthehike.com/fedora38-guide/>
> - <https://github.com/devangshekhawat/Fedora-38-Post-Install-Guide>

## Faster Updates

> - <https://dnf.readthedocs.io/en/latest/conf_ref.html#max-parallel-downloads-label>

```shell
sudo nano /etc/dnf/dnf.conf
```

```cfg
max_parallel_downloads=10
```

## RPM Fusion

> - <https://rpmfusion.org/Configuration>
> - <https://docs.fedoraproject.org/en-US/quick-docs/setup_rpmfusion/>

### Install RPM Fusion

```shell
sudo dnf install https://mirrors.rpmfusion.org/free/fedora/rpmfusion-free-release-$(rpm -E %fedora).noarch.rpm https://mirrors.rpmfusion.org/nonfree/fedora/rpmfusion-nonfree-release-$(rpm -E %fedora).noarch.rpm
```

### Install Appstream Metadata

```shell
sudo dnf upgrade --refresh
sudo dnf groupupdate core
```

### Install Tainted

> - <https://rpmfusion.org/FAQ>

```shell
sudo dnf install rpmfusion-free-release-tainted
sudo dnf install rpmfusion-nonfree-release-tainted
```

## Flatpak

> - <https://flatpak.org/setup/Fedora>

```shell
flatpak remote-add --if-not-exists flathub https://flathub.org/repo/flathub.flatpakrepo
flatpak update
```

## Fonts

> - <https://github.com/googlefonts/roboto>
> - <https://github.com/mozilla/Fira>
> - <https://github.com/tonsky/FiraCode>

```shell
sudo dnf install 'google-roboto*' 'mozilla-fira*' fira-code-fonts
```

### Microsoft TrueType Fonts

> - <https://mscorefonts2.sourceforge.net/>

```shell
sudo dnf install curl cabextract xorg-x11-font-utils fontconfig
sudo rpm -i https://downloads.sourceforge.net/project/mscorefonts2/rpms/msttcore-fonts-installer-2.6-1.noarch.rpm
```

## Media

### Install Codecs

> - <https://rpmfusion.org/Howto/Multimedia>

```shell
sudo dnf groupupdate multimedia --setop="install_weak_deps=False" --exclude=PackageKit-gstreamer-plugin
sudo dnf groupupdate sound-and-video
```

#### AMD Hardware Codecs

```shell
sudo dnf swap mesa-va-drivers mesa-va-drivers-freeworld
sudo dnf swap mesa-vdpau-drivers mesa-vdpau-drivers-freeworld
```

### Install Plugins

> - <https://docs.fedoraproject.org/en-US/quick-docs/assembly_installing-plugins-for-playing-movies-and-music/>

```shell
sudo dnf install gstreamer1-plugins-{bad-\*,good-\*,base} gstreamer1-libav --exclude=gstreamer1-plugins-bad-free-devel
sudo dnf install lame\* --exclude=lame-devel
sudo dnf group upgrade --with-optional Multimedia
```

#### OpenH264

> - <https://docs.fedoraproject.org/en-US/quick-docs/openh264/>

##### Install OpenH264

```shell
sudo dnf config-manager --set-enabled fedora-cisco-openh264
sudo dnf install gstreamer1-plugin-openh264 mozilla-openh264
```

##### Configure Firefox

- Open Firefox
- Go to Menu
- Select `Add-ons and themes`
- Select `Plugins`
- Enable OpenH264 plugin
