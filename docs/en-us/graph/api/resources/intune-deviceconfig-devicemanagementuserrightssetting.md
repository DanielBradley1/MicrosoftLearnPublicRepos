<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-devicemanagementuserrightssetting?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# deviceManagementUserRightsSetting resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Represents a user rights setting.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| state | [stateManagementSetting](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-statemanagementsetting?view=graph-rest-beta) | Representing the current state of this user rights setting. Possible values are: `notConfigured`, `blocked`, `allowed`. |
| localUsersOrGroups | [deviceManagementUserRightsLocalUserOrGroup](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-devicemanagementuserrightslocaluserorgroup?view=graph-rest-beta) collection | Representing a collection of local users or groups which will be set on device if the state of this setting is Allowed. This collection can contain a maximum of 500 elements. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.deviceManagementUserRightsSetting",
  "state": "String",
  "localUsersOrGroups": [
    {
      "@odata.type": "microsoft.graph.deviceManagementUserRightsLocalUserOrGroup",
      "name": "String",
      "description": "String",
      "securityIdentifier": "String"
    }
  ]
}
```
