---
title: Active-Active Data Replication between Primary and DR Sites
description: Real-time, secure data replication between primary DC and DR sites in active-active mode.
menu:
  main:
    parent: features
    name: Active-Active Data Replication between Primary and DR Sites
    weight: 40
---

# Active-Active Data Replication between Primary and DR Sites

KubeStash supports real-time and secure data replication between the primary data center (DC) and the disaster recovery (DR) site operating in active-active mode. Backup snapshots are replicated across multiple `BackupStorage` targets simultaneously, so the same logical snapshot is materialized in DC, DR, and any Near-DR site. For the live data path, KubeStash works together with KubeDB, which provides engine-native synchronous multi-master replication (MySQL Group Replication, Galera, MongoDB cross-region replica sets, PostgreSQL Patroni stretched clusters). Both sites remain authoritative and writable, with RPO near zero. Data in transit is encrypted end to end.

## Related concepts

- [BackupConfiguration](/docs/latest/concepts/crds/backupconfiguration/)
- [BackupBlueprint](/docs/latest/concepts/crds/backupblueprint/)
- [RestoreSession](/docs/latest/concepts/crds/restoresession/)
- [RetentionPolicy](/docs/latest/concepts/crds/retentionpolicy/)
- [BackupVerifier](/docs/latest/concepts/crds/backupverifier/)
