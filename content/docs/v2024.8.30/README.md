---
title: Welcome | KubeStash
description: Welcome to KubeStash
menu:
  docs_v2024.8.30:
    identifier: readme-kubestash
    name: Readme
    parent: welcome
    weight: -1
product_name: kubestash
menu_name: docs_v2024.8.30
section_menu_id: welcome
url: /docs/v2024.8.30/welcome/
aliases:
- /docs/v2024.8.30/
- /docs/v2024.8.30/README/
info:
  cli: v0.11.0
  installer: v2024.8.30
  version: v2024.8.30
---

# KubeStash

[KubeStash](https://kubestash.com) by AppsCode is a cloud native data backup and recovery solution for Kubernetes workloads. If you are running production workloads in Kubernetes, you might want to take backup of your disks, databases etc. Traditional tools are too complex to set up and maintain in a dynamic compute environment like Kubernetes. KubeStash is a Kubernetes operator that uses [restic](https://github.com/restic/restic) or Kubernetes CSI Driver VolumeSnapshotter functionality to address these issues. Using KubeStash, you can backup Kubernetes volumes mounted in workloads, stand-alone volumes and databases. Users may even extend KubeStash via [addons](https://kubestash.com/docs/{{< param "info.version" >}}/guides/addons/overview/) for any custom workload.

Here, we are going to give you an overview of KubeStash documentation structure.

## [Concepts](/docs/v2024.8.30/concepts/)

Concept explains some significant aspect of KubeStash. This is where you can learn about what KubeStash does and how it does it.

- [KubeStash Overview](/docs/v2024.8.30/concepts/what-is-kubestash/overview/) Provides an introduction to KubeStash and gives an overview of the features it provides.
- [KubeStash Architecture](/docs/v2024.8.30/concepts/what-is-kubestash/architecture/) Provides an overview of KubeStash architecture, and it's core components.
- [KubeStash API](/docs/v2024.8.30/concepts/crds/backupstorage/) Introduces KubeStash CRDs.

## [Setup](/docs/v2024.8.30/setup/)

Setup contains instruction for installing, uninstalling, and upgrading KubeStash.

- **Install KubeStash:** Provides installation instructions for KubeStash and its various components.
  - [KubeStash](/docs/v2024.8.30/setup/install/kubestash/): Provides installation instructions for KubeStash.
  - [kubeStash kubectl Plugin](/docs/v2024.8.30/setup/install/kubectl-plugin/): Provides installation instructions for KubeStash `kubectl` plugin.
  - [Troubleshooting](/docs/v2024.8.30/setup/install/troubleshooting/): Provides troubleshooting guide for various installation problems.
- **Uninstall KubeStash:** Provides uninstallation instructions for KubeStash and its various components.
  - [KubeStash](/docs/v2024.8.30/setup/uninstall/kubestash/): Provides uninstallation instructions for KubeStash.
  - [KubeStash kubectl Plugin](/docs/v2024.8.30/setup/uninstall/kubectl-plugin/): Provides uninstallation instructions for KubeStash `kubectl` plugin.
- [Upgrade KubeStash](/docs/v2024.8.30/setup/upgrade/): Provides instruction for updating KubeStash license and upgrading between various KubeStash versions.

## [Guides](/docs/v2024.8.30/guides/)

Guides show how to perform different operations with KubeStash.

- [Supported Backends](/docs/v2024.8.30/guides/backends/overview/): Describes how to configure different storage for storing backed up data.
- [Workload Volume Backup](/docs/v2024.8.30/guides/workloads/overview/): Shows how to use KubeStash to backup and restore volumes of a workload (i.e. `Deployment`, `StatefulSet`, `DaemonSet`, etc).
- [Stand-alone Volume Backup](/docs/v2024.8.30/guides/volumes/overview/): Shows how to use KubeStash to backup and restore stand-alone volumes(i.e. `PersistentVolumeClaim`).
- [Auto Backup](/docs/v2024.8.30/guides/auto-backup/overview/): Shows how to configure automatic backup of any stateful workload in your cluster.
- [Volume Snapshot](/docs/v2024.8.30/guides/volumesnapshot/overview/): Shows how KubeStash takes snapshot of `PersistentVolumeClaim`s and restore them from snapshot using Kubernetes `VolumeSnapshot` API.
- [Platforms](/docs/v2024.8.30/guides/platforms/eks-irsa/): Shows how to use KubeStash to backup and restore volumes of a Kubernetes workload running in different platforms.
- [Hooks](/docs/v2024.8.30/guides/hooks/overview/): Shows how to execute different actions before/after the backup/restore process.
- [CLI](/docs/v2024.8.30/guides/cli/kubectl-plugin/): Shows how to manage KubeStash objects quickly and easily using KubeStash `kubectl` plugin.
- [Security](/docs/v2024.8.30/guides/security/rbac/): Describes different built-in cluster security support by KubeStash.

We're always looking for help improving our documentation, so please don't hesitate to [file an issue](https://github.com/kubestash/project/issues/new) if you see some problem.
