<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-huntingschematable?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-09-23 -->

# huntingSchemaTable resource type

Namespace: microsoft.graph.security

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents an advanced hunting table accessible to the user. Part of the [huntingSchemaResult](https://learn.microsoft.com/en-us/graph/api/resources/security-huntingschemaresult?view=graph-rest-beta) returned by the [getHuntingSchema](https://learn.microsoft.com/en-us/graph/api/security-security-gethuntingschema?view=graph-rest-beta) function, and returned as a collection by the [getHuntingSchemaTables](https://learn.microsoft.com/en-us/graph/api/security-security-gethuntingschematables?view=graph-rest-beta) function.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| columns | [microsoft.graph.security.huntingSchemaTableColumn](https://learn.microsoft.com/en-us/graph/api/resources/security-huntingschematablecolumn?view=graph-rest-beta) collection | Collection of columns in the table with their data types. |
| description | String | Description of what data the table contains. |
| name | String | Name of the table. Required. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "name": "String",
  "description": "String",
  "columns": [{"@odata.type": "microsoft.graph.security.huntingSchemaTableColumn"}]
}
```
