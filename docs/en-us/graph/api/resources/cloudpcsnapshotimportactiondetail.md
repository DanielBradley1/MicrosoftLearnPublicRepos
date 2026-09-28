<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/cloudpcsnapshotimportactiondetail?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-10-22 -->

# cloudPcSnapshotImportActionDetail resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the required detailed information to start the [snapshot](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcsnapshot?view=graph-rest-beta) import action. The user must provide either Azure storage information or a shared access signature URL for the snapshot file. If both are provided, Azure storage information takes priority.

This file is a .vhd virtual hard disk format.

## Properties

| Property | Type | Description |
| --- | --- | --- |
| fileType | [cloudPcSnapshotImportFileType](#cloudpcsnapshotimportfiletype-values) | The file type of the imported virtual hard disk file. The possible values are: `dataFile`, `virtualMachineGuestState`, `unknownFutureValue`. The default value is `dataFile`. |
| sasUrl | String | The shared access signature URL of the snapshot import action. |
| sourceType | [cloudPcSnapshotImportSourceType](#cloudpcsnapshotimportsourcetype-values) | The source type of the snapshot import action. The possible values are: `azureStorageAccount`, `sasUrl`, `unknownFutureValue`. The default value is `azureStorageAccount`. |
| storageBlobInfo | [cloudPcStorageBlobDetail](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcstorageblobdetail?view=graph-rest-beta) | The storage account information of the snapshot import action. |

### cloudPcSnapshotImportSourceType values

| Member | Description |
| :--- | :--- |
| azureStorageAccount | Indicates that the snapshot uploads from an Azure storage account. |
| sasUrl | Indicates that the snapshot uploads via a shared access signature URL. |
| unknownFutureValue | Evolvable enumeration sentinel value. Don't use. |

### cloudPcSnapshotImportFileType values

| Member | Description |
| :--- | :--- |
| dataFile | Indicates that the file serves as a data file. |
| virtualMachineGuestState | Indicates that the file is a virtual machine guest state file \(VMGS\), specific to trusted launch VMs. It's a blob managed by Azure and contains the Unified Extensible Firmware Interface \(UEFI\) secure boot signature databases and other security information. |
| unknownFutureValue | Evolvable enumeration sentinel value. Don't use. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.cloudPcSnapshotImportActionDetail",
  "fileType": "String",
  "sasUrl": "String",
  "sourceType": "String",
  "storageBlobInfo": {"@odata.type": "microsoft.graph.cloudPcStorageBlobDetail"}
}
```
