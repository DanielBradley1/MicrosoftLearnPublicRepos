<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/ai-services/retrieval/resources/sharepointembeddedconfiguration -->
<!-- Sitemap-Last-Modified: 2026-08-18 -->

# sharePointEmbeddedConfiguration resource type

Important

APIs under the `/beta` version are subject to change. Use of these APIs in production applications is not supported.

Represents configuration options for retrieving data from SharePoint Embedded in the [retrieval API](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/ai-services/retrieval/copilotroot-retrieval). To retrieve data from SharePoint Embedded by using the Retrieval API, you must properly configure the application for [SharePoint Embedded billing](https://learn.microsoft.com/en-us/sharepoint/dev/embedded/administration/billing/billing).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| `containerTypeId` | String | A valid ID for a [SharePoint Embedded container type](https://learn.microsoft.com/en-us/sharepoint/dev/embedded/getting-started/containertypes) |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "microsoft.graph.sharePointEmbeddedConfiguration",
  "containerTypeId": "String"
}
```
