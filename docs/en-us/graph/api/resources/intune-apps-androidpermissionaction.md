<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-androidpermissionaction?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# androidPermissionAction resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Mapping between an Android app permission and the action Android should take when that permission is requested.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| permission | String | Android permission string, defined in the official Android documentation. Example 'android.permission.READ\_CONTACTS'. |
| action | [androidPermissionActionType](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-androidpermissionactiontype?view=graph-rest-beta) | Type of Android permission action. Possible values are: `prompt`, `autoGrant`, `autoDeny`. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.androidPermissionAction",
  "permission": "String",
  "action": "String"
}
```
