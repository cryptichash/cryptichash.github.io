---
title: "Fedora Config"
date: 2023-06-03
weight: 5
description: >
  Fedora Config for minikube
---

## minikube with podman

> <https://minikube.sigs.k8s.io/docs/start/>

```shell
curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-latest.x86_64.rpm
sudo rpm -Uvh minikube-latest.x86_64.rpm
```

### Known Issues

> <https://minikube.sigs.k8s.io/docs/drivers/podman/#known-issues>

Podman requires passwordless running of sudo.

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
