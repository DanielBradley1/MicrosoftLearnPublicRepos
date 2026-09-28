<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/ediscovery-tag?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-12-10 -->

# tag resource type

Namespace: microsoft.graph.ediscovery

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Caution

The eDiscovery APIs in the microsoft.graph.eDiscovery subnamespace are deprecated. Use the new [eDiscovery APIs under microsoft.graph.security subnamespace](https://learn.microsoft.com/en-us/graph/api/resources/security-api-overview#ediscovery).

Represents an eDiscovery tag, which is used to mark documents during review to separate responsive and non-responsive content.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/ediscovery-case-list-tags?view=graph-rest-beta) | [microsoft.graph.ediscovery.tag](https://learn.microsoft.com/en-us/graph/api/resources/ediscovery-tag?view=graph-rest-beta) collection | Get a list of the **tag** objects and their properties. |
| [Create](https://learn.microsoft.com/en-us/graph/api/ediscovery-case-post-tags?view=graph-rest-beta) | [microsoft.graph.ediscovery.tag](https://learn.microsoft.com/en-us/graph/api/resources/ediscovery-tag?view=graph-rest-beta) | Create a new **tag** object. |
| [Get](https://learn.microsoft.com/en-us/graph/api/ediscovery-tag-get?view=graph-rest-beta) | [microsoft.graph.ediscovery.tag](https://learn.microsoft.com/en-us/graph/api/resources/ediscovery-tag?view=graph-rest-beta) | Read the properties and relationships of a **tag** object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/ediscovery-tag-update?view=graph-rest-beta) | [microsoft.graph.ediscovery.tag](https://learn.microsoft.com/en-us/graph/api/resources/ediscovery-tag?view=graph-rest-beta) | Update the properties of a **tag** object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/ediscovery-tag-delete?view=graph-rest-beta) | None | Delete a **tag** object. |
| [List tags as hierarchy](https://learn.microsoft.com/en-us/graph/api/ediscovery-tag-ashierarchy?view=graph-rest-beta) | [microsoft.graph.ediscovery.tag](https://learn.microsoft.com/en-us/graph/api/resources/ediscovery-tag?view=graph-rest-beta) collection | Lists all tags, including their hierarchy. |
| [List child tags](https://learn.microsoft.com/en-us/graph/api/ediscovery-tag-childtags?view=graph-rest-beta) | [microsoft.graph.ediscovery.tag](https://learn.microsoft.com/en-us/graph/api/resources/ediscovery-tag?view=graph-rest-beta) collection | Get a list of child **tag** objects associated with a tag. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| childSelectability | [microsoft.graph.ediscovery.childSelectability](https://learn.microsoft.com/en-us/graph/api/resources/ediscovery-tag?view=graph-rest-beta#childselectability-values) | Indicates whether a single or multiple child tags can be associated with a document. The possible values are: `One`, `Many`. This value controls whether the UX presents the tags as checkboxes or a radio button group. |
| createdBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-beta) | The user who created the tag. |
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
| childTags | [microsoft.graph.ediscovery.tag](https://learn.microsoft.com/en-us/graph/api/resources/ediscovery-tag?view=graph-rest-beta) collection | Returns the tags that are a child of a tag. |
| parent | [microsoft.graph.ediscovery.tag](https://learn.microsoft.com/en-us/graph/api/resources/ediscovery-tag?view=graph-rest-beta) | Returns the parent tag of the specified tag. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.ediscovery.tag",
  "id": "String (identifier)",
  "displayName": "String",
  "description": "String",
  "childSelectability": "String",
  "createdBy": {
    "@odata.type": "microsoft.graph.identitySet"
  },
  "lastModifiedDateTime": "String (timestamp)"
}
```
