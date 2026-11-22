---
title: Comprehensively Documented Backup and Restoration Procedures
description: All backup and restoration procedures comprehensively documented through declarative CRDs.
menu:
  main:
    parent: features
    name: Comprehensively Documented Backup and Restoration Procedures
    weight: 70
---

# Comprehensively Documented Backup and Restoration Procedures

KubeStash documents all backup and restoration procedures comprehensively, by collapsing procedure and configuration into the same artifact: a Kubernetes Custom Resource Definition (CRD). Every backup schedule, restore plan, retention rule, pre and post hook, verification cadence, and disaster recovery drill is expressed as a `BackupConfiguration`, `RestoreSession`, `RetentionPolicy`, `HookTemplate`, `BackupVerifier`, or `BackupBlueprint` object. These YAML manifests live in Git, are reviewed in pull requests, and are applied via GitOps. The documentation is the configuration, which means it cannot drift from reality.

## Related concepts

- [BackupConfiguration](/docs/latest/concepts/crds/backupconfiguration/)
- [BackupBlueprint](/docs/latest/concepts/crds/backupblueprint/)
- [RestoreSession](/docs/latest/concepts/crds/restoresession/)
- [RetentionPolicy](/docs/latest/concepts/crds/retentionpolicy/)
- [BackupVerifier](/docs/latest/concepts/crds/backupverifier/)
