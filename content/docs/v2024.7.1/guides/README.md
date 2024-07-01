---
title: Table of Contents | Guides
description: Table of Contents | Guides
menu:
  docs_v2024.7.1:
    identifier: guides-readme
    name: Readme
    parent: guides
    weight: -1
product_name: kubestash
menu_name: docs_v2024.7.1
section_menu_id: guides
url: /docs/v2024.7.1/guides/
aliases:
- /docs/v2024.7.1/guides/README/
info:
  cli: v0.9.0
  installer: v2024.7.1
  version: v2024.7.1
---

# Guides

Guides show how to perform different operations with KubeStash. We have divided guides section into the following sub-sections:

- [Supported Backends](/docs/v2024.7.1/guides/backends/overview/): Describes how to configure different storage for storing backed up data.
- [Workload Volume Backup](/docs/v2024.7.1/guides/workloads/overview/): Shows how to use KubeStash to backup and restore volumes of a workload (i.e. `Deployment`, `StatefulSet`, `DaemonSet`, etc).
- [Stand-alone Volume Backup](/docs/v2024.7.1/guides/volumes/overview/): Shows how to use KubeStash to backup and restore stand-alone volumes(i.e. `PersistentVolumeClaim`).
- [Auto Backup](/docs/v2024.7.1/guides/auto-backup/overview/): Shows how to configure automatic backup of any stateful workload in your cluster.
- [Volume Snapshot](/docs/v2024.7.1/guides/volumesnapshot/overview/): Shows how KubeStash takes snapshot of `PersistentVolumeClaim`s and restore them from snapshot using Kubernetes `VolumeSnapshot` API.
- [Platforms](/docs/v2024.7.1/guides/platforms/eks-irsa/): Shows how to use KubeStash to backup and restore volumes of a Kubernetes workload running in different platforms.
- [Hooks](/docs/v2024.7.1/guides/hooks/overview/): Shows how to execute different actions before/after the backup/restore process.
- [CLI](/docs/v2024.7.1/guides/cli/kubectl-plugin/): Shows how to manage KubeStash objects quickly and easily using KubeStash `kubectl` plugin.
- [Security](/docs/v2024.7.1/guides/security/rbac/): Describes different built-in cluster security support by KubeStash.
