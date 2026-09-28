<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-tlsinspectionfqdndestination?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-09 -->

# tlsInspectionFqdnDestination resource type

Namespace: microsoft.graph.networkaccess

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a collection of fully qualified domain name \(FQDN\) destinations in a [TLS inspection rule](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-tlsinspectionrule?view=graph-rest-beta) for specifying domain names for TLS inspection matching.

Inherits from [microsoft.graph.networkaccess.tlsInspectionDestination](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-tlsinspectiondestination?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| values | String collection | A collection of fully qualified domain names to match against. The special value `*` represents any domain. Wildcard patterns can be used in domain names \(for example: `*.contoso.com`\). This collection cannot be empty or `null`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.networkaccess.tlsInspectionFqdnDestination",
  "values": [
    "String"
  ]
}
```
