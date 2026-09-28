<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/federatedidentitycredential?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-12-04 -->

# federatedIdentityCredential resource type

Namespace: microsoft.graph

References an application's federated identity credentials. These federated identity credentials are used in [workload identity federation](https://learn.microsoft.com/en-us/azure/active-directory/develop/workload-identity-federation) when exchanging a token from a trusted issuer for an access token linked to an application registered on Microsoft Entra ID.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/federatedidentitycredential-list?view=graph-rest-1.0) | [federatedIdentityCredential](https://learn.microsoft.com/en-us/graph/api/resources/federatedidentitycredential?view=graph-rest-1.0) collection | Get a list of the [federatedIdentityCredential](https://learn.microsoft.com/en-us/graph/api/resources/federatedidentitycredential?view=graph-rest-1.0) objects and their properties. |
| [Create](https://learn.microsoft.com/en-us/graph/api/federatedidentitycredential-post?view=graph-rest-1.0) | [federatedIdentityCredential](https://learn.microsoft.com/en-us/graph/api/resources/federatedidentitycredential?view=graph-rest-1.0) | Create a new [federatedIdentityCredential](https://learn.microsoft.com/en-us/graph/api/resources/federatedidentitycredential?view=graph-rest-1.0) object. |
| [Get](https://learn.microsoft.com/en-us/graph/api/federatedidentitycredential-get?view=graph-rest-1.0) | [federatedIdentityCredential](https://learn.microsoft.com/en-us/graph/api/resources/federatedidentitycredential?view=graph-rest-1.0) | Read the properties and relationships of a [federatedIdentityCredential](https://learn.microsoft.com/en-us/graph/api/resources/federatedidentitycredential?view=graph-rest-1.0) object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/federatedidentitycredential-update?view=graph-rest-1.0) | None | Update the properties of a [federatedIdentityCredential](https://learn.microsoft.com/en-us/graph/api/resources/federatedidentitycredential?view=graph-rest-1.0) object. |
| [Upsert](https://learn.microsoft.com/en-us/graph/api/federatedidentitycredential-upsert?view=graph-rest-1.0) | [federatedIdentityCredential](https://learn.microsoft.com/en-us/graph/api/resources/federatedidentitycredential?view=graph-rest-1.0) | Create a new [federatedIdentityCredential](https://learn.microsoft.com/en-us/graph/api/resources/federatedidentitycredential?view=graph-rest-1.0) if it doesn't exist, or update the properties of an existing [federatedIdentityCredential](https://learn.microsoft.com/en-us/graph/api/resources/federatedidentitycredential?view=graph-rest-1.0) object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/federatedidentitycredential-delete?view=graph-rest-1.0) | None | Deletes a [federatedIdentityCredential](https://learn.microsoft.com/en-us/graph/api/resources/federatedidentitycredential?view=graph-rest-1.0) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| audiences | String collection | The audience that can appear in the external token. This field is mandatory and should be set to `api://AzureADTokenExchange` for Microsoft Entra ID. It says what Microsoft identity platform should accept in the `aud` claim in the incoming token. This value represents Microsoft Entra ID in your external identity provider and has no fixed value across identity providers - you might need to create a new application registration in your identity provider to serve as the audience of this token. This field can only accept a single value and has a limit of 600 characters. Required. |
| description | String | The unvalidated description of the federated identity credential, provided by the user. It has a limit of 600 characters. Optional. |
| id | String | The unique identifier for the federated identity. Required. Read-only. |
| issuer | String | The URL of the external identity provider, which must match the `issuer` claim of the external token being exchanged. The combination of the values of **issuer** and **subject** must be unique within the app. It has a limit of 600 characters. Required. |
| name | String | The unique identifier for the federated identity credential, which has a limit of 120 characters and must be URL friendly. The string is immutable after it's created. Alternate key. Required. Not nullable. Supports `$filter` \(`eq`\). |
| subject | String | Required. The identifier of the external software workload within the external identity provider. Like the audience value, it has no fixed format; each identity provider uses their own - sometimes a GUID, sometimes a colon delimited identifier, sometimes arbitrary strings. The value here must match the `sub` claim within the token presented to Microsoft Entra ID. The combination of **issuer** and **subject** must be unique within the app. It has a limit of 600 characters. Supports `$filter` \(`eq`\). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.federatedIdentityCredential",
  "audiences": [
    "String"
  ],
  "description": "String",
  "issuer": "String",
  "name": "String",
  "subject": "String"
}
```
