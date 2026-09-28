<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/authcontext?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-28 -->

# authContext resource type

Namespace: microsoft.graph

Represents the authentication context protecting the data that the authenticating identity is attempting to access, as defined in [Conditional Access What If evaluation](https://learn.microsoft.com/en-us/graph/api/conditionalaccessroot-evaluate?view=graph-rest-1.0). Inherits from [signInContext](https://learn.microsoft.com/en-us/graph/api/resources/signincontext?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| authenticationContextValue | String | Supported values are `c1` through `c99`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.authContext",
  "authenticationContextValue": "String"
}
```
