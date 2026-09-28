<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/columndefinition?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-06-30 -->

# columnDefinition resource type

Namespace: microsoft.graph

Represents a column in a [site](https://learn.microsoft.com/en-us/graph/api/resources/site?view=graph-rest-1.0), [list](https://learn.microsoft.com/en-us/graph/api/resources/list?view=graph-rest-1.0), or [contentType](https://learn.microsoft.com/en-us/graph/api/resources/contenttype?view=graph-rest-1.0).

By default, **columnDefinitions** and field values for `hidden` columns aren't shown. To list hidden **columnDefinitions**, include `hidden` in your `$select` statement. To list hidden **field** values on [listItems](https://learn.microsoft.com/en-us/graph/api/resources/listitem?view=graph-rest-1.0), include the desired columns by name in your `$select` statement.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List columns in a site](https://learn.microsoft.com/en-us/graph/api/site-list-columns?view=graph-rest-1.0) | [columnDefinition](https://learn.microsoft.com/en-us/graph/api/resources/columndefinition?view=graph-rest-1.0) collection | Get a list of the [columnDefinition](https://learn.microsoft.com/en-us/graph/api/resources/columndefinition?view=graph-rest-1.0) objects and their properties in a [site](https://learn.microsoft.com/en-us/graph/api/resources/site?view=graph-rest-1.0). |
| [List columns in a list](https://learn.microsoft.com/en-us/graph/api/list-list-columns?view=graph-rest-1.0) | [columnDefinition](https://learn.microsoft.com/en-us/graph/api/resources/columndefinition?view=graph-rest-1.0) collection | Get a list of the [columnDefinition](https://learn.microsoft.com/en-us/graph/api/resources/columndefinition?view=graph-rest-1.0) objects and their properties in a [list](https://learn.microsoft.com/en-us/graph/api/resources/list?view=graph-rest-1.0). |
| [List columns in a content type](https://learn.microsoft.com/en-us/graph/api/contenttype-list-columns?view=graph-rest-1.0) | [columnDefinition](https://learn.microsoft.com/en-us/graph/api/resources/columndefinition?view=graph-rest-1.0) collection | Get a list of the [columnDefinition](https://learn.microsoft.com/en-us/graph/api/resources/columndefinition?view=graph-rest-1.0) objects and their properties in a [content type](https://learn.microsoft.com/en-us/graph/api/resources/contenttype?view=graph-rest-1.0). |
| [Create columnDefinition for a site](https://learn.microsoft.com/en-us/graph/api/site-post-columns?view=graph-rest-1.0) | [columnDefinition](https://learn.microsoft.com/en-us/graph/api/resources/columndefinition?view=graph-rest-1.0) | Create a new [columnDefinition](https://learn.microsoft.com/en-us/graph/api/resources/columndefinition?view=graph-rest-1.0) object in a [site](https://learn.microsoft.com/en-us/graph/api/resources/site?view=graph-rest-1.0). |
| [Create columnDefinition for a list](https://learn.microsoft.com/en-us/graph/api/list-post-columns?view=graph-rest-1.0) | [columnDefinition](https://learn.microsoft.com/en-us/graph/api/resources/columndefinition?view=graph-rest-1.0) | Create a new [columnDefinition](https://learn.microsoft.com/en-us/graph/api/resources/columndefinition?view=graph-rest-1.0) object in a [list](https://learn.microsoft.com/en-us/graph/api/resources/list?view=graph-rest-1.0). |
| [Create columnDefinition for a content type](https://learn.microsoft.com/en-us/graph/api/contenttype-post-columns?view=graph-rest-1.0) | [columnDefinition](https://learn.microsoft.com/en-us/graph/api/resources/columndefinition?view=graph-rest-1.0) | Create a new [columnDefinition](https://learn.microsoft.com/en-us/graph/api/resources/columndefinition?view=graph-rest-1.0) object in a [content type](https://learn.microsoft.com/en-us/graph/api/resources/contenttype?view=graph-rest-1.0). |
| [Get columnDefinition](https://learn.microsoft.com/en-us/graph/api/columndefinition-get?view=graph-rest-1.0) | [columnDefinition](https://learn.microsoft.com/en-us/graph/api/resources/columndefinition?view=graph-rest-1.0) | Read the properties and relationships of a [columnDefinition](https://learn.microsoft.com/en-us/graph/api/resources/columndefinition?view=graph-rest-1.0) object. |
| [Update columnDefinition](https://learn.microsoft.com/en-us/graph/api/columndefinition-update?view=graph-rest-1.0) | [columnDefinition](https://learn.microsoft.com/en-us/graph/api/resources/columndefinition?view=graph-rest-1.0) | Update the properties of a [columnDefinition](https://learn.microsoft.com/en-us/graph/api/resources/columndefinition?view=graph-rest-1.0) object. |
| [Delete columnDefinition](https://learn.microsoft.com/en-us/graph/api/columndefinition-delete?view=graph-rest-1.0) | None | Delete a [columnDefinition](https://learn.microsoft.com/en-us/graph/api/resources/columndefinition?view=graph-rest-1.0) object. |

## Properties

Columns can hold data of various types. The following properties indicate what type of data a column stores, as well as additional settings for that data. The type-related properties \(Boolean, calculated, choice, currency, dateTime, lookup, number, personOrGroup, text, term, hyperlinkOrPicture, thumbnail, and contentApprovalStatus\) are mutually exclusive; a column can only have one of them specified.

| Property name | Type | Description |
| :--- | :--- | :--- |
| **boolean** | [booleanColumn](https://learn.microsoft.com/en-us/graph/api/resources/booleancolumn?view=graph-rest-1.0) | This column stores Boolean values. |
| **calculated** | [calculatedColumn](https://learn.microsoft.com/en-us/graph/api/resources/calculatedcolumn?view=graph-rest-1.0) | This column's data is calculated based on other columns. |
| **choice** | [choiceColumn](https://learn.microsoft.com/en-us/graph/api/resources/choicecolumn?view=graph-rest-1.0) | This column stores data from a list of choices. |
| **columnGroup** | string | For site columns, the name of the group this column belongs to. Helps organize related columns. |
| **contentApprovalStatus** | [contentApprovalStatusColumn](https://learn.microsoft.com/en-us/graph/api/resources/contentapprovalstatuscolumn?view=graph-rest-1.0) | This column stores content approval status. |
| **currency** | [currencyColumn](https://learn.microsoft.com/en-us/graph/api/resources/currencycolumn?view=graph-rest-1.0) | This column stores currency values. |
| **dateTime** | [dateTimeColumn](https://learn.microsoft.com/en-us/graph/api/resources/datetimecolumn?view=graph-rest-1.0) | This column stores DateTime values. |
| **defaultValue** | [defaultColumnValue](https://learn.microsoft.com/en-us/graph/api/resources/defaultcolumnvalue?view=graph-rest-1.0) | The default value for this column. |
| **description** | string | The user-facing description of the column. |
| **displayName** | string | The user-facing name of the column. |
| **enforceUniqueValues** | Boolean | If `true`, no two list items may have the same value for this column. |
| **geolocation** | [geolocationColumn](https://learn.microsoft.com/en-us/graph/api/resources/geolocationcolumn?view=graph-rest-1.0) | This column stores a geolocation. |
| **hidden** | Boolean | Specifies whether the column is displayed in the user interface. |
| **hyperlinkOrPicture** | [hyperlinkOrPictureColumn](https://learn.microsoft.com/en-us/graph/api/resources/hyperlinkorpicturecolumn?view=graph-rest-1.0) | This column stores hyperlink or picture values. |
| **isDeletable** | Boolean | Indicates whether this column can be deleted. |
| **isReorderable** | Boolean | Indicates whether values in the column can be reordered. Read-only. |
| **id** | string | The unique identifier for the column. |
| **indexed** | Boolean | Specifies whether the column values can be used for sorting and searching. |
| **isSealed** | Boolean | Specifies whether the column can be changed. |
| **lookup** | [lookupColumn](https://learn.microsoft.com/en-us/graph/api/resources/lookupcolumn?view=graph-rest-1.0) | This column's data is looked up from another source in the site. |
| **name** | string | The API-facing name of the column as it appears in the [fields](https://learn.microsoft.com/en-us/graph/api/resources/fieldvalueset?view=graph-rest-1.0) on a [listItem](https://learn.microsoft.com/en-us/graph/api/resources/listitem?view=graph-rest-1.0). For the user-facing name, see **displayName**. |
| **number** | [numberColumn](https://learn.microsoft.com/en-us/graph/api/resources/numbercolumn?view=graph-rest-1.0) | This column stores number values. |
| **personOrGroup** | [personOrGroupColumn](https://learn.microsoft.com/en-us/graph/api/resources/personorgroupcolumn?view=graph-rest-1.0) | This column stores Person or Group values. |
| **propagateChanges** | Boolean | If 'true', changes to this column will be propagated to lists that implement the column. |
| **readOnly** | Boolean | Specifies whether the column values can be modified. |
| **required** | Boolean | Specifies whether the column value isn't optional. |
| **sourceContentType** | [contentTypeInfo](https://learn.microsoft.com/en-us/graph/api/resources/contenttypeinfo?view=graph-rest-1.0) | ContentType from which this column is inherited from. Present only in contentTypes columns response. Read-only. |
| **term** | [termColumn](https://learn.microsoft.com/en-us/graph/api/resources/termcolumn?view=graph-rest-1.0) | This column stores taxonomy terms. |
| **text** | [textColumn](https://learn.microsoft.com/en-us/graph/api/resources/textcolumn?view=graph-rest-1.0) | This column stores text values. |
| **thumbnail** | [thumbnailColumn](https://learn.microsoft.com/en-us/graph/api/resources/thumbnailcolumn?view=graph-rest-1.0) | This column stores thumbnail values. |
| **type** | columnTypes | For site columns, the type of column. Read-only. |
| **validation** | [columnValidation](https://learn.microsoft.com/en-us/graph/api/resources/columnvalidation?view=graph-rest-1.0) | This column stores validation formula and message for the column. |

## Relationships

| Property name | Type | Description |
| :--- | :--- | :--- |
| **sourceColumn** | [columnDefinition](https://learn.microsoft.com/en-us/graph/api/resources/columndefinition?view=graph-rest-1.0) | The source column for the content type column. |

> **Note:** These properties correspond to the SharePoint [SPFieldType](https://learn.microsoft.com/en-us/previous-versions/office/sharepoint-server/ms428806\(v=office.15\)) enumeration. Note that the most common field types are represented in the previous table. However, this API is still missing some. In those cases, none of the column type facets will be populated, and the column will only have its basic properties. Sites and list columns response won't contain **isDeletable**, **propagateChanges**, **isReorderable**, **isSealed**, **validation**, **hyperlinkOrPicture**, **term**, **sourceContentType**, **thumbnail**, **type**, **contentApprovalStatus**, and **sourceColumn** properties.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "boolean": { "@odata.type": "microsoft.graph.booleanColumn" },
  "calculated": { "@odata.type": "microsoft.graph.calculatedColumn" },
  "choice": { "@odata.type": "microsoft.graph.choiceColumn" },
  "columnGroup": "String",
  "contentApprovalStatus": { "@odata.type": "microsoft.graph.contentApprovalStatusColumn" },
  "currency": { "@odata.type": "microsoft.graph.currencyColumn" },
  "dateTime": { "@odata.type": "microsoft.graph.dateTimeColumn" },
  "defaultValue": { "@odata.type": "microsoft.graph.defaultColumnValue" },
  "description": "String",
  "displayName": "String",
  "enforceUniqueValues": "Boolean",
  "geolocation": { "@odata.type": "microsoft.graph.geolocationColumn" },
  "hidden": "Boolean",
  "hyperlinkOrPicture": { "@odata.type": "microsoft.graph.hyperlinkOrPictureColumn" },
  "id": "String (identifier)",
  "indexed": "Boolean",
  "isDeletable" : "Boolean",
  "isReorderable": "Boolean",
  "isSealed": "Boolean",
  "lookup": { "@odata.type": "microsoft.graph.lookupColumn" },
  "name": "staticNameForApi",
  "number": { "@odata.type": "microsoft.graph.numberColumn" },
  "personOrGroup": { "@odata.type": "microsoft.graph.personOrGroupColumn" },
  "readOnly": "Boolean",
  "required": "Boolean",
  "propagateChanges": "Boolean",
  "sourceContentType": { "@odata.type": "microsoft.graph.contentTypeInfo" },
  "term": { "@odata.type": "microsoft.graph.termColumn" },
  "text": { "@odata.type": "microsoft.graph.textColumn" },
  "thumbnail": { "@odata.type": "microsoft.graph.thumbnailColumn" },
  "type": { "@odata.type": "microsoft.graph.columnTypes" },
  "validation": { "@odata.type": "microsoft.graph.columnValidation" }
}
```
