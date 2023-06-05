---
title: "VS Code Dev Containers"
date: 2023-06-02
weight: 5
description: >
  VS Code Dev Containers for Docsy
---

## Create Dev Containers files in `.devcontainer` folder

### `devcontainer.json` file

* Go
  * <https://github.com/microsoft/vscode-dev-containers/blob/main/containers/go/.devcontainer/devcontainer.json>
* Hugo
  * <https://github.com/microsoft/vscode-dev-containers/blob/main/containers/hugo/.devcontainer/devcontainer.json>

```json
// For format details, see https://aka.ms/devcontainer.json. For config options, see the
// README at: https://github.com/devcontainers/templates/tree/main/src/go
{
	"name": "Go",
	// Or use a Dockerfile or Docker Compose file. More info: https://containers.dev/guide/dockerfile
	"build": {
		"dockerfile": "Dockerfile",
		"args": {
			"VARIANT": "1-bullseye",
			// Update HUGO_VARIANT to pick hugo variant.
			// Example variants: hugo, hugo_extended
			// Rebuild the container if it already exists to update.
			"HUGO_VARIANT": "hugo_extended",
			// Update HUGO_VERSION to pick a specific hugo version.
			// Example versions: latest, 0.73.0, 0,71.1
			// Rebuild the container if it already exists to update.
			"HUGO_VERSION": "0.112.4",
			// Update NODE_VERSION to pick the Node.js version: 12, 14
			"NODE_VERSION": "18"
		}
	},

	// Features to add to the dev container. More info: https://containers.dev/features.
	// "features": {},

	// Use 'forwardPorts' to make a list of ports inside the container available locally.
	"forwardPorts": [
		1313
	],

	// Use 'postCreateCommand' to run commands after the container is created.
	// "postCreateCommand": "go version",

	// Configure tool-specific properties.
	"customizations": {
		// Configure properties specific to VS Code.
		"vscode": {
			// Set *default* container specific settings.json values on container create.
			"settings": { 
				"html.format.templating": true
			},
			
			// Add the IDs of extensions you want installed when the container is created.
			"extensions": [
				"bungcip.better-toml",
				"davidanson.vscode-markdownlint"
			]
		}
	},

  // Set `remoteUser` to `root` to connect as root instead. More info: https://aka.ms/vscode-remote/containers/non-root.
  "remoteUser": "vscode"
}
```

### `Dockerfile`

* Go
  * <https://github.com/microsoft/vscode-dev-containers/blob/main/containers/go/.devcontainer/Dockerfile>
* Hugo
  * <https://github.com/microsoft/vscode-dev-containers/blob/main/containers/hugo/.devcontainer/Dockerfile>

```dockerfile
# [Choice] Go version (use -bullseye variants on local arm64/Apple Silicon): 1, 1.19, 1.18, 1-bullseye, 1.19-bullseye, 1.18-bullseye, 1-buster, 1.19-buster, 1.18-buster
ARG VARIANT=1-bullseye
FROM mcr.microsoft.com/vscode/devcontainers/go:0-${VARIANT}

# [Choice] Node.js version: none, lts/*, 18, 16, 14
ARG NODE_VERSION="none"
RUN if [ "${NODE_VERSION}" != "none" ]; then su vscode -c "umask 0002 && . /usr/local/share/nvm/nvm.sh && nvm install ${NODE_VERSION} 2>&1"; fi

# HUGO_VARIANT can be either 'hugo' for the standard version or 'hugo_extended' for the extended version.
ARG HUGO_VARIANT=hugo
# HUGO_VERSION can be either 'latest' or a specific version number
ARG HUGO_VERSION=latest

# Download Hugo
RUN apt-get update && apt-get install -y ca-certificates openssl git curl && \
    rm -rf /var/lib/apt/lists/* && \
    case ${HUGO_VERSION} in \
    latest) \
    export HUGO_VERSION=$(curl -s https://api.github.com/repos/gohugoio/hugo/releases/latest | grep "tag_name" | awk '{print substr($2, 3, length($2)-4)}') ;;\
    esac && \
    echo ${HUGO_VERSION} && \
    case $(uname -m) in \
    aarch64) \
    export ARCH=ARM64 ;; \
    *) \
    export ARCH=64bit ;; \
    esac && \
    echo ${ARCH} && \
    wget -O ${HUGO_VERSION}.tar.gz https://github.com/gohugoio/hugo/releases/download/v${HUGO_VERSION}/${HUGO_VARIANT}_${HUGO_VERSION}_Linux-${ARCH}.tar.gz && \
    tar xf ${HUGO_VERSION}.tar.gz && \
    mv hugo /usr/bin/hugo

# Hugo dev server port
EXPOSE 1313

# [Optional] Uncomment this section to install additional OS packages.
# RUN apt-get update && export DEBIAN_FRONTEND=noninteractive \
#     && apt-get -y install --no-install-recommends <your-package-list-here>

# [Optional] Uncomment the next lines to use go get to install anything else you need
# USER vscode
# RUN go get -x <your-dependency-or-tool>

# [Optional] Uncomment this line to install global node packages.
RUN su vscode -c "source /usr/local/share/nvm/nvm.sh && npm install -g autoprefixer postcss-cli postcss" 2>&1
```

## Rebuild Container

> Within the Container Shell

```shell
vscode ➜ /workspace (master) $
```

### Create `package-lock.json` file

> Commit `package-lock.json`!

```shell
npm install
```

### Create Docsy Site

```shell
hugo
```

### Test Docsy Site

> <http://localhost:1313/>

```shell
hugo server
```
