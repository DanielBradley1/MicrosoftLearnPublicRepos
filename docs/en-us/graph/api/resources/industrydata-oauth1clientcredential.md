<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/industrydata-oauth1clientcredential?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-06-05 -->

# oAuth1ClientCredential resource type

Namespace: microsoft.graph.industryData

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents credentials that use OAuth 1.0 to authenticate to a resource.

Inherits from [oAuthClientCredential](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-oauthclientcredential?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| clientId | String | The client identifier of the application that is authenticating. Inherited from [oAuthClientCredential](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-oauthclientcredential?view=graph-rest-beta). |
| clientSecret | String | The client secret that is used to authenticate \(write-only\). Inherited from [oAuthClientCredential](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-oauthclientcredential?view=graph-rest-beta). |
| displayName | String | The name of the credential. Inherited from [credential](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-credential?view=graph-rest-beta). |
| isValid | Boolean | Indicates whether the credential provided is valid based on the last data connector [validate](https://learn.microsoft.com/en-us/graph/api/industrydata-industrydataconnector-validate?view=graph-rest-beta) operation. Inherited from [credential](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-credential?view=graph-rest-beta). |
| lastValidDateTime | DateTimeOffset | The time that the credential was last successfully validated by the data connector [validate](https://learn.microsoft.com/en-us/graph/api/industrydata-industrydataconnector-validate?view=graph-rest-beta) operation. Inherited from [credential](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-credential?view=graph-rest-beta). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.industryData.oAuth1ClientCredential",
  "displayName": "String",
  "isValid": "Boolean",
  "lastValidDateTime": "String (timestamp)",
  "clientId": "String",
  "clientSecret": "String"
}
```
