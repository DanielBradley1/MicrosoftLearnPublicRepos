<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-huntingschematablecolumn?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-09-23 -->

# huntingSchemaTableColumn resource type

Namespace: microsoft.graph.security

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a column in an advanced hunting table. Part of the [huntingSchemaTable](https://learn.microsoft.com/en-us/graph/api/resources/security-huntingschematable?view=graph-rest-beta) returned by the [getHuntingSchema](https://learn.microsoft.com/en-us/graph/api/security-security-gethuntingschema?view=graph-rest-beta) and [getHuntingSchemaTables](https://learn.microsoft.com/en-us/graph/api/security-security-gethuntingschematables?view=graph-rest-beta) functions.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| dataType | String | Data type of the column \(for example, `DateTime`, `String`\). Required. |
| description | String | Description of the column. |
| name | String | Name of the column. Required. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "dataType": "String",
  "description": "String",
  "name": "String"
}
```
