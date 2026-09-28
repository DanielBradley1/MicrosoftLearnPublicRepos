<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/policybase?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# policyBase resource type

Namespace: microsoft.graph

Represents an abstract base type for policy types to inherit from. Inherits from [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0).

## Methods

None

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Unique identifier for this policy. Read-only. Inherited from [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0). |
| description | String | Description for this policy. Required. |
| displayName | String | Display name for this policy. Required. |

## Relationships

None

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "id": "String (identifier)",
  "description": "String",
  "displayName": "String"
}
```
