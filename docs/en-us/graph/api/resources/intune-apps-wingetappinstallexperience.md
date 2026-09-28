<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-wingetappinstallexperience?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# winGetAppInstallExperience resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Represents the install experience settings associated with WinGet apps. This is used to ensure the desired install experiences on the target device are taken into account. Required at creation time.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| runAsAccount | [runAsAccountType](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-runasaccounttype?view=graph-rest-beta) | Indicates the type of execution context the app setup runs in on target devices. Options include values of the RunAsAccountType enum, which are System and User. Required at creation time, cannot be modified on existing objects. Possible values are: `system`, `user`. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.winGetAppInstallExperience",
  "runAsAccount": "String"
}
```
