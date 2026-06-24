---
title: Table of Contents | Guides
description: Table of Contents | Guides
menu:
  docs_v2025.10.17:
    identifier: guides-readme
    name: Readme
    parent: guides
    weight: -1
product_name: kubestash
menu_name: docs_v2025.10.17
section_menu_id: guides
url: /docs/v2025.10.17/guides/
aliases:
- /docs/v2025.10.17/guides/README/
info:
  cli: v0.20.0
  installer: v2025.10.17
  version: v2025.10.17
---

# Guides

Guides show how to perform different operations with KubeStash. We have divided guides section into the following sub-sections:

- [Supported Backends](/docs/v2025.10.17/guides/backends/overview/): Describes how to configure different storage for storing backed up data.
- [Workload Volume Backup](/docs/v2025.10.17/guides/workloads/overview/): Shows how to use KubeStash to backup and restore volumes of a workload (i.e. `Deployment`, `StatefulSet`, `DaemonSet`, etc).
- [Stand-alone Volume Backup](/docs/v2025.10.17/guides/volumes/overview/): Shows how to use KubeStash to backup and restore stand-alone volumes(i.e. `PersistentVolumeClaim`).
- [Auto Backup](/docs/v2025.10.17/guides/auto-backup/overview/): Shows how to configure automatic backup of any stateful workload in your cluster.
- [Volume Snapshot](/docs/v2025.10.17/guides/volumesnapshot/overview/): Shows how KubeStash takes snapshot of `PersistentVolumeClaim`s and restore them from snapshot using Kubernetes `VolumeSnapshot` API.
- [Platforms](/docs/v2025.10.17/guides/platforms/eks-irsa/): Shows how to use KubeStash to backup and restore volumes of a Kubernetes workload running in different platforms.
- [Monitoring](/docs/v2025.10.17/guides/monitoring/overview/): Shows how Prometheus monitoring works with KubeStash, what metrics KubeStash exports, and how to enable monitoring.
- [Hooks](/docs/v2025.10.17/guides/hooks/overview/): Shows how to execute different actions before/after the backup/restore process.
- [CLI](/docs/v2025.10.17/guides/cli/kubectl-plugin/): Shows how to manage KubeStash objects quickly and easily using KubeStash `kubectl` plugin.
- [Security](/docs/v2025.10.17/guides/security/rbac/): Describes different built-in cluster security support by KubeStash.
