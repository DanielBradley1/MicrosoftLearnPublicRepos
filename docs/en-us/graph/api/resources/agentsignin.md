<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/agentsignin?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-11-18 -->

# agentSignIn resource type \(for conditionalAccess\)

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Defines details of the agent identity that is signing in, as defined in [Conditional Access What If evaluation](https://learn.microsoft.com/en-us/graph/api/conditionalaccessroot-evaluate?view=graph-rest-beta).

Inherits from [signInIdentity](https://learn.microsoft.com/en-us/graph/api/resources/signinidentity?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| agentServicePrincipalId | String | Agent identity object IDs included in the policy. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.agentSignIn",
  "agentServicePrincipalId": "String"
}
```
