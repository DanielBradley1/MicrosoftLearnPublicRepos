<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/cloudpcbulkmodifydiskencryptiontype?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-04-23 -->

# cloudPcBulkModifyDiskEncryptionType resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Defines the disk encryption type to apply to a collection of Cloud PCs.

Inherits from [cloudPcBulkAction](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcbulkaction?view=graph-rest-beta).

## Methods

None.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| diskEncryptionType | [cloudPcDiskEncryptionType](#cloudpcdiskencryptiontype-values) | Indicates the disk encryption type that is specific to an individual Cloud PC. The possible values are: `platformManagedKey`, `customerManagedKey`. |
| cloudPcIds | String collection | IDs of the Cloud PCs the bulk action applies to. Inherited from [cloudPcBulkAction](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcbulkaction?view=graph-rest-beta). |
| createdDateTime | DateTimeOffset | The date and time when the bulk action was created. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. Inherited from [cloudPcBulkAction](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcbulkaction?view=graph-rest-beta). |
| diskEncryptionType | [cloudPcDiskEncryptionType](#cloudpcdiskencryptiontype-values) | Indicates the disk encryption type of the Cloud PC. The possible values are: `platformManagedKey`, `customerManagedKey`. |
| displayName | String | Name of the bulk action. Inherited from [cloudPcBulkAction](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcbulkaction?view=graph-rest-beta). |
| id | String | ID of the bulk action. Inherited from [cloudPcBulkAction](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcbulkaction?view=graph-rest-beta). |

### cloudPcDiskEncryptionType values

| Member | Description |
| :--- | :--- |
| platformManagedKey | Default. Indicates that the Cloud PC disk is encrypted with a platform-managed key. |
| customerManagedKey | Indicates that the Cloud PC disk is encrypted with a customer-managed key. |
| unknownFutureValue | Evolvable enumeration sentinel value. Don't use. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.cloudPcBulkModifyDiskEncryptionType",
  "diskEncryptionType": "customerManagedKey",
  "cloudPcIds": ["*"],
  "createdDateTime": "2023-08-10T09:27:06.1351438-07:00",
  "displayName": "Change disk encryption type of tenant's CPCs",
  "id": "1d164206-bf41-4fd2-8424-a3192d392273"
}
```
