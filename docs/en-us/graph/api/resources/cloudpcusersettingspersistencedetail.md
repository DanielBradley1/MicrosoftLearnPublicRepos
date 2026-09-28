<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/cloudpcusersettingspersistencedetail?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-11-18 -->

# cloudPCUserSettingsPersistenceDetail resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the configuration that indicates whether Cloud PC user settings persistence is enabled. When enabled, Windows 365 saves user-specific application data in a central cloud storage location and reconnects the user to that storage upon each connection.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Batch delete user settings persistence profile](https://learn.microsoft.com/en-us/graph/api/cloudpcusersettingspersistencedetail-batchcleanupusersettingspersistenceprofile?view=graph-rest-beta) | None | Delete a list of selected [user settings persistence](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcusersettingspersistencedetail?view=graph-rest-beta) profiles that aren't attached to a specific user's Cloud PC in the Cloud PC policy assignment. |
| [Retrieve user settings persistence profiles](https://learn.microsoft.com/en-us/graph/api/cloudpcusersettingspersistencedetail-retrieveusersettingspersistenceprofiles?view=graph-rest-beta) | [cloudPCUserSettingsPersistenceProfile](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcusersettingspersistenceprofile?view=graph-rest-beta) collection | Retrieve the user storage list for Cloud PC [user settings persistence](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcusersettingspersistencedetail?view=graph-rest-beta) under the selected Cloud PC policy assignment. |
| [Retrieve user settings persistence usage](https://learn.microsoft.com/en-us/graph/api/cloudpcusersettingspersistencedetail-retrieveusersettingspersistenceprofileusage?view=graph-rest-beta) | [cloudPCUserSettingsPersistenceUsageResult](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcusersettingspersistenceusageresult?view=graph-rest-beta) | Retrieve the usage of Cloud PC [user settings persistence](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcusersettingspersistencedetail?view=graph-rest-beta) in the selected Cloud PC policy assignment. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| gracePeriodEndDateTime | DateTimeOffset | Indicates the grace period end time when user settings persistence exceeds the available quota. If usage exceeds the available quota when the grace period expires, the system automatically deletes the profile with the oldest last attached timestamp. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. Read-only. |
| id | String | Indicates the unique identifier for the Cloud PC user settings persistence configuration for a single policy collection. Required. Read-only. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.cloudPCUserSettingsPersistenceDetail",
  "id": "String (identifier)",
  "gracePeriodEndDateTime": "String (timestamp)"
}
```
