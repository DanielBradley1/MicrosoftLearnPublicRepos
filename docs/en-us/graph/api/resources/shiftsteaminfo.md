<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/shiftsteaminfo?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-26 -->

# shiftsTeamInfo resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the details of a team with a [schedule](https://learn.microsoft.com/en-us/graph/api/resources/schedule?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| --- | --- | --- |
| displayName | `string` | The display name for the `team`. Required. |
| teamId | `string` | ID of the `team`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "displayName": "String",
  "teamId": "String"
}
```
