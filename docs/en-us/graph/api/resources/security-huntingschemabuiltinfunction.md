<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-huntingschemabuiltinfunction?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-06-24 -->

# huntingSchemaBuiltInFunction resource type

Namespace: microsoft.graph.security

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a prebuilt function included with Microsoft Defender XDR advanced hunting. Built-in functions are available to all advanced hunting instances and can't be modified by users. Part of the [huntingSchemaFunctions](https://learn.microsoft.com/en-us/graph/api/resources/security-huntingschemafunctions?view=graph-rest-beta) returned by the [getHuntingSchema](https://learn.microsoft.com/en-us/graph/api/security-security-gethuntingschema?view=graph-rest-beta) function.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| documentation | String | Description of the function and its usage. |
| huntingFunctionId | Int64 | Unique identifier for the function. Required. |
| inputParameters | [microsoft.graph.security.huntingSchemaFunctionParameter](https://learn.microsoft.com/en-us/graph/api/resources/security-huntingschemafunctionparameter?view=graph-rest-beta) collection | Collection of input parameters accepted by the function. |
| name | String | Name of the function. Required. |
| outputColumns | [microsoft.graph.security.huntingSchemaTableColumn](https://learn.microsoft.com/en-us/graph/api/resources/security-huntingschematablecolumn?view=graph-rest-beta) collection | Collection of columns returned by the function. |
| path | String | Folder path of the function. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "documentation": "String",
  "huntingFunctionId": "Int64",
  "inputParameters": [{"@odata.type": "microsoft.graph.security.huntingSchemaFunctionParameter"}],
  "name": "String",
  "outputColumns": [{"@odata.type": "microsoft.graph.security.huntingSchemaTableColumn"}],
  "path": "String"
}
```
