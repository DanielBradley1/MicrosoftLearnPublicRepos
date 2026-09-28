<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-huntingschemafunctionparameter?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-06-24 -->

# huntingSchemaFunctionParameter resource type

Namespace: microsoft.graph.security

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents an input parameter for an advanced hunting function. Parameters allow callers to provide arguments when invoking a function. Used by both [huntingSchemaBuiltInFunction](https://learn.microsoft.com/en-us/graph/api/resources/security-huntingschemabuiltinfunction?view=graph-rest-beta) and [huntingSchemaSavedFunction](https://learn.microsoft.com/en-us/graph/api/resources/security-huntingschemasavedfunction?view=graph-rest-beta) resource types.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| cslType | String | Data type of the parameter in Kusto Query Language \(KQL\) CSL format. Required. |
| defaultValue | String | Default value used when the caller doesn't provide a value for this parameter. |
| name | String | Name of the parameter. Required. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "cslType": "String",
  "defaultValue": "String",
  "name": "String"
}
```
