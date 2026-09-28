<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/ipsegmentconfiguration?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-07-03 -->

# ipSegmentConfiguration resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents application segments for an on-premises nonweb application published through Microsoft Entra application proxy. This object is configured in the **segmentsConfiguration** property of [onPremisesPublishing](https://learn.microsoft.com/en-us/graph/api/resources/onpremisespublishing?view=graph-rest-beta).

Inherits from [segmentConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/segmentconfiguration?view=graph-rest-beta).

## Properties

None.

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| applicationSegments | [ipApplicationSegment](https://learn.microsoft.com/en-us/graph/api/resources/ipapplicationsegment?view=graph-rest-beta) collection | A collection of application segments for an on-premises nonweb application published through Microsoft Entra application proxy. It includes the destinationHost and ports. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.ipSegmentConfiguration"
}
```
