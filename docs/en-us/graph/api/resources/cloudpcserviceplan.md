<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/cloudpcserviceplan?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-07-17 -->

# cloudPcServicePlan resource type

Namespace: microsoft.graph

Represents a Windows 365 service plan that can be purchased and configured for a Cloud PC.

For examples of currently available service plans, see [Windows 365 compare plans and pricing](https://www.microsoft.com/windows-365/business/compare-plans-pricing). Currently, the Microsoft Graph API is available for Windows 365 Enterprise.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/virtualendpoint-list-serviceplans?view=graph-rest-1.0) | [cloudPcServicePlan](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcserviceplan?view=graph-rest-1.0) collection | List the currently available [service plans](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcserviceplan?view=graph-rest-1.0) that an organization can purchase for their Cloud PCs. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | The name for the service plan. Read-only. |
| id | String | Unique identifier for the service plan. Read-only. |
| ramInGB | Int32 | The size of the RAM in GB. Read-only. |
| storageInGB | Int32 | The size of the operating system disk in GB. Read-only. |
| vCpuCount | Int32 | The number of vCPUs. Read-only. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.cloudPcServicePlan",
  "displayName": "String",
  "id": "String (identifier)",
  "ramInGB": "Int32",
  "storageInGB": "Int32",
  "vCpuCount": "Int32"
}
```
