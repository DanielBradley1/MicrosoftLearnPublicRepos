<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicyuploadedcategory?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# groupPolicyUploadedCategory resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

The category entity stores the category of a group policy definition

Inherits from [groupPolicyCategory](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicycategory?view=graph-rest-beta)

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List groupPolicyUploadedCategories](https://learn.microsoft.com/en-us/graph/api/intune-grouppolicy-grouppolicyuploadedcategory-list?view=graph-rest-beta) | [groupPolicyUploadedCategory](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicyuploadedcategory?view=graph-rest-beta) collection | List properties and relationships of the [groupPolicyUploadedCategory](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicyuploadedcategory?view=graph-rest-beta) objects. |
| [Get groupPolicyUploadedCategory](https://learn.microsoft.com/en-us/graph/api/intune-grouppolicy-grouppolicyuploadedcategory-get?view=graph-rest-beta) | [groupPolicyUploadedCategory](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicyuploadedcategory?view=graph-rest-beta) | Read properties and relationships of the [groupPolicyUploadedCategory](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicyuploadedcategory?view=graph-rest-beta) object. |
| [Create groupPolicyUploadedCategory](https://learn.microsoft.com/en-us/graph/api/intune-grouppolicy-grouppolicyuploadedcategory-create?view=graph-rest-beta) | [groupPolicyUploadedCategory](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicyuploadedcategory?view=graph-rest-beta) | Create a new [groupPolicyUploadedCategory](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicyuploadedcategory?view=graph-rest-beta) object. |
| [Delete groupPolicyUploadedCategory](https://learn.microsoft.com/en-us/graph/api/intune-grouppolicy-grouppolicyuploadedcategory-delete?view=graph-rest-beta) | None | Deletes a [groupPolicyUploadedCategory](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicyuploadedcategory?view=graph-rest-beta). |
| [Update groupPolicyUploadedCategory](https://learn.microsoft.com/en-us/graph/api/intune-grouppolicy-grouppolicyuploadedcategory-update?view=graph-rest-beta) | [groupPolicyUploadedCategory](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicyuploadedcategory?view=graph-rest-beta) | Update the properties of a [groupPolicyUploadedCategory](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicyuploadedcategory?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | The string id of the category's display name Inherited from [groupPolicyCategory](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicycategory?view=graph-rest-beta) |
| isRoot | Boolean | Defines if the category is a root category Inherited from [groupPolicyCategory](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicycategory?view=graph-rest-beta) |
| ingestionSource | [ingestionSource](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-ingestionsource?view=graph-rest-beta) | Defines this category's ingestion source \(0 - unknown, 1 - custom, 2 - global\) Inherited from [groupPolicyCategory](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicycategory?view=graph-rest-beta). Possible values are: `unknown`, `custom`, `builtIn`, `unknownFutureValue`. |
| id | String | Key of the entity. Inherited from [groupPolicyCategory](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicycategory?view=graph-rest-beta) |
| lastModifiedDateTime | DateTimeOffset | The date and time the entity was last modified. Inherited from [groupPolicyCategory](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicycategory?view=graph-rest-beta) |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| parent | [groupPolicyCategory](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicycategory?view=graph-rest-beta) | The parent category Inherited from [groupPolicyCategory](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicycategory?view=graph-rest-beta) |
| children | [groupPolicyCategory](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicycategory?view=graph-rest-beta) collection | The children categories Inherited from [groupPolicyCategory](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicycategory?view=graph-rest-beta) |
| definitions | [groupPolicyDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicydefinition?view=graph-rest-beta) collection | The immediate GroupPolicyDefinition children of the category Inherited from [groupPolicyCategory](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicycategory?view=graph-rest-beta) |
| definitionFile | [groupPolicyDefinitionFile](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicydefinitionfile?view=graph-rest-beta) | The id of the definition file the category came from Inherited from [groupPolicyCategory](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicycategory?view=graph-rest-beta) |

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.groupPolicyUploadedCategory",
  "displayName": "String",
  "isRoot": true,
  "ingestionSource": "String",
  "id": "String (identifier)",
  "lastModifiedDateTime": "String (timestamp)"
}
```
