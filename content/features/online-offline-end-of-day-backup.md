---
title: Online, Offline, and End-of-Day Backup
description: Online, offline, and end-of-day backup from one declarative API.
menu:
  main:
    parent: features
    name: Online, Offline, and End-of-Day Backup
    weight: 10
---

# Online, Offline, and End-of-Day Backup

KubeStash provides comprehensive online, offline, and end-of-day backup capabilities for Kubernetes workloads, databases, and persistent volumes. A single `BackupConfiguration` can run hot online captures throughout the business day for low-RPO recovery, plus an end-of-day backup at a fixed cron expression for daily checkpoints. Snapshots are written to one or more `BackupStorage` targets, including immutable / WORM-compliant tiers such as S3 Object Lock, Azure Blob immutability, GCS bucket lock, and MinIO WORM, which makes the backup effectively offline and tamper-proof even though the storage itself remains online for fast recovery.

## Related concepts

- [BackupConfiguration](/docs/latest/concepts/crds/backupconfiguration/)
- [BackupBlueprint](/docs/latest/concepts/crds/backupblueprint/)
- [RestoreSession](/docs/latest/concepts/crds/restoresession/)
- [RetentionPolicy](/docs/latest/concepts/crds/retentionpolicy/)
- [BackupVerifier](/docs/latest/concepts/crds/backupverifier/)
