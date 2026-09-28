<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/ai-services/search/resources/copilotsearchdatasourcesconfiguration -->
<!-- Sitemap-Last-Modified: 2025-10-20 -->

# copilotSearchDataSourcesConfiguration resource type

Important

APIs under the `/beta` version are subject to change. Use of these APIs in production applications is not supported.

Configuration for data sources to include in the search.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| `oneDrive` | [oneDriveDataSourceConfiguration](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/ai-services/search/resources/onedrivedatasourceconfiguration) | OneDrive-specific search configuration \(currently the only supported data source\). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.copilotSearchDataSourcesConfiguration",
  "oneDrive": {
    "@odata.type": "microsoft.graph.oneDriveDataSourceConfiguration"
  }
}
```
