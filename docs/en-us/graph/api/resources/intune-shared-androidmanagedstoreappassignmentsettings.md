<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-androidmanagedstoreappassignmentsettings?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# androidManagedStoreAppAssignmentSettings resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Contains properties used to assign an Android Managed Store mobile app to a group.

Inherits from [mobileAppAssignmentSettings](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-mobileappassignmentsettings?view=graph-rest-beta)

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| androidManagedStoreAppTrackIds | String collection | The track IDs to enable for this app assignment. |
| autoUpdateMode | [androidManagedStoreAutoUpdateMode](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-androidmanagedstoreautoupdatemode?view=graph-rest-beta) | The prioritization of automatic updates for this app assignment. The possible values are: `default`, `postponed`, `priority`, `unknownFutureValue`. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.androidManagedStoreAppAssignmentSettings",
  "androidManagedStoreAppTrackIds": [
    "String"
  ],
  "autoUpdateMode": "String"
}
```
