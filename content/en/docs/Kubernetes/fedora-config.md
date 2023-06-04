---
title: "Fedora Config"
date: 2023-06-03
weight: 5
description: >
  Fedora Config for Kubernetes
---

## minikube with podman

> <https://minikube.sigs.k8s.io/docs/start/>

```shell
curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-latest.x86_64.rpm
sudo rpm -Uvh minikube-latest.x86_64.rpm
```

### Known Issues

> <https://minikube.sigs.k8s.io/docs/drivers/podman/#known-issues>

- Podman requires passwordless running of sudo.

```shell
$ sudo visudo
```

Then append the following to the section *at the very bottom* of the file where `username` is your user account.

```shell
username ALL=(ALL) NOPASSWD: /usr/bin/podman
```

Be sure this text is *after* `#includedir /etc/sudoers.d`. To confirm it worked, try:

```shell
sudo -k -n podman version
```

## OpenLens

> - Source
>   - <https://github.com/lensapp/lens>
> - Build
>   - <https://github.com/MuhammedKalkan/OpenLens>
> - Releases
>   - <https://github.com/MuhammedKalkan/OpenLens/releases>

```shell
sudo rpm -Uvh OpenLens-<version>.x86_64.rpm 
```

### Extensions

> <https://github.com/alebcay/openlens-node-pod-menu>

In OpenLens, navigate to the Extensions list. In the text box, enter the name of this plugin:

```
@alebcay/openlens-node-pod-menu
```

Click "Install", and after a few moments, the plugin should appear in the list of installed extensions and be enabled.
