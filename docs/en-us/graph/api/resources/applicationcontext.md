<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/applicationcontext?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-28 -->

# applicationContext resource type

Namespace: microsoft.graph

Represents the application that the authenticating identity is attempting to access, as defined in [Conditional Access What If evaluation](https://learn.microsoft.com/en-us/graph/api/conditionalaccessroot-evaluate?view=graph-rest-1.0). Inherits from [signInContext](https://learn.microsoft.com/en-us/graph/api/resources/signincontext?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| includeApplications | String collection | Collection of **appId** values for the applications. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.applicationContext",
  "includeApplications": [
    "String"
  ]
}
```
