---
title: "VS Code Dev Containers"
date: 2023-06-02
weight: 5
description: >
  VS Code Dev Containers for Docsy using Podman
---

https://opensource.com/article/21/7/vs-code-remote-containers-podman

```shell
code --install-extension ms-vscode-remote.remote-containers
```

use podman instead of docker

```
"workspaceMount": "source=${localWorkspaceFolder},target=/workspace,type=bind,Z",
"workspaceFolder": "/workspace",

"runArgs": ["--userns=keep-id"],
"containerUser": "vscode"
```