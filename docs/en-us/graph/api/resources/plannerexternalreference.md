<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/plannerexternalreference?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-26 -->

# plannerExternalReference resource type

Namespace: microsoft.graph

The **plannerExternalReference** resource represents the metadata of a reference \(attachments such as file, URL\). It's the value of property-value pairs in the [externalReferences object](https://learn.microsoft.com/en-us/graph/api/resources/plannerexternalreferences?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| alias | String | A name alias to describe the reference. |
| lastModifiedBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-1.0) | Read-only. User ID by which this is last modified. |
| lastModifiedDateTime | DateTimeOffset | Read-only. Date and time at which this is last modified. The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z` |
| previewPriority | String | Used to set the relative priority order in which the reference will be shown as a preview on the task. |
| type | String | Used to describe the type of the reference. Types include: `PowerPoint`, `Word`, `Excel`, `Other`. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "alias": "String",
  "lastModifiedBy": {"@odata.type": "microsoft.graph.identitySet"},
  "lastModifiedDateTime": "String (timestamp)",
  "previewPriority": "String",
  "type": "String"
}
```
