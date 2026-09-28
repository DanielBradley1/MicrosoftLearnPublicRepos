<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoveryreviewtag?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-12-03 -->

# ediscoveryReviewTag resource type

Namespace: microsoft.graph.security

Represents an eDiscovery tag, which is used to mark documents during review to separate responsive and nonresponsive content.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/security-ediscoverycase-list-tags?view=graph-rest-1.0) | [microsoft.graph.security.ediscoveryReviewTag](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoveryreviewtag?view=graph-rest-1.0) collection | Get a list of the [ediscoveryReviewTag](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoveryreviewtag?view=graph-rest-1.0) objects and their properties. |
| [Create](https://learn.microsoft.com/en-us/graph/api/security-ediscoverycase-post-tags?view=graph-rest-1.0) | [microsoft.graph.security.ediscoveryReviewTag](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoveryreviewtag?view=graph-rest-1.0) | Create a new [ediscoveryReviewTag](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoveryreviewtag?view=graph-rest-1.0) object. |
| [Get](https://learn.microsoft.com/en-us/graph/api/security-ediscoveryreviewtag-get?view=graph-rest-1.0) | [microsoft.graph.security.ediscoveryReviewTag](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoveryreviewtag?view=graph-rest-1.0) | Read the properties and relationships of an [ediscoveryReviewTag](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoveryreviewtag?view=graph-rest-1.0) object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/security-ediscoveryreviewtag-update?view=graph-rest-1.0) | [microsoft.graph.security.ediscoveryReviewTag](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoveryreviewtag?view=graph-rest-1.0) | Update the properties of an [ediscoveryReviewTag](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoveryreviewtag?view=graph-rest-1.0) object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/security-ediscoverycase-delete-tags?view=graph-rest-1.0) | None | Delete an [ediscoveryReviewTag](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoveryreviewtag?view=graph-rest-1.0) object. |
| [List tags as hierarchy](https://learn.microsoft.com/en-us/graph/api/security-ediscoveryreviewtag-ashierarchy?view=graph-rest-1.0) | [microsoft.graph.security.ediscoveryReviewTag](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoveryreviewtag?view=graph-rest-1.0) collection | List tags organized as hierarchy. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| childSelectability | microsoft.graph.security.childSelectability | Indicates whether a single or multiple child tags can be associated with a document. The possible values are: `One`, `Many`. This value controls whether the UX presents the tags as checkboxes or a radio button group. |
| createdBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-1.0) | The user who created the tag. |
| description | String | The description for the tag. |
| displayName | String | Display name of the tag. |
| id | String | Unique identifier for the tag. |
| lastModifiedDateTime | DateTimeOffset | The date and time the tag was last modified. |

### childSelectability values

| Member | Description |
| :--- | --- |
| One | Only one child can be selected. This corresponds to a UI that presents the tags with radio buttons. |
| Many | Zero or many children can be selected. This corresponds to a UI that presents the tags with checkboxes. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| childTags | [microsoft.graph.security.ediscoveryReviewTag](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoveryreviewtag?view=graph-rest-1.0) collection | Returns the tags that are a child of a tag. |
| parent | [microsoft.graph.security.ediscoveryReviewTag](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoveryreviewtag?view=graph-rest-1.0) | Returns the parent tag of the specified tag. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.ediscoveryReviewTag",
  "id": "String (identifier)",
  "displayName": "String",
  "description": "String",
  "createdBy": {
    "@odata.type": "microsoft.graph.identitySet"
  },
  "lastModifiedDateTime": "String (timestamp)",
  "childSelectability": "String"
}
```
