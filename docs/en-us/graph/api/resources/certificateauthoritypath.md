<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/certificateauthoritypath?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-01-02 -->

# certificateAuthorityPath resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Container for certificate authorities-related configurations for applications in the tenant.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta).

## Methods

None.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The unique identifier for the certificate authority configuration. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| certificateBasedApplicationConfigurations | [certificateBasedApplicationConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/certificatebasedapplicationconfiguration?view=graph-rest-beta) collection | Defines the trusted certificate authorities for certificates that can be added to apps and service principals in the tenant. |
| mutualTlsOauthConfigurations | [mutualTlsOauthConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/mutualtlsoauthconfiguration?view=graph-rest-beta) collection | Defines the trusted certificate authorities for certificates that can be added to Internet of Things \(IoT\) devices. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.certificateAuthorityPath",
  "id": "String (identifier)"
}
```
