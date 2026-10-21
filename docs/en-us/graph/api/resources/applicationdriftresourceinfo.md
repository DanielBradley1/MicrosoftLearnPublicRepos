<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/applicationdriftresourceinfo?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-10-17 -->

# applicationDriftResourceInfo resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents resource information for an application in an access drift context.

This object can be returned in the **resource** property of [accessDriftSummary](https://learn.microsoft.com/en-us/graph/api/resources/accessdriftsummary?view=graph-rest-beta) and [accessDriftDetail](https://learn.microsoft.com/en-us/graph/api/resources/accessdriftdetail?view=graph-rest-beta).

Inherits from [driftResourceInfo](https://learn.microsoft.com/en-us/graph/api/resources/driftresourceinfo?view=graph-rest-beta).

## Methods

None.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| catalogIdentifier | String | The identifier of the entitlement management catalog that contains the resource. Inherited from [driftResourceInfo](https://learn.microsoft.com/en-us/graph/api/resources/driftresourceinfo?view=graph-rest-beta). |
| catalogName | String | The display name of the entitlement management catalog. Inherited from [driftResourceInfo](https://learn.microsoft.com/en-us/graph/api/resources/driftresourceinfo?view=graph-rest-beta). |
| displayName | String | The display name of the application. Inherited from [driftResourceInfo](https://learn.microsoft.com/en-us/graph/api/resources/driftresourceinfo?view=graph-rest-beta). |
| identifier | String | The unique identifier of the application. Inherited from [driftResourceInfo](https://learn.microsoft.com/en-us/graph/api/resources/driftresourceinfo?view=graph-rest-beta). |
| type | [accessDriftResourceType](https://learn.microsoft.com/en-us/graph/api/resources/enums?view=graph-rest-beta#accessdriftresourcetype-values) | The type of governed resource. Inherited from [driftResourceInfo](https://learn.microsoft.com/en-us/graph/api/resources/driftresourceinfo?view=graph-rest-beta). The possible values are: `application`, `group`, `unknownFutureValue`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.applicationDriftResourceInfo",
  "catalogName": "String",
  "identifier": "String",
  "displayName": "String",
  "type": "String",
  "catalogIdentifier": "String"
}
```
