<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/serviceprincipalsignin?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-28 -->

# servicePrincipalSignIn resource type

Namespace: microsoft.graph

Represents the service principal that is signing in, as defined in [Conditional Access What If evaluation](https://learn.microsoft.com/en-us/graph/api/conditionalaccessroot-evaluate?view=graph-rest-1.0). Inherits from [signInIdentity](https://learn.microsoft.com/en-us/graph/api/resources/signinidentity?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| servicePrincipalId | String | `appId` of the service principal that is signing in. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.servicePrincipalSignIn",
  "servicePrincipalId": "String"
}
```
