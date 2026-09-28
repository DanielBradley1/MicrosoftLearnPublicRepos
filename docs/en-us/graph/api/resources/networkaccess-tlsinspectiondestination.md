<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-tlsinspectiondestination?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-09 -->

# tlsInspectionDestination resource type

Namespace: microsoft.graph.networkaccess

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

An abstract type that represents the set of destinations to be matched in [TLS inspection rules](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-tlsinspectionrule?view=graph-rest-beta). This type serves as a base for specific destination types like FQDN and web categories in TLS inspection policies.

This is an abstract type that can be instantiated as either:

- [tlsInspectionFqdnDestination](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-tlsinspectionfqdndestination?view=graph-rest-beta) - For matching against fully qualified domain names \(FQDNs\)
- [tlsInspectionWebCategoryDestination](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-tlsinspectionwebcategorydestination?view=graph-rest-beta) - For matching against predefined web categories

## Properties

None.

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.networkaccess.tlsInspectionDestination"
}
```
