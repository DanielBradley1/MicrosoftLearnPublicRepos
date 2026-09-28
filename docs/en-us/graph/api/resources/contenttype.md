<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/contenttype?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-03-26 -->

# contentType resource type

Namespace: microsoft.graph

Represents a content type in SharePoint. Content types allow you to define a set of columns that must be present on every [**listItem**](https://learn.microsoft.com/en-us/graph/api/resources/listitem?view=graph-rest-1.0) in a [**list**](https://learn.microsoft.com/en-us/graph/api/resources/list?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List contentTypes in a site](https://learn.microsoft.com/en-us/graph/api/site-list-contenttypes?view=graph-rest-1.0) | [contentType](https://learn.microsoft.com/en-us/graph/api/resources/contenttype?view=graph-rest-1.0) collection | Get a list of the [contentType](https://learn.microsoft.com/en-us/graph/api/resources/contenttype?view=graph-rest-1.0) objects and their properties in a [site](https://learn.microsoft.com/en-us/graph/api/resources/site?view=graph-rest-1.0). |
| [List contentTypes in a list](https://learn.microsoft.com/en-us/graph/api/list-list-contenttypes?view=graph-rest-1.0) | [contentType](https://learn.microsoft.com/en-us/graph/api/resources/contenttype?view=graph-rest-1.0) collection | Get a list of the [contentType](https://learn.microsoft.com/en-us/graph/api/resources/contenttype?view=graph-rest-1.0) objects and their properties in a [list](https://learn.microsoft.com/en-us/graph/api/resources/list?view=graph-rest-1.0). |
| [Create contentType for a site](https://learn.microsoft.com/en-us/graph/api/site-post-contenttypes?view=graph-rest-1.0) | [contentType](https://learn.microsoft.com/en-us/graph/api/resources/contenttype?view=graph-rest-1.0) | Create a new [contentType](https://learn.microsoft.com/en-us/graph/api/resources/contenttype?view=graph-rest-1.0) object in a [site](https://learn.microsoft.com/en-us/graph/api/resources/site?view=graph-rest-1.0). |
| [Get contentType](https://learn.microsoft.com/en-us/graph/api/contenttype-get?view=graph-rest-1.0) | [contentType](https://learn.microsoft.com/en-us/graph/api/resources/contenttype?view=graph-rest-1.0) | Read the properties and relationships of a [contentType](https://learn.microsoft.com/en-us/graph/api/resources/contenttype?view=graph-rest-1.0) object. |
| [Update contentType](https://learn.microsoft.com/en-us/graph/api/contenttype-update?view=graph-rest-1.0) | [contentType](https://learn.microsoft.com/en-us/graph/api/resources/contenttype?view=graph-rest-1.0) | Update the properties of a [contentType](https://learn.microsoft.com/en-us/graph/api/resources/contenttype?view=graph-rest-1.0) object. |
| [Delete contentType](https://learn.microsoft.com/en-us/graph/api/contenttype-delete?view=graph-rest-1.0) | None | Delete a [contentType](https://learn.microsoft.com/en-us/graph/api/resources/contenttype?view=graph-rest-1.0) object. |
| [isPublished](https://learn.microsoft.com/en-us/graph/api/contenttype-ispublished?view=graph-rest-1.0) | Boolean | Indicates whether the [contentType](https://learn.microsoft.com/en-us/graph/api/resources/contenttype?view=graph-rest-1.0) is published. |
| [publish](https://learn.microsoft.com/en-us/graph/api/contenttype-publish?view=graph-rest-1.0) | [contentType](https://learn.microsoft.com/en-us/graph/api/resources/contenttype?view=graph-rest-1.0) | Publish a [contentType](https://learn.microsoft.com/en-us/graph/api/resources/contenttype?view=graph-rest-1.0). |
| [unpublish](https://learn.microsoft.com/en-us/graph/api/contenttype-unpublish?view=graph-rest-1.0) | [contentType](https://learn.microsoft.com/en-us/graph/api/resources/contenttype?view=graph-rest-1.0) | Unpublish a [contentType](https://learn.microsoft.com/en-us/graph/api/resources/contenttype?view=graph-rest-1.0). |
| [addCopy](https://learn.microsoft.com/en-us/graph/api/contenttype-addcopy?view=graph-rest-1.0) | [contentType](https://learn.microsoft.com/en-us/graph/api/resources/contenttype?view=graph-rest-1.0) | Add copy of a [contentType](https://learn.microsoft.com/en-us/graph/api/resources/contenttype?view=graph-rest-1.0) from a [site](https://learn.microsoft.com/en-us/graph/api/resources/site?view=graph-rest-1.0) to a [list](https://learn.microsoft.com/en-us/graph/api/resources/list?view=graph-rest-1.0). |
| [associateWithHubSites](https://learn.microsoft.com/en-us/graph/api/contenttype-associatewithhubsites?view=graph-rest-1.0) | [contentType](https://learn.microsoft.com/en-us/graph/api/resources/contenttype?view=graph-rest-1.0) | Associate a [contentType](https://learn.microsoft.com/en-us/graph/api/resources/contenttype?view=graph-rest-1.0) with a list of hub sites. |
| [copyToDefaultContentLocation](https://learn.microsoft.com/en-us/graph/api/contenttype-copytodefaultcontentlocation?view=graph-rest-1.0) | [contentType](https://learn.microsoft.com/en-us/graph/api/resources/contenttype?view=graph-rest-1.0) | Copy a file to default content location in a [contentType](https://learn.microsoft.com/en-us/graph/api/resources/contenttype?view=graph-rest-1.0). |
| [List columns](https://learn.microsoft.com/en-us/graph/api/contenttype-list-columns?view=graph-rest-1.0) | [columnDefinition](https://learn.microsoft.com/en-us/graph/api/resources/columndefinition?view=graph-rest-1.0) collection | Get a collection of columns, represented as [columnDefinition](https://learn.microsoft.com/en-us/graph/api/resources/columndefinition?view=graph-rest-1.0) resources, in a **contentType**. |
| [Create column](https://learn.microsoft.com/en-us/graph/api/contenttype-post-columns?view=graph-rest-1.0) | [columnDefinition](https://learn.microsoft.com/en-us/graph/api/resources/columndefinition?view=graph-rest-1.0) | Add a column to a **content type** in a site or list. |
| [getCompatibleHubContentTypes](https://learn.microsoft.com/en-us/graph/api/contenttype-getcompatiblehubcontenttypes?view=graph-rest-1.0) | [contentType](https://learn.microsoft.com/en-us/graph/api/resources/contenttype?view=graph-rest-1.0) collection | Get a list of compatible content types from the content type hub that can be added to a target [site](https://learn.microsoft.com/en-us/graph/api/resources/site?view=graph-rest-1.0) or a [list](https://learn.microsoft.com/en-us/graph/api/resources/list?view=graph-rest-1.0). |
| [addCopyFromContentTypeHub](https://learn.microsoft.com/en-us/graph/api/contenttype-addcopyfromcontenttypehub?view=graph-rest-1.0) | [contentType](https://learn.microsoft.com/en-us/graph/api/resources/contenttype?view=graph-rest-1.0) | Add or sync a copy of a published content type from the content type hub to a target [site](https://learn.microsoft.com/en-us/graph/api/resources/site?view=graph-rest-1.0) or a [list](https://learn.microsoft.com/en-us/graph/api/resources/list?view=graph-rest-1.0). |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| associatedHubsUrls | String collection | List of canonical URLs for hub sites with which this content type is associated to. This will contain all hub sites where this content type is queued to be enforced or is already enforced. Enforcing a content type means that the content type is applied to the lists in the enforced sites. |
| description | string | The descriptive text for the item. |
| documentSet | [documentSet](https://learn.microsoft.com/en-us/graph/api/resources/documentset?view=graph-rest-1.0) | [Document Set](https://learn.microsoft.com/en-us/sharepoint/governance/document-set-planning#about-document-sets) metadata. |
| documentTemplate | [documentSetContent](https://learn.microsoft.com/en-us/graph/api/resources/documentsetcontent?view=graph-rest-1.0) | Document template metadata. To make sure that documents have consistent content across a site and its subsites, you can associate a Word, Excel, or PowerPoint template with a site content type. |
| group | string | The name of the group this content type belongs to. Helps organize related content types. |
| hidden | Boolean | Indicates whether the content type is hidden in the list's 'New' menu. |
| id | string | The unique identifier of the content type. |
| inheritedFrom | [itemReference](https://learn.microsoft.com/en-us/graph/api/resources/itemreference?view=graph-rest-1.0) | If this content type is inherited from another scope \(like a site\), provides a reference to the item where the content type is defined. |
| isBuiltIn | Boolean | Specifies if a content type is a built-in content type. |
| name | string | The name of the content type. |
| order | [contentTypeOrder](https://learn.microsoft.com/en-us/graph/api/resources/contenttypeorder?view=graph-rest-1.0) | Specifies the order in which the content type appears in the selection UI. |
| parentId | string | The unique identifier of the content type. |
| propagateChanges | Boolean | If `true`, any changes made to the content type are pushed to inherited content types and lists that implement the content type. |
| readOnly | Boolean | If `true`, the content type can't be modified unless this value is first set to `false`. |
| sealed | Boolean | If `true`, the content type can't be modified by users or through push-down operations. Only site collection administrators can seal or unseal content types. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| base | [contentType](https://learn.microsoft.com/en-us/graph/api/resources/contenttype?view=graph-rest-1.0) | Parent contentType from which this content type is derived. |
| baseTypes | [contentType](https://learn.microsoft.com/en-us/graph/api/resources/contenttype?view=graph-rest-1.0) collection | The collection of content types that are ancestors of this content type. |
| columnLinks | [columnLink](https://learn.microsoft.com/en-us/graph/api/resources/columnlink?view=graph-rest-1.0) collection | The collection of columns that are required by this content type. |
| columnPositions | [columnDefinition](https://learn.microsoft.com/en-us/graph/api/resources/columndefinition?view=graph-rest-1.0) collection | Column order information in a content type. |
| columns | [columnDefinition](https://learn.microsoft.com/en-us/graph/api/resources/columndefinition?view=graph-rest-1.0) collection | The collection of column definitions for this content type. |

For more information, see [Introduction to content types and content type publishing](https://support.office.com/en-us/article/Introduction-to-content-types-and-content-type-publishing-e1277a2e-a1e8-4473-9126-91a0647766e5).

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "associatedHubsUrls" : ["string"],
  "base": { "@type": "microsoft.graph.contentType" },
  "baseTypes" : [{ "@type": "microsoft.graph.contentType" }],
  "columns" : [{ "@type": "microsoft.graph.columnDefinition" }],
  "columnLinks": [{ "@type": "microsoft.graph.columnLink" }],
  "columnPositions" : [{ "@type": "microsoft.graph.columnDefinition" }],
  "description": "string",
  "documentSet" : { "@type": "microsoft.graph.documentSet" },
  "documentTemplate" : { "@type": "microsoft.graph.documentSetContent" },
  "group": "string",
  "hidden": "Boolean",
  "id": "string",
  "inheritedFrom": { "@type": "microsoft.graph.itemReference" },
  "isBuiltIn" : "Boolean",
  "name": "string",
  "order": { "@type": "microsoft.graph.contentTypeOrder" },
  "parentId": "string",
  "propagateChanges" : "Boolean",
  "readOnly": "Boolean",
  "sealed": "Boolean"
}
```
