<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-huntingschemaresult?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-06-24 -->

# huntingSchemaResult resource type

Namespace: microsoft.graph.security

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Contains the advanced hunting schema accessible to the signed-in user, including tables and functions. Returned by the [getHuntingSchema](https://learn.microsoft.com/en-us/graph/api/security-security-gethuntingschema?view=graph-rest-beta) function.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| functions | [microsoft.graph.security.huntingSchemaFunctions](https://learn.microsoft.com/en-us/graph/api/resources/security-huntingschemafunctions?view=graph-rest-beta) | Object containing the built-in functions and saved functions available to the user. |
| tables | [microsoft.graph.security.huntingSchemaTable](https://learn.microsoft.com/en-us/graph/api/resources/security-huntingschematable?view=graph-rest-beta) collection | Collection of advanced hunting tables the user is authorized to query. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "tables": [{"@odata.type": "microsoft.graph.security.huntingSchemaTable"}],
  "functions": {"@odata.type": "microsoft.graph.security.huntingSchemaFunctions"}
}
```
