<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/signinidentity?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-28 -->

# signInIdentity resource type

Namespace: microsoft.graph

Represents the identity that is signing in, as defined in [Conditional Access What If evaluation](https://learn.microsoft.com/en-us/graph/api/conditionalaccessroot-evaluate?view=graph-rest-1.0). The identity could be that of a user, an guest user, or a single tenant service principal. This resource is an abstract type from which the following types derive:

- [userSignIn](https://learn.microsoft.com/en-us/graph/api/resources/usersignin?view=graph-rest-1.0)
- [servicePrincipalSignIn](https://learn.microsoft.com/en-us/graph/api/resources/serviceprincipalsignin?view=graph-rest-1.0)

## Properties

None.

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.signInIdentity"
}
```
