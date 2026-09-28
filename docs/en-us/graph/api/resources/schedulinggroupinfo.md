<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/schedulinggroupinfo?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-26 -->

# schedulingGroupInfo resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the details of a [schedulingGroup](https://learn.microsoft.com/en-us/graph/api/resources/schedulinggroup?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| --- | --- | --- |
| displayName | `string` | The display name for the `schedulingGroup`. Required. |
| schedulingGroupId | `string` | ID of the `schedulingGroup`. |
| code | `string` | The code for the `schedulingGroup`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "displayName": "String",
  "schedulingGroupId": "String",
  "code": "String"
}
```
