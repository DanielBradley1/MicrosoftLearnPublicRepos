<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/cloudpcusersettingspersistenceusageresult?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-11-18 -->

# cloudPCUserSettingsPersistenceUsageResult resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the storage usage status of user settings persistence for a specific Cloud PC user settings persistence configuration and its associated policy assignment.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| remainingAvailableStorageInGB | Int32 | The remaining available preallocated user settings persistence profile storage for a specific Cloud PC policy assignment. This value equals the total preallocated storage size minus the used preallocated storage size. Required. Read-only. |
| totalAllocatedStorageInGB | Int32 | The total preallocated user settings persistence profile storage for a specific Cloud PC policy assignment. The system calculates the total size based on the number of licenses assigned to this policy and the size of each Cloud PC disk. Required. Read-only. |
| usedStorageInGB | Int32 | The total used preallocated user settings persistence storage for a specific Cloud PC policy assignment. This value represents the total allocated size for users who signed in. Required. Read-only. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.cloudPCUserSettingsPersistenceUsageResult",
  "remainingAvailableStorageInGB": "Int32",
  "totalAllocatedStorageInGB": "Int32",
  "usedStorageInGB": "Int32"
}
```
