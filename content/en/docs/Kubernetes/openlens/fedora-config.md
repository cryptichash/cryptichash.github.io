---
title: "Fedora Config"
date: 2023-06-03
weight: 5
description: >
  Fedora Config for OpenLens
---

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
