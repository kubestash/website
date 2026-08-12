---
title: Install KubeStash using YAML
description: Install KubeStash using YAML
menu:
  docs_v2026.8.12-rc.0:
    identifier: install-kubestash-yaml
    name: YAML
    parent: install-kubestash-enterprise
    weight: 20
product_name: kubestash
menu_name: docs_v2026.8.12-rc.0
section_menu_id: setup
info:
  cli: v0.28.0-rc.0
  installer: v2026.8.12-rc.0
  version: v2026.8.12-rc.0
---

# Using YAML

If you prefer to not use Helm, you can generate YAMLs from KubeStash chart and deploy using `kubectl`. Here we are going to show the procedure using Helm 3.

## Get a Free License

Download a FREE license from [AppsCode License Server](https://appscode.com/issue-license?p=stash) before you begin. You can also automate this from your CI/CD pipeline using the [offline license server](https://github.com/appscode/offline-license-server#offline-license-server).

```bash
$ helm template kubestash oci://ghcr.io/appscode-charts/kubestash \
        --version {{< param "info.version" >}} \
        --namespace stash --create-namespace \
        --set-file global.license=/path/to/the/license.txt | kubectl apply -f -
```

To see the detailed configuration options, visit [here](https://github.com/kubestash/installer/tree/{{< param "info.version" >}}/charts/kubestash).

Next: [verify the installation](/docs/v2026.8.12-rc.0/setup/install/kubestash/configuration).
