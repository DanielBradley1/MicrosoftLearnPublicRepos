<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/usagerightsincluded?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-01 -->

# usageRightsIncluded resource type

Namespace: microsoft.graph

Represents the usage rights associated with a specific piece of content.

This entity defines the permissions and actions available for the content based on its rights.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Get](https://learn.microsoft.com/en-us/graph/api/usagerightsincluded-get?view=graph-rest-1.0) | [usageRightsIncluded](https://learn.microsoft.com/en-us/graph/api/resources/usagerightsincluded?view=graph-rest-1.0) | Read the properties and relationships of a usageRightsIncluded object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The unique identifier for the label usage rights entity. Key property. |
| ownerEmail | String | The email of owner label rights. |
| userEmail | String | The email of user with label user rights. |
| value | [usageRights](https://learn.microsoft.com/en-us/graph/api/resources/usagerights?view=graph-rest-1.0) | A reference to the associated usage rights. This value defines the specific rights for the content. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.usageRightsIncluded",
  "id": "String (identifier)",
  "ownerEmail": "String",
  "userEmail": "String",
  "value": "String"
}
```
