---
title: Install KubeStash using YAML
description: Install KubeStash using YAML
menu:
  docs_v2026.6.18-rc.2:
    identifier: install-kubestash-yaml
    name: YAML
    parent: install-kubestash-enterprise
    weight: 20
product_name: kubestash
menu_name: docs_v2026.6.18-rc.2
section_menu_id: setup
info:
  cli: v0.27.0-rc.2
  installer: v2026.6.18-rc.2
  version: v2026.6.18-rc.2
---

# Using YAML

If you prefer to not use Helm, you can generate YAMLs from KubeStash chart and deploy using `kubectl`. Here we are going to show the procedure using Helm 3.

```bash
$ helm template kubestash oci://ghcr.io/appscode-charts/kubestash \
        --version {{< param "info.version" >}} \
        --namespace stash --create-namespace \
        --set-file global.license=/path/to/the/license.txt | kubectl apply -f -
```

To see the detailed configuration options, visit [here](https://github.com/kubestash/installer/tree/master/charts/kubestash).

Next: [verify the installation](/docs/v2026.6.18-rc.2/setup/install/kubestash/configuration).
