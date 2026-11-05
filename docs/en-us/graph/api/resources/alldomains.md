<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/alldomains?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-10-30 -->

# allDomains resource type

Namespace: microsoft.graph

A derived complex type that defines validation that applies to a category of domains without enumerating specific domain names. The **validatingDomains** property of the [federatedTokenValidationPolicy](https://learn.microsoft.com/en-us/graph/api/resources/federatedtokenvalidationpolicy?view=graph-rest-1.0) resource returns this type when `rootDomains` is set to `none`, `all`, `allFederated`, or `allManaged`.

Inherits from [validatingDomains](https://learn.microsoft.com/en-us/graph/api/resources/validatingdomains?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| rootDomains | [rootDomains](https://learn.microsoft.com/en-us/graph/api/resources/enums?view=graph-rest-1.0#rootdomains-values) | Defines the types of domains that Microsoft Entra ID validates. Inherited from [validatingDomains](https://learn.microsoft.com/en-us/graph/api/resources/validatingdomains?view=graph-rest-1.0). For this subtype the value can be `none`, `all` \(default\), `allFederated`, `allManaged`, or `unknownFutureValue`. The `enumerated` and `allManagedAndEnumeratedFederated` values belong to the [enumeratedDomains](https://learn.microsoft.com/en-us/graph/api/resources/enumerateddomains?view=graph-rest-1.0) subtype. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.allDomains",
  "rootDomains": "String"
}
```
