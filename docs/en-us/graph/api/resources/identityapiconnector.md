<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/identityapiconnector?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# identityApiConnector resource type

Namespace: microsoft.graph

Represents API connectors in a Microsoft Entra tenants.

An API connector used in your Microsoft Entra External ID self-service sign-up user flows allows you to call an API during the execution of the user flow. An API connector provides the information needed to call an API including an endpoint URL and authentication. An API connector can be used at a specific step in a user flow to affect the execution of the user flow. For example, the API response can block a user from signing up, show an input validation error, or overwrite user collected attributes.

Use the [b2xIdentityUserFlow](https://learn.microsoft.com/en-us/graph/api/resources/b2xidentityuserflow?view=graph-rest-1.0) API to use an API connector from an External Identities self-service sign-up user flow.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/identityapiconnector-list?view=graph-rest-1.0) | [identityApiConnector](https://learn.microsoft.com/en-us/graph/api/resources/identityapiconnector?view=graph-rest-1.0) collection | Get a list of API connectors |
| [Create](https://learn.microsoft.com/en-us/graph/api/identityapiconnector-create?view=graph-rest-1.0) | [identityApiConnector](https://learn.microsoft.com/en-us/graph/api/resources/identityapiconnector?view=graph-rest-1.0) | Create a new API connector. |
| [Get](https://learn.microsoft.com/en-us/graph/api/identityapiconnector-get?view=graph-rest-1.0) | [identityApiConnector](https://learn.microsoft.com/en-us/graph/api/resources/identityapiconnector?view=graph-rest-1.0) | Read the properties of an [identityApiConnector](https://learn.microsoft.com/en-us/graph/api/resources/identityapiconnector?view=graph-rest-1.0) object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/identityapiconnector-update?view=graph-rest-1.0) | [identityApiConnector](https://learn.microsoft.com/en-us/graph/api/resources/identityapiconnector?view=graph-rest-1.0) | Update the properties of an API connector. |
| [Upload a client certificate](https://learn.microsoft.com/en-us/graph/api/identityapiconnector-uploadclientcertificate?view=graph-rest-1.0) | [identityApiConnector](https://learn.microsoft.com/en-us/graph/api/resources/identityapiconnector?view=graph-rest-1.0) | Upload a client certificate to use for authentication. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/identityapiconnector-delete?view=graph-rest-1.0) | None | Delete an API connector. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| authenticationConfiguration | [apiAuthenticationConfigurationBase](https://learn.microsoft.com/en-us/graph/api/resources/apiauthenticationconfigurationbase?view=graph-rest-1.0) | The object which describes the authentication configuration details for calling the API. Basic and PKCS 12 client certificate are supported. |
| displayName | String | The name of the API connector. |
| id | String | The randomly generated identifier of the API connector. |
| targetUrl | String | The URL of the API endpoint to call. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.identityApiConnector",
  "id": "String (identifier)",
  "displayName": "String",
  "targetUrl": "String",
  "authenticationConfiguration": {
    "@odata.type": "microsoft.graph.apiAuthenticationConfigurationBase"
  }
}
```
