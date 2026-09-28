<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/insights-sharingdetail?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# sharingDetail resource type

Namespace: microsoft.graph

Contains properties of [sharedInsight](https://learn.microsoft.com/en-us/graph/api/resources/insights-shared?view=graph-rest-1.0) items.

## Properties

| Property | Type | Description |
| --- | --- | --- |
| sharedBy | [insightIdentity](https://learn.microsoft.com/en-us/graph/api/resources/insights-insightidentity?view=graph-rest-1.0) | The user who shared the document. |
| sharedDateTime | DateTimeOffset | The date and time the file was last shared. The timestamp represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. Read-only. |
| sharingSubject | String | The subject with which the document was shared. |
| sharingType | String | Determines the way the document was shared. Can be by a 1Link1, 1Attachment1, 1Group1, 1Site1. |
| sharingReference | [resourceReference](https://learn.microsoft.com/en-us/graph/api/resources/insights-resourcereference?view=graph-rest-1.0) | Reference properties of the document, such as the URL and type of the document. Read-only |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "sharedDateTime": "dateTimeOffset",
  "sharingSubject": "string",
  "sharingType": "string",
  "sharedBy": "insightIdentity",
  "sharingReference": "resourceReference"
}
```
