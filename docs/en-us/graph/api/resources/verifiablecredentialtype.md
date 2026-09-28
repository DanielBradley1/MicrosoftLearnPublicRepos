<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/verifiablecredentialtype?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# verifiableCredentialType resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Contains details of a verifiable credential type, including the type of the credential issued and list of accepted issuers. Used for the **credentialType** property of [verifiableCredentialSettings](https://learn.microsoft.com/en-us/graph/api/resources/verifiablecredentialsettings?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| issuers | String collection | List of the accepted issuers authority as identified by the Microsoft Entra Verified ID service, for example, `did:ion:EiAlrenrtD3Lsw0GlbzS1O2YFdy3Xtu8yo35W\\<SNIP\>...`. |
| credentialType | String | The type of credential issued, for example, `BusinessCardCredential`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.verifiableCredentialType",
  "issuers": [
    "String"
  ],
  "credentialType": "String"
}
```
