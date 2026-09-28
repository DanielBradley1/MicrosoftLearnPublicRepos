<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/ai-services/retrieval/resources/datasourceconfiguration -->
<!-- Sitemap-Last-Modified: 2026-08-18 -->

# dataSourceConfiguration resource type

Represents the data source configuration used in the [retrieval API](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/ai-services/retrieval/copilotroot-retrieval).

Important

APIs under the `/beta` version are subject to change. Use of these APIs in production applications is not supported.

Represents the data source configuration used in the [retrieval API](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/ai-services/retrieval/copilotroot-retrieval). A data source configuration must contain either an `externalItem` or `sharePointEmbedded` property to be valid.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| `externalItem` | [externalItemConfiguration](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/ai-services/retrieval/resources/externalitemconfiguration) | Configuration for Copilot connectors retrieval. Optional. |

| Property | Type | Description |
| :--- | :--- | :--- |
| `externalItem` | [externalItemConfiguration](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/ai-services/retrieval/resources/externalitemconfiguration) | Configuration for Copilot connectors retrieval. Optional. |
| `sharePointEmbedded` | [sharePointEmbeddedConfiguration](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/ai-services/retrieval/resources/sharepointembeddedconfiguration) | Configuration for SharePoint Embedded retrieval. Optional. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "externalItem": {
    "@odata.type": "microsoft.graph.externalItemConfiguration"
  }
}
```

```json
{
  "externalItem": {
    "@odata.type": "microsoft.graph.externalItemConfiguration"
  },
  "sharePointEmbedded": {
    "@odata.type": "microsoft.graph.sharePointEmbeddedConfiguration"
  }
}
```
