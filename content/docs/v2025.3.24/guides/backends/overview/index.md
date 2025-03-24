---
title: Backend Overview | KubeStash
description: An overview of the backends used by KubeStash to store backed up data.
menu:
  docs_v2025.3.24:
    identifier: backend-overview
    name: What is Backend?
    parent: backend
    weight: 10
product_name: kubestash
menu_name: docs_v2025.3.24
section_menu_id: guides
info:
  cli: v0.16.0
  installer: v2025.3.24
  version: v2025.3.24
---

> New to KubeStash? Please start [here](/docs/v2025.3.24/concepts/README).

# KubeStash Backends

## BackupStorage

KubeStash supports various backends for storing backup data. It can be a cloud storage like GCS bucket, AWS S3, Azure Blob Storage etc. or a Kubernetes persistent volume like [HostPath](https://kubernetes.io/docs/concepts/storage/volumes/#hostpath), [PersistentVolumeClaim](https://kubernetes.io/docs/concepts/storage/volumes/#persistentvolumeclaim), [NFS](https://kubernetes.io/docs/concepts/storage/volumes/#nfs) etc.

The following diagram shows how KubeStash operator and backup container accesses and backs up data into a backend.

<figure align="center">
	<img alt="KubeStash Backend Overview" src="images/kubestash_backend_overview.svg">
  <figcaption align="center">Fig: KubeStash Backend Overview</figcaption>
</figure>

The Backend process works in the following steps:

- At first user creates a [BackupStorage](/docs/v2025.3.24/concepts/crds/backupstorage/) object that contains the backend information along with a `Secret` object containing the corresponding backend credentials required for accessing the backend.
- KubeStash operator watches for `BackupStorage` custom resources and `Secrets`. When it finds a `BackupStorage` object, it initializes the storage by uploading the `metadata.yaml` file.

Below, a screenshot that shows initialization of a `BackupStorage` in a GCS bucket named `kubestash-qa`:

<figure align="center">
  <img alt="BackupStorage initialization in GCS Backend" src="./images/backupstorage-initialize.png">
  <figcaption align="center">Fig: BackupStorage initialization in GCS Backend</figcaption>
</figure>

Here, `kubestash-qa` serves as the bucket name, and the presence of `metadata.yaml` indicates the successful initialization of the BackupStorage.

## Next Steps
- Learn how to configure `Kubernetes Volume` as backend from [here](/docs/v2025.3.24/guides/backends/local/).
- Learn how to configure `AWS S3/Minio/Rook` backend from [here](/docs/v2025.3.24/guides/backends/s3/).
- Learn how to configure `Google Cloud Storage (GCS)` backend from [here](/docs/v2025.3.24/guides/backends/gcs/).
- Learn how to configure `Microsoft Azure Storage` backend from [here](/docs/v2025.3.24/guides/backends/azure/).
