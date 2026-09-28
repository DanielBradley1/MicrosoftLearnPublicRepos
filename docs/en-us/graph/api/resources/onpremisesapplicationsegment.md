<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/onpremisesapplicationsegment?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-07-03 -->

# onPremisesApplicationSegment resource type \(deprecated\)

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents an on-premises wildcard application segment published with Microsoft Entra application proxy. This resource is used for setting an application segment for a particular wildcard application. This object is configured in the **onPremisesApplicationSegments** property \(deprecated\) of [onPremisesPublishing](https://learn.microsoft.com/en-us/graph/api/resources/onpremisespublishing?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| alternateUrl | String | If you're configuring a traffic manager in front of multiple App Proxy application segments, contains the user-friendly URL that will point to the traffic manager. |
| corsConfigurations | [corsConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/corsconfiguration?view=graph-rest-beta) collection | CORS Rule definition for a particular application segment. |
| externalUrl | String | The published external URL for the application segment; for example, https://intranet.contoso.com./ |
| internalUrl | String | The internal URL of the application segment; for example, https://intranet/. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "alternateUrl": "String",
    "corsConfigurations": [
    {
      "@odata.type": "microsoft.graph.corsConfiguration"
    }
  ],
  "externalUrl": "String",
  "internalUrl": "String",
}
```
