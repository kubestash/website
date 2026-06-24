---
title: Concepts | KubeStash
menu:
  docs_v2024.9.30:
    identifier: concepts-readme
    name: README
    parent: concepts
    weight: -1
product_name: kubestash
menu_name: docs_v2024.9.30
section_menu_id: concepts
url: /docs/v2024.9.30/concepts/
aliases:
- /docs/v2024.9.30/concepts/README/
info:
  cli: v0.12.0
  installer: v2024.9.30
  version: v2024.9.30
---

# Concepts

Concepts help you to learn about the different parts of the KubeStash and the abstractions it uses.

This concept section is divided into the following modules:

## What is KubeStash?
- [Overview](/docs/v2024.9.30/concepts/what-is-kubestash/overview/) provides an introduction to KubeStash. It also gives an overview of the features it provides.
- [Architecture](/docs/v2024.9.30/concepts/what-is-kubestash/architecture/) provides a visual representation of KubeStash architecture. It also provides a brief overview of the components it uses.

## Declarative API
- [BackupStorage](/docs/v2024.9.30/concepts/crds/backupstorage/) introduces the concept of `BackupStorage` crd that holds the backend information in a Kubernetes native way where the backed up data of different applications will be stored.
- [Repository](/docs/v2024.9.30/concepts/crds/repository/) introduces the concept of `Repository` crd that holds backup information for a specific application.
- [BackupConfiguration](/docs/v2024.9.30/concepts/crds/backupconfiguration/) introduces the concept of `BackupConfiguration` crd that is used to configure backup for a target application in a Kubernetes native way.
- [BackupSession](/docs/v2024.9.30/concepts/crds/backupsession/) introduces the concept of `BackupSession` crd that represents a backup run triggered for a session of a `BackupConfiguration` for a target application.
- [RestoreSession](/docs/v2024.9.30/concepts/crds/restoresession/) introduces the concept of `RestoreSession` crd that represents a restore run for a target application.
- [HookTemplate](/docs/v2024.9.30/concepts/crds/hooktemplate/) introduces the concept of `HookTemplate` crd that represents a template for an action that will be executed before or/and after backup/restore process.
- [Addon](/docs/v2024.9.30/concepts/crds/addon/) introduces the concept of `Addon` crd which represents the backup and restore capabilities for a specific type of target.
- [Function](/docs/v2024.9.30/concepts/crds/function/) introduces the concept of `Function` crd that represents a task of a backup or restore process.
- [BackupBlueprint](/docs/v2024.9.30/concepts/crds/backupblueprint/) introduces the concept of `BackupBlueprint` crd that represents a blueprint for `BackupConfiguration` objects. It allows for the automatic creation of `BackupConfiguration`s for similar targets based on the blueprint.
- [Snapshot](/docs/v2024.9.30/concepts/crds/snapshot/) introduces the concept of `Snapshot` crd which represents the state of a backup run for one or more components of an application.
- [RetentionPolicy](/docs/v2024.9.30/concepts/crds/retentionpolicy/) introduces the concept of `RetentionPolicy` crd that represents how the old `Snapshots` should be cleaned up.
