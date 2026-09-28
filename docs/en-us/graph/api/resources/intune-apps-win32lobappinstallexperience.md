<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-win32lobappinstallexperience?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-01-08 -->

# win32LobAppInstallExperience resource type

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Contains installation experience properties for a Win32 App

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| runAsAccount | [runAsAccountType](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-runasaccounttype?view=graph-rest-1.0) | Indicates the type of execution context the app runs in. The possible values are: `system`, `user`. |
| deviceRestartBehavior | [win32LobAppRestartBehavior](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-win32lobapprestartbehavior?view=graph-rest-1.0) | Device restart behavior. The possible values are: `basedOnReturnCode`, `allow`, `suppress`, `force`. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.win32LobAppInstallExperience",
  "runAsAccount": "String",
  "deviceRestartBehavior": "String"
}
```
