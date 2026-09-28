<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/signincontext?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-28 -->

# signInContext resource type

Namespace: microsoft.graph

Represents the context of the sign-in as defined in [Conditional Access What If evaluation](https://learn.microsoft.com/en-us/graph/api/conditionalaccessroot-evaluate?view=graph-rest-1.0). The context could involve accessing an application, performing a specific user action, or accessing data protected by an authentication context.

This resource is an abstract type from which the following types derive:

- [applicationContext](https://learn.microsoft.com/en-us/graph/api/resources/applicationcontext?view=graph-rest-1.0)
- [authContext](https://learn.microsoft.com/en-us/graph/api/resources/authcontext?view=graph-rest-1.0)
- [userActionContext](https://learn.microsoft.com/en-us/graph/api/resources/useractioncontext?view=graph-rest-1.0)

## Properties

None.

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.signInContext"
}
```
