<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/cloudpcwindowssetting?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-08-30 -->

# cloudPcWindowsSetting resource type

Namespace: microsoft.graph

Represents a specific Windows setting to configure during the creation of Cloud PCs for a provisioning policy.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| locale | String | The Windows language or region tag to use for language pack configuration and localization of the Cloud PC. The default value is `en-US`, which corresponds to English \(United States\). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.cloudPcWindowsSetting",
  "locale": "String"
}
```
