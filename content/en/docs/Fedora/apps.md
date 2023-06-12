---
title: "Apps"
date: 2023-06-03
weight: 5
description: >
  Apps for Fedora
---

## Media

### mpv

> - <https://mpv.io/>
> - <https://github.com/mpv-player/mpv>
> - <https://mpv.io/manual/stable/>

```shell
sudo dnf install mpv
```

`~/.config/mpv/mpv.conf`

```cfg
vo=gpu
gpu-context=wayland
hwdec=vaapi
```

### Celluloid

> - <https://celluloid-player.github.io/>
> - <https://github.com/celluloid-player/celluloid>

```shell
sudo dnf install celluloid
```

### YT-DLP

> <https://github.com/yt-dlp/yt-dlp>

```shell
sudo dnf install yt-dlp
```

## Terminal

### Bottom

> <https://github.com/ClementTsang/bottom>

```shell
sudo dnf copr enable atim/bottom
sudo dnf install bottom
```

### Alacritty

> - <https://alacritty.org/>
> - <https://github.com/alacritty/alacritty>
> - <https://ostechnix.com/alacritty-terminal-emulator/>

```shell
sudo dnf install alacritty
```

## FlatPak

- Dropbox
- Bitwarden
