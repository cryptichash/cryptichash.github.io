---
title: "Kubernetes"
linkTitle: "Kubernetes"
weight: 2
date: 2023-06-04
description: >
  Kubernetes
---

## minikube
> https://minikube.sigs.k8s.io/docs/

### Create Cluster

* Driver
  * podman
    * https://minikube.sigs.k8s.io/docs/drivers/podman/
* Container runtime
  * cri-o
    * https://minikube.sigs.k8s.io/docs/drivers/podman/#usage
    * https://minikube.sigs.k8s.io/docs/runtimes/cri-o/
* CNI
  * cilium
    * https://docs.cilium.io/en/stable/gettingstarted/k8s-install-default/#create-cluster
    * https://kubernetes.io/docs/tasks/administer-cluster/network-policy-provider/cilium-network-policy/

```shell
minikube start --driver=podman --container-runtime=cri-o --cni=cilium
```

### Commands
> https://minikube.sigs.k8s.io/docs/commands/

Pause Kubernetes without impacting deployed applications:
```shell
minikube pause
```
Unpause a paused instance:
```shell
minikube unpause
```

Halt the cluster:
```shell
minikube stop
```

List clusters:
```shell
minikube profile list
```

Delete cluster:
```shell
minikube delete -p <profile-name>
```