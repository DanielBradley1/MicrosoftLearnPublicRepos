<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-vpptokenactionresult?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-01-08 -->

# vppTokenActionResult resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

The status of the action performed with an Apple Volume Purchase Program token.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| actionName | String | Action name |
| actionState | [actionState](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-actionstate?view=graph-rest-beta) | State of the action. Possible values are: `none`, `pending`, `canceled`, `active`, `done`, `failed`, `notSupported`. |
| startDateTime | DateTimeOffset | Time the action was initiated |
| lastUpdatedDateTime | DateTimeOffset | Time the action state was last updated |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.vppTokenActionResult",
  "actionName": "String",
  "actionState": "String",
  "startDateTime": "String (timestamp)",
  "lastUpdatedDateTime": "String (timestamp)"
}
```
