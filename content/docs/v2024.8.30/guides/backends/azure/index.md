---
title: Azure Backend | KubeStash
description: Configure KubeStash to use Microsoft Azure Storage as Backend.
menu:
  docs_v2024.8.30:
    identifier: backend-azure
    name: Azure Blob Storage
    parent: backend
    weight: 40
product_name: kubestash
menu_name: docs_v2024.8.30
section_menu_id: guides
info:
  cli: v0.11.0
  installer: v2024.8.30
  version: v2024.8.30
---

# Microsoft Azure Storage

KubeStash supports Microsoft's [Azure Blob Storage](https://azure.microsoft.com/en-us/services/storage/blobs/) as a backend. This tutorial will show you how to use this backend.

In order to use Azure Blob Storage as backend, you have to create a `Secret` and a `BackupStorage` object pointing to the desired blob container.

#### Create Storage Secret

To configure storage secret for this backend, following secret keys are needed:

|         Key          |    Type    |                        Description                         |
| -------------------- | ---------- | ---------------------------------------------------------- |
| `AZURE_ACCOUNT_KEY`  | `Required` | Azure Storage account key                                  |

Create storage secret as below,

```bash
$ echo -n '<your-azure-storage-account-key>' > AZURE_ACCOUNT_KEY
$ kubectl create secret generic -n demo azure-secret \
    --from-file=./AZURE_ACCOUNT_KEY
secret/azure-secret created
```

### Create BackupStorage

Now, you have to create a `BackupStorage` cr. You have to specify the name of the storage secret that we have created earlier in the `spec.storage.azure.secretName` field.

Following parameters are available for `azure` backend.

| Parameter              |    Type    | Description                                                                                                                             |
|------------------------| ---------- |-----------------------------------------------------------------------------------------------------------------------------------------|
| `azure.storageAccount` | `Required` | Name of the Storage account.                                                                                                            |
| `azure.container`      | `Required` | Name of Storage container.                                                                                                              |
| `azure.secretName`     | `Required` | Specify the name of the Secret that contains the access credential for this storage.                                                    |        |
| `azure.prefix`         | `Optional` | Path prefix inside the container where backed up data will be stored.                                                                   |
| `azure.maxConnections` | `Optional` | Maximum number of parallel connections to use for uploading backup data. By default, KubeStash will use maximum 5 parallel connections. |

Below, the YAML of a sample `BackupStorage` crd that uses an Azure Blob container as a backend.

```yaml
apiVersion: storage.kubestash.com/v1alpha1
kind: BackupStorage
metadata:
  name: azure-storage
  namespace: demo
spec:
  storage:
    provider: azure
    azure:
      storageAccount: kubestash
      container: kubestash-demo
      prefix: /backup/demo/deployment/kubestash-demo
      secretName: azure-secret
  usagePolicy:
    allowedNamespaces:
      from: All
  default: true
  deletionPolicy: WipeOut
```

Create the `BackupStorage` we have shown above using the following command,

```bash
$ kubectl apply -f https://github.com/kubestash/docs/raw/{{< param "info.version" >}}/docs/guides/backends/azure/examples/azure.yaml
backupstorage.storage.kubestash.com/azure-storage created
```

Now, we are ready to use this backend to backup our desired data using KubeStash.

## Next Steps

- Learn how to use KubeStash to backup workloads data from [here](/docs/v2024.8.30/guides/workloads/overview/).
- Learn how to use KubeStash to backup stand-alone PVC from [here](/docs/v2024.8.30/guides/volumes/overview/).
