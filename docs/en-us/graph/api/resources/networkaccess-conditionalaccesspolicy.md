<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-conditionalaccesspolicy?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-22 -->

# conditionalAccessPolicy resource type

Namespace: microsoft.graph.networkaccess

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

represents the configuration and settings of a conditional access policy within a network infrastructure, which determines the access control rules and conditions for network traffic filtering.

Inherits from [microsoft.graph.entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta).

## Methods

None.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| createdDateTime | DateTimeOffset | Indicates the date and time the conditional access policy was created. |
| description | String | Provides a summary of the conditional access policy. |
| displayName | String | Represents the human-readable name or title assigned to the conditional access policy. |
| id | String | Represents the unique identifier assigned to the conditional access policy. Inherited from [microsoft.graph.entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). |
| modifiedDateTime | DateTimeOffset | Indicates the date and time when the conditional access policy was last modified. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.networkaccess.conditionalAccessPolicy",
  "id": "String (identifier)",
  "createdDateTime": "String (timestamp)",
  "modifiedDateTime": "String (timestamp)",
  "displayName": "String",
  "description": "String"
}
```
