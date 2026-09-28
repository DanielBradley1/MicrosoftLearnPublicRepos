<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-windowsuniversalappxappassignmentsettings?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# windowsUniversalAppXAppAssignmentSettings resource type

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Contains properties used when assigning a Windows Universal AppX mobile app to a group.

Inherits from [mobileAppAssignmentSettings](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobileappassignmentsettings?view=graph-rest-1.0)

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| useDeviceContext | Boolean | If true, uses device execution context for Windows Universal AppX mobile app. Device-context install is not allowed when this type of app is targeted with Available intent. Defaults to false. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.windowsUniversalAppXAppAssignmentSettings",
  "useDeviceContext": true
}
```
