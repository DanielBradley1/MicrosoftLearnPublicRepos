<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/driftresourceinfo?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-10-17 -->

# driftResourceInfo resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents abstract base information about a governed resource in an access drift context. Derived types include [applicationDriftResourceInfo](https://learn.microsoft.com/en-us/graph/api/resources/applicationdriftresourceinfo?view=graph-rest-beta) and [groupDriftResourceInfo](https://learn.microsoft.com/en-us/graph/api/resources/groupdriftresourceinfo?view=graph-rest-beta).

This object is configured in the **resource** property of [accessDriftSummary](https://learn.microsoft.com/en-us/graph/api/resources/accessdriftsummary?view=graph-rest-beta) and [accessDriftDetail](https://learn.microsoft.com/en-us/graph/api/resources/accessdriftdetail?view=graph-rest-beta).

This is an abstract type.

## Methods

None.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| catalogIdentifier | String | The identifier of the entitlement management catalog that contains the resource. |
| catalogName | String | The display name of the entitlement management catalog. |
| displayName | String | The display name of the governed resource. |
| identifier | String | The unique identifier of the governed resource. |
| type | [accessDriftResourceType](https://learn.microsoft.com/en-us/graph/api/resources/enums?view=graph-rest-beta#accessdriftresourcetype-values) | The type of governed resource. The possible values are: `application`, `group`, `unknownFutureValue`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.driftResourceInfo",
  "catalogName": "String",
  "identifier": "String",
  "displayName": "String",
  "type": "String",
  "catalogIdentifier": "String"
}
```
