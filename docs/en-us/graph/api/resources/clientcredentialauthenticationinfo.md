<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/clientcredentialauthenticationinfo?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-08-12 -->

# clientCredentialAuthenticationInfo resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents client credential \(OAuth 2.0 client credentials\) authentication information used by Microsoft Entra Entitlement Management to connect to an external system, including the client identifier, the Azure Key Vault secret reference, and the token endpoint.

Inherits from [authenticationInfo](https://learn.microsoft.com/en-us/graph/api/resources/authenticationinfo?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| accessTokenUrl | String | The URL endpoint used to obtain access tokens for authentication with the external system. |
| clientId | String | The client identifier used for authentication with the external system. |
| secretName | String | The name of the secret in Azure Key Vault that contains the client secret. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.clientCredentialAuthenticationInfo",
  "clientId": "String",
  "secretName": "String",
  "accessTokenUrl": "String"
}
```
