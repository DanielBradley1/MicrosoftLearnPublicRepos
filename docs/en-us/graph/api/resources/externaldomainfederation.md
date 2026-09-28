<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/externaldomainfederation?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-06-20 -->

# externalDomainFederation resource type

Namespace: microsoft.graph

Used in the identity sources of an [connectedOrganization](https://learn.microsoft.com/en-us/graph/api/resources/connectedorganization?view=graph-rest-1.0). The `@odata.type` value `#microsoft.graph.externalDomainFederation` indicates that this type identifies a domain with a configured identity provider as an identity source for a connected organization.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | The name of the identity source, typically also the domain name. Read-only. |
| domainName | String | The domain name. Read-only. |
| issuerUri | String | The issuerURI of the incoming federation. Read-only. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.externalDomainFederation",
  "displayName": "String",
  "domainName": "String",
  "issuerUri": "String"
}
```
