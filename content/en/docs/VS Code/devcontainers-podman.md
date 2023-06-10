---
title: "Dev Containers with Podman"
date: 2023-06-04
weight: 5
description: >
  Dev Containers with Podman for VS Code
---

> - <https://code.visualstudio.com/docs/devcontainers/containers>
> - <https://containers.dev/>
> - <https://github.com/devcontainers/templates>
> - <https://github.com/devcontainers/images>

## Install Dev Containers extension

> <https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-containers>

```shell
code --install-extension ms-vscode-remote.remote-containers
```

### Podman Config

> https://code.visualstudio.com/remote/advancedcontainers/docker-options#_podman

Podman 1.9+ is mostly compatible with Docker's CLI commands and therefore does work if you update the Docker Path setting (via Dev > Containers: Docker Path in the Settings editor) to `podman` on Linux.

### devcontainer.json file

> - <https://code.visualstudio.com/docs/devcontainers/create-dev-container>
> - <https://containers.dev/implementors/json_reference/>
> - <https://code.visualstudio.com/remote/advancedcontainers/change-default-source-mount>
> - <https://podman-desktop.io/blog/develop-using-devcontainer>
> - <https://docs.podman.io/en/latest/markdown/podman-run.1.html#volume-v-source-volume-host-dir-container-dir-options>
> - <https://www.redhat.com/sysadmin/podman-inside-container>
> - <https://opensource.com/article/21/7/vs-code-remote-containers-podman>

```json
"workspaceMount": "source=${localWorkspaceFolder},target=/workspace,type=bind",
"workspaceFolder": "/workspace",
"runArgs": [
	// run container as current user
	"--userns=keep-id",
	// disable selinux isolation that breaks bind mounts
	"--security-opt=label=disable"
],
"containerUser": "vscode"
```
