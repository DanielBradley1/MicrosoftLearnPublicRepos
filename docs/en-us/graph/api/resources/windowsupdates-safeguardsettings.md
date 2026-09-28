<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-safeguardsettings?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-01-27 -->

# safeguardSettings resource type

Namespace: microsoft.graph.windowsUpdates

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Manages the safeguards that Windows Autopatch applies to devices in a deployment.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| disabledSafeguardProfiles | [microsoft.graph.windowsUpdates.safeguardProfile](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-safeguardprofile?view=graph-rest-beta) collection | List of safeguards to ignore per device. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.windowsUpdates.safeguardSettings",
  "disabledSafeguardProfiles": [
    {
      "@odata.type": "microsoft.graph.windowsUpdates.safeguardProfile"
    }
  ]
}
```
