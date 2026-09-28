<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/securityactionstate?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-12-03 -->

# securityActionState resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the history of securityAction state changes.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| appId | String | The Application ID of the calling application that submitted an update \(PATCH\) to the action. The `appId` should be extracted from the auth token and not entered manually by the calling application. |
| status | String | Status of the securityAction in this update. The possible values are: `NotStarted`, `Running`, `Completed`, `Failed`. |
| updatedDateTime | DateTimeOffset | Timestamp when the actionState was updated. The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z` |
| user | String | The user principal name of the signed-in user that submitted an update \(PATCH\) to the action. The `user` should be extracted from the auth token and not entered manually by the calling application. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "appId": "String",
  "status": "String",
  "updatedDateTime": "String (timestamp)",
  "user": "String"
}
```
