<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/federatedidentityexpression?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-12-11 -->

# federatedIdentityExpression resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Enables the use of a restricted expression language for flexible matching of federated identity credentials to workload scenarios. Primarily, this resource type allows the specification of wildcard-based expressions within **claimsMatchingExpression** property of [federatedIdentityCredential resource type](https://learn.microsoft.com/en-us/graph/api/resources/federatedidentitycredential?view=graph-rest-beta) > **value** property. For more information on supported patterns and scenarios, visit the [flexible federated identity credentials documentation](https://aka.ms/flexiblefic).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| languageVersion | Int32 | Indicated the language version to be used. Should always be set to 1. Required. |
| value | String | Indicates the configured expression. Required. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.federatedIdentityExpression",
  "languageVersion": "Integer",
  "value": "String"
}
```
