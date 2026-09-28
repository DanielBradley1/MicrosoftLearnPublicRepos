<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/ai-services/retrieval/resources/retrievalhit -->
<!-- Sitemap-Last-Modified: 2026-08-18 -->

# retrievalHit resource type

Important

APIs under the `/beta` version are subject to change. Use of these APIs in production applications is not supported.

Represents a single result within the list of retrieval results.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| `extracts` | [retrievalExtract](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/ai-services/retrieval/resources/retrievalextract) collection | An array of text extracts extracted from the document for Retrieval-Augmented Generation. Currently, only one text snippet is extracted. |
| `resourceMetadata` | [searchResourceMetadataDictionary](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/ai-services/retrieval/resources/searchresourcemetadatadictionary) | The requested [SharePoint](https://learn.microsoft.com/en-us/sharepoint/crawled-and-managed-properties-overview) and [Microsoft 365 Copilot connectors](https://learn.microsoft.com/en-us/graph/connecting-external-content-manage-schema) metadata from the request payload \(empty if not applicable\). |
| `resourceType` | [retrievalEntityType](#retrievalentitytype-enumeration) | The resource type of the item. |
| `sensitivityLabel` | [searchSensitivityLabelInfo](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/ai-services/resources/searchsensitivitylabelinfo) | A JSON object with information about the document's sensitivity label. |
| `webUrl` | String | The URL of the item in which the extract was retrieved. |

| Property | Type | Description |
| :--- | :--- | :--- |
| `extracts` | [retrievalExtract](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/ai-services/retrieval/resources/retrievalextract) collection | An array of text extracts extracted from the document for Retrieval-Augmented Generation. Currently, only one text snippet is extracted. |
| `resourceMetadata` | [searchResourceMetadataDictionary](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/ai-services/retrieval/resources/searchresourcemetadatadictionary) | The requested [SharePoint](https://learn.microsoft.com/en-us/sharepoint/crawled-and-managed-properties-overview) and [Microsoft 365 Copilot connectors](https://learn.microsoft.com/en-us/graph/connecting-external-content-manage-schema) metadata from the request payload \(empty if not applicable\). |
| `resourceType` | [retrievalEntityType](#retrievalentitytype-enumeration) | The resource type of the item. |
| `sensitivityLabel` | [searchSensitivityLabelInfo](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/ai-services/resources/searchsensitivitylabelinfo) | A JSON object with information about the document's sensitivity label. |
| `thumbnails` | [retrievalThumbnail](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/ai-services/retrieval/resources/retrievalthumbnail) collection | The collection of thumbnails for the document if requested and available. |
| `webUrl` | String | The URL of the item in which the extract was retrieved. |

### retrievalEntityType enumeration

An [evolvable enumeration](https://learn.microsoft.com/en-us/graph/best-practices-concept#handling-future-members-in-evolvable-enumerations) with the following possible values.

| Value |
| :--- |
| `site` |
| `list` |
| `listItem` |
| `externalItem` |
| `drive` |
| `driveItem` |
| `unknownFutureValue` |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.retrievalHit",
  "webUrl": "String",
  "sensitivityLabel": {
    "@odata.type": "microsoft.graph.searchSensitivityLabelInfo"
  },
  "extracts": [
    {
      "@odata.type": "microsoft.graph.retrievalExtract"
    }
  ],
  "resourceType": "String",
  "resourceMetadata": {
    "@odata.type": "microsoft.graph.searchResourceMetadataDictionary"
  }
}
```

```json
{
  "@odata.type": "#microsoft.graph.retrievalHit",
  "webUrl": "String",
  "sensitivityLabel": {
    "@odata.type": "microsoft.graph.searchSensitivityLabelInfo"
  },
  "extracts": [
    {
      "@odata.type": "microsoft.graph.retrievalExtract"
    }
  ],
  "resourceType": "String",
  "resourceMetadata": {
    "@odata.type": "microsoft.graph.searchResourceMetadataDictionary"
  },
  "thumbnails": [
    {
      "@odata.type": "microsoft.graph.retrievalThumbnail"
    }
  ]
}
```
