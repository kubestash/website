---
title: Install KubeStash
description: Installation guide for KubeStash
menu:
  docs_v2026.6.18-rc.2:
    identifier: install-kubestash-enterprise
    name: KubeStash
    parent: installation-guide
    weight: 20
product_name: kubestash
menu_name: docs_v2026.6.18-rc.2
section_menu_id: setup
info:
  cli: v0.27.0-rc.2
  installer: v2026.6.18-rc.2
  version: v2026.6.18-rc.2
---

# Install KubeStash

## Get a Free License

Download a FREE license from [AppsCode License Server](https://appscode.com/issue-license?p=stash).

> KubeStash licensing process has been designed to work with CI/CD workflow. You can automatically obtain a license from your CI/CD pipeline by following the guide from [here](https://github.com/appscode/offline-license-server#offline-license-server).

## Choose an Installation Method

KubeStash can be installed in several ways. Pick the one that fits your workflow:

- [Helm 3](/docs/v2026.6.18-rc.2/setup/install/kubestash/helm) — recommended for most users.
- [YAML](/docs/v2026.6.18-rc.2/setup/install/kubestash/yaml) — render manifests and apply with `kubectl`.
- [ArgoCD](/docs/v2026.6.18-rc.2/setup/install/kubestash/argocd) — GitOps via ArgoCD `Application` resources.
- [FluxCD](/docs/v2026.6.18-rc.2/setup/install/kubestash/fluxcd) — GitOps via the Flux Helm Controller.
- [OpenShift](/docs/v2026.6.18-rc.2/setup/install/kubestash/openshift) — standard chart or Red Hat certified chart.

After installing, see [Common Configuration](/docs/v2026.6.18-rc.2/setup/install/kubestash/configuration) to verify the installation.

## Purchase KubeStash License

If you are interested in purchasing KubeStash license, please contact us via sales@appscode.com for further discussion. You can also set up a meeting via our [calendly link](https://calendly.com/appscode/intro).

If you are willing to purchase KubeStash license but need more time to test in your dev cluster, feel free to contact sales@appscode.com. We will be happy to extend your trial period.
