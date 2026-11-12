---
title: Business Continuity and Disaster Recovery
description: Business Continuity Plan (BCP) and Disaster Recovery (DR) with online DR readiness.
menu:
  main:
    parent: features
    name: Business Continuity and Disaster Recovery
    weight: 30
---

# Business Continuity and Disaster Recovery

KubeStash provides a complete Business Continuity Plan (BCP) and Disaster Recovery (DR) solution with online DR readiness for Kubernetes workloads and databases. `BackupBlueprint` standardizes how every workload is protected, `RetentionPolicy` enforces the long-term retention windows that BCP frameworks require, and `BackupVerifier` proves recoverability on a schedule. A `RestoreSession` can target a separate cluster, so the DR site is online and ready to be promoted at any time. Combined with engine-level high availability from KubeDB, the result is an always-ready DR posture with defined RPO and RTO.

## Related concepts

- [BackupConfiguration](/docs/latest/concepts/crds/backupconfiguration/)
- [BackupBlueprint](/docs/latest/concepts/crds/backupblueprint/)
- [RestoreSession](/docs/latest/concepts/crds/restoresession/)
- [RetentionPolicy](/docs/latest/concepts/crds/retentionpolicy/)
- [BackupVerifier](/docs/latest/concepts/crds/backupverifier/)
