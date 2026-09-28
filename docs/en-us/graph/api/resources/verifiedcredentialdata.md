<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/verifiedcredentialdata?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# verifiedCredentialData resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the metadata of the verifiable credential including the issuing authority, presented credentials, and the verified claims. Used for the **verifiedCredentialsData** property of [access package assignment request](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageassignmentrequest?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| authority | String | The authority ID for the issuer. |
| type | String collection | The list of credential types provided by the issuer. |
| claims | [verifiedCredentialClaims](https://learn.microsoft.com/en-us/graph/api/resources/verifiedcredentialclaims?view=graph-rest-beta) | Key-value pair of claims retrieved from the credential that the user presented, and the service verified. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.verifiedCredentialData",
  "authority": "String",
  "type": [
    "String"
  ],
  "claims": {
    "@odata.type": "microsoft.graph.verifiedCredentialClaims"
  }
}
```
