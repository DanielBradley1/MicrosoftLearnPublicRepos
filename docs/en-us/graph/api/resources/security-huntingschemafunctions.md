<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-huntingschemafunctions?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-06-24 -->

# huntingSchemaFunctions resource type

Namespace: microsoft.graph.security

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Contains the two categories of advanced hunting functions accessible to the user: built-in functions and saved functions. Part of the [huntingSchemaResult](https://learn.microsoft.com/en-us/graph/api/resources/security-huntingschemaresult?view=graph-rest-beta) returned by the [getHuntingSchema](https://learn.microsoft.com/en-us/graph/api/security-security-gethuntingschema?view=graph-rest-beta) function.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| builtInFunctions | [microsoft.graph.security.huntingSchemaBuiltInFunction](https://learn.microsoft.com/en-us/graph/api/resources/security-huntingschemabuiltinfunction?view=graph-rest-beta) collection | Prebuilt functions included with Microsoft Defender XDR advanced hunting. |
| savedFunctions | [microsoft.graph.security.huntingSchemaSavedFunction](https://learn.microsoft.com/en-us/graph/api/resources/security-huntingschemasavedfunction?view=graph-rest-beta) collection | Custom functions created by users, including shared functions accessible to all tenant users and personal functions visible only to their creator. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "builtInFunctions": [{"@odata.type": "microsoft.graph.security.huntingSchemaBuiltInFunction"}],
  "savedFunctions": [{"@odata.type": "microsoft.graph.security.huntingSchemaSavedFunction"}]
}
```
