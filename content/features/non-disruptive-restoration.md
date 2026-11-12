---
title: Non-Disruptive Restoration
description: Restore data without impacting application performance or response time.
menu:
  main:
    parent: features
    name: Non-Disruptive Restoration
    weight: 20
---

# Non-Disruptive Restoration

KubeStash restores data without impacting application performance or response time. A `RestoreSession` does not have to overwrite the source. The default and recommended pattern is to restore into an alternate namespace, PVC, or even a separate cluster, validate integrity, and only then cut traffic over. Because the live production workload is never touched during recovery, response time and throughput remain at steady state. `BackupVerifier` runs scheduled, isolated restore drills against every backup, providing continuous evidence that any snapshot is fully recoverable, again without disturbing production.

## Related concepts

- [BackupConfiguration](/docs/latest/concepts/crds/backupconfiguration/)
- [BackupBlueprint](/docs/latest/concepts/crds/backupblueprint/)
- [RestoreSession](/docs/latest/concepts/crds/restoresession/)
- [RetentionPolicy](/docs/latest/concepts/crds/retentionpolicy/)
- [BackupVerifier](/docs/latest/concepts/crds/backupverifier/)
