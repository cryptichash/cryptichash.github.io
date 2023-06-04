---
title: "Fedora Config"
date: 2023-06-03
weight: 5
description: >
  Fedora Config for VS Code
---

https://code.visualstudio.com/docs/setup/linux#_rhel-fedora-and-centos-based-distributions


```shell
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo sh -c 'echo -e "[code]\nname=Visual Studio Code\nbaseurl=https://packages.microsoft.com/yumrepos/vscode\nenabled=1\ngpgcheck=1\ngpgkey=https://packages.microsoft.com/keys/microsoft.asc" > /etc/yum.repos.d/vscode.repo'
```

```shell
dnf check-update
sudo dnf install code
```

https://code.visualstudio.com/docs/sourcecontrol/github