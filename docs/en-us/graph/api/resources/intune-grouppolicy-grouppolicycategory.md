<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicycategory?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# groupPolicyCategory resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

The category entity stores the category of a group policy definition

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [Get groupPolicyCategory](https://learn.microsoft.com/en-us/graph/api/intune-grouppolicy-grouppolicycategory-get?view=graph-rest-beta) | [groupPolicyCategory](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicycategory?view=graph-rest-beta) | Read properties and relationships of the [groupPolicyCategory](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicycategory?view=graph-rest-beta) object. |
| [Update groupPolicyCategory](https://learn.microsoft.com/en-us/graph/api/intune-grouppolicy-grouppolicycategory-update?view=graph-rest-beta) | [groupPolicyCategory](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicycategory?view=graph-rest-beta) | Update the properties of a [groupPolicyCategory](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicycategory?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | The string id of the category's display name |
| isRoot | Boolean | Defines if the category is a root category |
| ingestionSource | [ingestionSource](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-ingestionsource?view=graph-rest-beta) | Defines this category's ingestion source \(0 - unknown, 1 - custom, 2 - global\). Possible values are: `unknown`, `custom`, `builtIn`, `unknownFutureValue`. |
| id | String | Key of the entity. |
| lastModifiedDateTime | DateTimeOffset | The date and time the entity was last modified. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| parent | [groupPolicyCategory](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicycategory?view=graph-rest-beta) | The parent category |
| children | [groupPolicyCategory](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicycategory?view=graph-rest-beta) collection | The children categories |
| definitions | [groupPolicyDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicydefinition?view=graph-rest-beta) collection | The immediate GroupPolicyDefinition children of the category |
| definitionFile | [groupPolicyDefinitionFile](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicydefinitionfile?view=graph-rest-beta) | The id of the definition file the category came from |

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.groupPolicyCategory",
  "displayName": "String",
  "isRoot": true,
  "ingestionSource": "String",
  "id": "String (identifier)",
  "lastModifiedDateTime": "String (timestamp)"
}
```
