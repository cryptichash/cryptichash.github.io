---
title: "Config"
date: 2023-06-03
weight: 5
description: >
  Config
---

/etc/dnf/dnf.conf

```
max_parallel_downloads=10
```

```shell
sudo dnf install https://mirrors.rpmfusion.org/free/fedora/rpmfusion-free-release-$(rpm -E %fedora).noarch.rpm https://mirrors.rpmfusion.org/nonfree/fedora/rpmfusion-nonfree-release-$(rpm -E %fedora).noarch.rpm
```

```shell
sudo dnf upgrade --refresh
sudo dnf groupupdate core
```

<https://rpmfusion.org/FAQ>

```shell
sudo dnf install rpmfusion-free-release-tainted
sudo dnf install rpmfusion-nonfree-release-tainted
```

```shell
flatpak remote-add --if-not-exists flathub https://flathub.org/repo/flathub.flatpakrepo
flatpak update
```

```shell
sudo dnf install 'google-roboto*' 'mozilla-fira*' fira-code-fonts
```

<https://docs.fedoraproject.org/en-US/quick-docs/assembly_installing-plugins-for-playing-movies-and-music/>

<https://rpmfusion.org/Howto/Multimedia>

```shell
sudo dnf groupupdate multimedia --setop="install_weak_deps=False" --exclude=PackageKit-gstreamer-plugin
sudo dnf groupupdate sound-and-video
```

```shell
sudo dnf swap mesa-va-drivers mesa-va-drivers-freeworld
sudo dnf swap mesa-vdpau-drivers mesa-vdpau-drivers-freeworld
```

```shell
sudo dnf install gstreamer1-plugins-{bad-\*,good-\*,base} gstreamer1-plugin-openh264 gstreamer1-libav --exclude=gstreamer1-plugins-bad-free-devel
sudo dnf install lame\* --exclude=lame-devel
sudo dnf group upgrade --with-optional Multimedia
```

<https://docs.fedoraproject.org/en-US/quick-docs/openh264/>

```shell
sudo dnf config-manager --set-enabled fedora-cisco-openh264
sudo dnf install gstreamer1-plugin-openh264 mozilla-openh264
```

Afterwards you need open Firefox, go to menu → Add-ons → Plugins and enable OpenH264 plugin.
