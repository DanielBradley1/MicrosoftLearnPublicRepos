<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/apiauthenticationconfigurationbase?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# apiAuthenticationConfigurationBase resource type

Namespace: microsoft.graph

The base type to hold authentication information for calling an API.

Derived types include:

- [basicAuthentication](https://learn.microsoft.com/en-us/graph/api/resources/basicauthentication?view=graph-rest-1.0) for HTTP basic authentication
- [pkcs12certificate](https://learn.microsoft.com/en-us/graph/api/resources/pkcs12certificate?view=graph-rest-1.0) for client certificate authentication \(used for API connector create or upload\)
- [clientCertificateAuthentication](https://learn.microsoft.com/en-us/graph/api/resources/pkcs12certificate?view=graph-rest-1.0) for client certificate authentication \(used for fetching the client certificates of an API connector\)

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.apiAuthenticationConfigurationBase"
}
```
