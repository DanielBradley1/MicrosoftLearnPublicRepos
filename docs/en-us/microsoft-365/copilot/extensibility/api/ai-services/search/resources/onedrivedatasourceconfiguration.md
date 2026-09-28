<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/ai-services/search/resources/onedrivedatasourceconfiguration -->
<!-- Sitemap-Last-Modified: 2025-10-20 -->

# oneDriveDataSourceConfiguration resource type

Important

APIs under the `/beta` version are subject to change. Use of these APIs in production applications is not supported.

OneDrive-specific search configuration, including filtering and metadata options.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| `filterExpression` | String | [Keyword Query Language \(KQL\)](https://learn.microsoft.com/en-us/sharepoint/dev/general-development/keyword-query-language-kql-syntax-reference) expression for filtering OneDrive content. Currently only supports `path:` expressions. |
| `resourceMetadataNames` | String collection | Resource metadata fields to return in results. Supported fields: `path`, `author`, `fileName`, `fileType`, `title`, `id`, `driveId`, `siteId`, `listId`, `createdBy`, `lastModifiedTime`, and `modifiedBy`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.oneDriveDataSourceConfiguration",
  "filterExpression": "String",
  "resourceMetadataNames": [
    "String"
  ]
}
```
