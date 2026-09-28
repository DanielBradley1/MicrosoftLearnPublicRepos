<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/sectiongroup?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-06-20 -->

# sectionGroup resource type

Namespace: microsoft.graph

A section group in a OneNote notebook. Section groups can contain sections and section groups.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "createdBy": {"@odata.type": "microsoft.graph.identitySet"},
  "createdDateTime": "String (timestamp)",
  "id": "string (identifier)",
  "lastModifiedBy": {"@odata.type": "microsoft.graph.identitySet"},
  "lastModifiedDateTime": "String (timestamp)",
  "displayName": "string",
  "sectionGroupsUrl": "string",
  "sectionsUrl": "string",
  "self": "string"
}
```

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| createdBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-1.0) | Identity of the user, device, and application which created the item. Read-only. |
| createdDateTime | DateTimeOffset | The date and time when the section group was created. The timestamp represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. Read-only. |
| displayName | String | The name of the section group. |
| id | String | The unique identifier of the section group. Read-only. |
| lastModifiedBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-1.0) | Identity of the user, device, and application which created the item. Read-only. |
| lastModifiedDateTime | DateTimeOffset | The date and time when the section group was last modified. The timestamp represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. Read-only. |
| sectionGroupsUrl | String | The URL for the `sectionGroups` navigation property, which returns all the section groups in the section group. Read-only. |
| sectionsUrl | String | The URL for the `sections` navigation property, which returns all the sections in the section group. Read-only. |
| self | String | The endpoint where you can get details about the section group. Read-only. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| parentNotebook | [Notebook](https://learn.microsoft.com/en-us/graph/api/resources/notebook?view=graph-rest-1.0) | The notebook that contains the section group. Read-only. |
| parentSectionGroup | [SectionGroup](https://learn.microsoft.com/en-us/graph/api/resources/sectiongroup?view=graph-rest-1.0) | The section group that contains the section group. Read-only. |
| sectionGroups | [SectionGroup](https://learn.microsoft.com/en-us/graph/api/resources/sectiongroup?view=graph-rest-1.0) collection | The section groups in the section. Read-only. Nullable. |
| sections | [OnenoteSection](https://learn.microsoft.com/en-us/graph/api/resources/onenotesection?view=graph-rest-1.0) collection | The sections in the section group. Read-only. Nullable. |

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [Get section group](https://learn.microsoft.com/en-us/graph/api/sectiongroup-get?view=graph-rest-1.0) | [SectionGroup](https://learn.microsoft.com/en-us/graph/api/resources/sectiongroup?view=graph-rest-1.0) | Read the properties and relationships of the section group. |
| [Create section group](https://learn.microsoft.com/en-us/graph/api/sectiongroup-post-sectiongroups?view=graph-rest-1.0) | [SectionGroup](https://learn.microsoft.com/en-us/graph/api/resources/sectiongroup?view=graph-rest-1.0) | Create a section group by posting to the sectionGroups collection in the specified section group. |
| [List section groups](https://learn.microsoft.com/en-us/graph/api/sectiongroup-list-sectiongroups?view=graph-rest-1.0) | [SectionGroup](https://learn.microsoft.com/en-us/graph/api/resources/sectiongroup?view=graph-rest-1.0) collection | Get collection of section groups in the specified section group. |
| [Create section](https://learn.microsoft.com/en-us/graph/api/sectiongroup-post-sections?view=graph-rest-1.0) | [OnenoteSection](https://learn.microsoft.com/en-us/graph/api/resources/onenotesection?view=graph-rest-1.0) | Create a section by posting to the sections collection in the specified section group. |
| [List sections](https://learn.microsoft.com/en-us/graph/api/sectiongroup-list-sections?view=graph-rest-1.0) | [OnenoteSection](https://learn.microsoft.com/en-us/graph/api/resources/onenotesection?view=graph-rest-1.0) collection | Get a collection of sections in the specified section group. |
