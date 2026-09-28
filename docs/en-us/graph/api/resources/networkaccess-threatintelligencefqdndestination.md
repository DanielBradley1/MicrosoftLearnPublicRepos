<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-threatintelligencefqdndestination?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-09 -->

# threatIntelligenceFqdnDestination resource type

Namespace: microsoft.graph.networkaccess

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a collection of fully qualified domain names \(FQDNs\) associated with potential security threats. These domains can be used in threat intelligence policies to identify and block access to malicious destinations. Parent resource [threatintelligenceMatchingConditions](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-threatintelligencematchingconditions?view=graph-rest-beta) consumes this complex type.

Inherits from [microsoft.graph.networkaccess.threatIntelligenceDestination](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-threatintelligencedestination?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| values | String collection | A collection of fully qualified domain names \(FQDNs\) associated with potential security threats. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.networkaccess.threatIntelligenceFqdnDestination",
  "values": [
    "String"
  ]
}
```
