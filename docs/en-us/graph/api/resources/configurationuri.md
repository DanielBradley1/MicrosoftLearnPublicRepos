<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/configurationuri?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-12-03 -->

# configurationUri resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a URI for the single sign-on configuration of a preintegrated application.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| appliesToSingleSignOnMode | String | The single sign-on mode that the URI is configured for. The possible values are: `saml`, `password`. |
| examples | String collection | The various formats that the URI should follow. |
| isRequired | Boolean | Indicates whether this URI is required for the single sign-on configuration. |
| usage | uriUsageType | Indicates how the URI is used in single sign-on. The possible values are: `redirectUri`, `identifierUri`, `loginUrl`, `logoutUrl`, `unknownFutureValue`. |
| values | String collection | The suggested values for the URI. Developers may need to customize these values for their tenant. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.configurationUri",
  "appliesToSingleSignOnMode": "String",
  "examples": ["String"],
  "isRequired": "Boolean",
  "usage": "String",
  "values": ["String"]
}
```
