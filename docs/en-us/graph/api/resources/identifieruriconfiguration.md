<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/identifieruriconfiguration?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-05-14 -->

# identifierUriConfiguration resource type

Namespace: microsoft.graph

Configuration object to configure a restriction for [identifier URIs on application objects](https://learn.microsoft.com/en-us/graph/api/resources/identifieruriconfiguration?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| nonDefaultUriAddition | [identifierUriRestriction](https://learn.microsoft.com/en-us/graph/api/resources/identifierurirestriction?view=graph-rest-1.0) | Block new identifier URIs for applications, unless they are the "default" URI of the format `api://{appId}` or `api://{tenantId}/{appId}`. |
| uriAdditionWithoutUniqueTenantIdentifier | [identifierUriRestriction](https://learn.microsoft.com/en-us/graph/api/resources/identifierurirestriction?view=graph-rest-1.0) | Block new identifier URIs for applications, unless they contain a unique tenant identifier like the tenant ID, **appId** \(client ID\), or verified domain. For example, `api://{tenantId}/string`, `api://{appId}/string`, `{scheme}://string/{tenantId}`, `{scheme}://string/{appId}`, `https://{verified-domain.com}/path`, `{scheme}://{subdomain}.{verified-domain.com}/path`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.identifierUriConfiguration",
  "nonDefaultUriAddition": {
    "@odata.type": "microsoft.graph.identifierUriRestriction"
  },
  "uriAdditionWithoutUniqueTenantIdentifier": {
    "@odata.type": "microsoft.graph.identifierUriRestriction"
  }
}
```
