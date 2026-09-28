<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/cloudpcwindowssettings?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-08-30 -->

# cloudPcWindowsSettings resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents specific Windows settings to configure while creating Cloud PCs for a provisioning policy.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| language | String | The Windows language/region tag to use for language pack configuration and localization of the Cloud PC. The default value is `en-US`, which corresponds to English \(United States\). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.cloudPcWindowsSettings",
  "language": "String"
}
```
