<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-contentapplicabilitysettings?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-01-27 -->

# contentApplicabilitySettings resource type

Namespace: microsoft.graph.windowsUpdates

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents settings for governing whether content is applicable to a device.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| offerWhileRecommendedBy | String collection | Offer if the update is recommended by a vendor in the list, otherwise withhold the offer. |
| safeguard | [microsoft.graph.windowsUpdates.safeguardSettings](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-safeguardsettings?view=graph-rest-beta) | Settings for governing safeguard-holds on offering content. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.windowsUpdates.contentApplicabilitySettings",
  "offerWhileRecommendedBy": ["String"],
  "safeguard": {
    "@odata.type": "microsoft.graph.windowsUpdates.safeguardSettings"
  }
}
```
