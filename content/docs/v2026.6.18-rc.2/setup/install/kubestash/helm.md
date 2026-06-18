---
title: Install KubeStash using Helm 3
description: Install KubeStash using Helm 3
menu:
  docs_v2026.6.18-rc.2:
    identifier: install-kubestash-helm
    name: Helm 3
    parent: install-kubestash-enterprise
    weight: 10
product_name: kubestash
menu_name: docs_v2026.6.18-rc.2
section_menu_id: setup
info:
  cli: v0.27.0-rc.2
  installer: v2026.6.18-rc.2
  version: v2026.6.18-rc.2
---

# Using Helm 3

KubeStash can be installed via [Helm](https://helm.sh/) using the [chart](https://github.com/kubestash/installer/tree/master/charts/kubestash) from [AppsCode Charts Repository](https://github.com/appscode/charts). To install the chart with the release name `kubestash`:

```bash
$ helm install kubestash oci://ghcr.io/appscode-charts/kubestash \
        --version {{< param "info.version" >}} \
        --namespace stash --create-namespace \
        --set-file global.license=/path/to/the/license.txt \
        --wait --burst-limit=10000 --debug
```

To see the detailed configuration options, visit [here](https://github.com/kubestash/installer/tree/master/charts/kubestash).

Next: [verify the installation](/docs/v2026.6.18-rc.2/setup/install/kubestash/configuration).
