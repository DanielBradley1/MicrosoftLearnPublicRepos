<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/stspolicy?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# stsPolicy resource type

Namespace: microsoft.graph

Represents an abstract base type for policy types that control [Microsoft identity platform](https://learn.microsoft.com/en-us/azure/active-directory/develop/) behavior.

Inherits from [policyBase](https://learn.microsoft.com/en-us/graph/api/resources/policybase?view=graph-rest-1.0).

## Methods

None

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| description | String | Description for this policy. Inherited from [policyBase](https://learn.microsoft.com/en-us/graph/api/resources/policybase?view=graph-rest-1.0). |
| displayName | String | Display name for this policy. Inherited from [policyBase](https://learn.microsoft.com/en-us/graph/api/resources/policybase?view=graph-rest-1.0). |
| definition | String collection | A string collection containing a JSON string that defines the rules and settings for a policy. The syntax for the definition differs for each derived policy type. Required. |
| id | String | Unique identifier for this policy. Read-only. Inherited from [policyBase](https://learn.microsoft.com/en-us/graph/api/resources/policybase?view=graph-rest-1.0). |
| isOrganizationDefault | Boolean | If set to true, activates this policy. There can be many policies for the same policy type, but only one can be activated as the organization default. Optional, default value is false. |

## Relationships

None

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "id": "String (identifier)",
  "description": "String",
  "displayName": "String",
  "definition": ["String"],
  "isOrganizationDefault": true
}
```
