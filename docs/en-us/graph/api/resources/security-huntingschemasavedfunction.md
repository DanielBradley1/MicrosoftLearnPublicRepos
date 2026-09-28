<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-huntingschemasavedfunction?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-06-24 -->

# huntingSchemaSavedFunction resource type

Namespace: microsoft.graph.security

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a custom function created by a user in advanced hunting. Custom functions allow users to save reusable query logic that can be invoked in other queries. Includes both shared functions accessible to all tenant users and personal functions visible only to their creator. Part of the [huntingSchemaFunctions](https://learn.microsoft.com/en-us/graph/api/resources/security-huntingschemafunctions?view=graph-rest-beta) returned by the [getHuntingSchema](https://learn.microsoft.com/en-us/graph/api/security-security-gethuntingschema?view=graph-rest-beta) function.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| createdBy | String | Identity of the user who created the function. |
| description | String | Description of the function purpose and usage. |
| huntingFunctionId | Int64 | Unique identifier for the function. Required. |
| inputParameters | [microsoft.graph.security.huntingSchemaFunctionParameter](https://learn.microsoft.com/en-us/graph/api/resources/security-huntingschemafunctionparameter?view=graph-rest-beta) collection | Collection of input parameters accepted by the function. |
| lastModifiedBy | String | Identity of the user who last modified the function. |
| lastModifiedDateTime | DateTimeOffset | Date and time when the function was last modified. |
| name | String | Name of the function. Required. |
| outputColumns | [microsoft.graph.security.huntingSchemaTableColumn](https://learn.microsoft.com/en-us/graph/api/resources/security-huntingschematablecolumn?view=graph-rest-beta) collection | Collection of columns returned by the function. |
| path | String | Folder path where the function is saved. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "createdBy": "String",
  "description": "String",
  "huntingFunctionId": "Int64",
  "inputParameters": [{"@odata.type": "microsoft.graph.security.huntingSchemaFunctionParameter"}],
  "lastModifiedBy": "String",
  "lastModifiedDateTime": "String (timestamp)",
  "name": "String",
  "outputColumns": [{"@odata.type": "microsoft.graph.security.huntingSchemaTableColumn"}],
  "path": "String"
}
```
