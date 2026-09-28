<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/managedidentity?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-07-04 -->

# managedIdentity resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents details of the managed identity that was used to sign into the target resource. This object is configured in the **managedServiceIdentity** property of [signIn](https://learn.microsoft.com/en-us/graph/api/resources/signin?view=graph-rest-beta) and [summarizedSignIn](https://learn.microsoft.com/en-us/graph/api/resources/summarizedsignin?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| associatedResourceId | String | The ARM resource ID of the Azure resource associated with the managed identity used for sign in. |
| federatedTokenId | String | The unique ID of the federated token. |
| federatedTokenIssuer | String | The issuer of the federated token. |
| msiType | msiType | The possible values are: `none`, `userAssigned`, `systemAssigned`, `unknownFutureValue`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.managedIdentity",
  "msiType": "String",
  "associatedResourceId": "String",
  "federatedTokenId": "String",
  "federatedTokenIssuer": "String"
}
```
