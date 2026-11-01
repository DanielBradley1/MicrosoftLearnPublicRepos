<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/enumerateddomains?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-10-30 -->

# enumeratedDomains resource type

Namespace: microsoft.graph

A derived complex type that defines validation against an enumerated list of root domains. The **validatingDomains** property of the [federatedTokenValidationPolicy](https://learn.microsoft.com/en-us/graph/api/resources/federatedtokenvalidationpolicy?view=graph-rest-1.0) resource returns this type when `rootDomains` is set to `enumerated` or `allManagedAndEnumeratedFederated`.

Inherits from [validatingDomains](https://learn.microsoft.com/en-us/graph/api/resources/validatingdomains?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| domainNames | String collection | List of federated or managed root domains that Microsoft Entra ID validates. |
| rootDomains | [rootDomains](https://learn.microsoft.com/en-us/graph/api/resources/enums?view=graph-rest-1.0#rootdomains-values) | Defines the types of domains that Microsoft Entra ID validates. Inherited from [validatingDomains](https://learn.microsoft.com/en-us/graph/api/resources/validatingdomains?view=graph-rest-1.0). For this subtype the value can be `enumerated`, `allManagedAndEnumeratedFederated`, or `unknownFutureValue`. The `none`, `all` \(default\), `allFederated`, and `allManaged` values belong to the [allDomains](https://learn.microsoft.com/en-us/graph/api/resources/alldomains?view=graph-rest-1.0) subtype. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.enumeratedDomains",
  "rootDomains": "String",
  "domainNames": [
    "String"
  ]
}
```
