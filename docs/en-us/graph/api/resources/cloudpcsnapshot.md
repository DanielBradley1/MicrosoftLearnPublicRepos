<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/cloudpcsnapshot?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-10-22 -->

# cloudPcSnapshot resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a snapshot of the device settings of a Cloud PC that can be used to restore the device system. The background service runs periodically or can be manually triggered by a user to take a snapshot for disaster recovery or restore purposes.

To learn more about how to provision a new Cloud PC with an imported snapshot, see [cloudPCSnapshot: importSnapshot](https://learn.microsoft.com/en-us/graph/api/cloudpcsnapshot-importsnapshot?view=graph-rest-beta).

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Import snapshot](https://learn.microsoft.com/en-us/graph/api/cloudpcsnapshot-importsnapshot?view=graph-rest-beta) | [cloudPcSnapshotImportActionResult](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcsnapshotimportactionresult?view=graph-rest-beta) | Import the [snapshot](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcsnapshot?view=graph-rest-beta) from the customer-managed storage account using the provided information, and store it in the Azure storage account within the Cloud PC service on behalf of the customer. |
| [Purge imported snapshot](https://learn.microsoft.com/en-us/graph/api/cloudpcsnapshot-purgeimportedsnapshot?view=graph-rest-beta) | None | Purge \(delete\) the unused imported [snapshot](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcsnapshot?view=graph-rest-beta) from the Windows 365 service-managed storage account. |
| [Retrieve imported snapshots](https://learn.microsoft.com/en-us/graph/api/cloudpcsnapshot-retrievesnapshotimportresults?view=graph-rest-beta) | [cloudPcSnapshotImportActionResult](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcsnapshotimportactionresult?view=graph-rest-beta) | Retrieve the result and status of the [snapshot](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcsnapshot?view=graph-rest-beta) import action. |
| [Retrieve snapshots](https://learn.microsoft.com/en-us/graph/api/cloudpc-retrievesnapshots?view=graph-rest-beta) | [cloudPcSnapshot](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcsnapshot?view=graph-rest-beta) collection | Get a list of [cloudPcSnapshot](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcsnapshot?view=graph-rest-beta) resources for a Cloud PC. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| cloudPcId | String | The unique identifier for the Cloud PC. |
| createdDateTime | DateTimeOffset | The date and time at which the snapshot was taken. The timestamp is shown in ISO 8601 format and Coordinated Universal Time \(UTC\). For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |
| expirationDateTime | DateTimeOffset | The date and time when the snapshot expires. The timestamp is shown in ISO 8601 format and Coordinated Universal Time \(UTC\). For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |
| healthCheckStatus | [cloudPcSnapshotHealthCheckStatus](#cloudpcsnapshothealthcheckstatus-values) | Indicates the health check status of the Cloud PC snapshot. The possible values are: `unknown`, `healthy`, `unhealthy`, `unknownFutureValue`. The default value is `unknown`. Read-only. Nullable. |
| id | String | The unique identifier for the snapshot of the Cloud PC device at a specific point in time. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). |
| lastRestoredDateTime | DateTimeOffset | The date and time at which the snapshot was last used to restore the Cloud PC device. The timestamp is shown in ISO 8601 format and Coordinated Universal Time \(UTC\). For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |
| snapshotType | [cloudPcSnapshotType](#cloudpcsnapshottype-values) | The type of snapshot that indicates how to create the snapshot. Possible values are `automatic`, `manual`, `unknownFutureValue`, `retention`. Use the `Prefer: include-unknown-enum-members` request header to get the following members from this [evolvable enum](https://learn.microsoft.com/en-us/graph/best-practices-concept#handling-future-members-in-evolvable-enumerations): `retention`. The default value is `automatic`. |
| status | [cloudPcSnapshotStatus](#cloudpcsnapshotstatus-values) | The status of the Cloud PC snapshot. The possible values are: `ready`, `unknownFutureValue`. |

### cloudPcSnapshotHealthCheckStatus values

| Member | Description |
| :--- | :--- |
| unknown | Default. Indicates that both the session host and virtual machine agent connectivity statuses are unknown. |
| healthy | Indicates that the Cloud PC snapshot is healthy to use. For example, the Cloud PC snapshot is healthy if either the connectivity status of the session host or the virtual machine agent is healthy, or if the virtual machine itself is unreachable due to shutdown or deallocation. |
| unhealthy | Indicates that the Cloud PC snapshot is unhealthy to use. For example, the Cloud PC snapshot is unhealthy if both the connectivity status of the session host and the virtual machine agent are unhealthy. |
| unknownFutureValue | Evolvable enumeration sentinel value. Don't use. |

### cloudPcSnapshotStatus values

| Member | Description |
| :--- | :--- |
| ready | The snapshot is ready to restore the Cloud PC device. |
| unknownFutureValue | Evolvable enumeration sentinel value. Don't use. |

### cloudPcSnapshotType values

| Member | Description |
| :--- | :--- |
| automatic | Indicates that Windows 365 regularly creates snapshots automatically. |
| manual | Indicates that the customer manually creates snapshots. |
| unknownFutureValue | Evolvable enumeration sentinel value. Don't use. |
| retention | Indicates that the snapshot is a retention snapshot. If a Cloud PC is about to be deprovisioned \(manually, due to license expiration, and so on\), a snapshot of the Cloud PC is taken as a retention snapshot. It's stored in a Microsoft-managed, limited-function storage account for 90 days. During this period, customers can extract the data or use it to provision a new Cloud PC. After the 90-day retention period, Microsoft disables the account and deletes the customer data. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.cloudPcSnapshot",
  "cloudPcId": "String",
  "createdDateTime": "String (timestamp)",
  "expirationDateTime": "String (timestamp)",
  "healthCheckStatus": "String",
  "id": "String (identifier)",
  "lastRestoredDateTime": "String (timestamp)",
  "snapshotType": "String",
  "status": "String"
}
```
