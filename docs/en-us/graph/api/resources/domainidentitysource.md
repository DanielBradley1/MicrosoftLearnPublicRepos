<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/domainidentitysource?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-07-04 -->

# domainIdentitySource resource type

Namespace: microsoft.graph

Used in the **identitySources** property of [connectedOrganization](https://learn.microsoft.com/en-us/graph/api/resources/connectedorganization?view=graph-rest-1.0). The `@odata.type` value `#microsoft.graph.domainIdentitySource` indicates that this type identifies a domain as an identity source for a connected organization.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | The name of the identity source, typically also the domain name. Read-only. |
| domainName | String | The domain name. Read-only. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.domainIdentitySource",
  "displayName": "String",
  "domainName": "String"
}
```
