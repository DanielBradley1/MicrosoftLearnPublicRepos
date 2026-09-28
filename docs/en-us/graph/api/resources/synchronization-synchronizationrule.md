<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/synchronization-synchronizationrule?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-07-03 -->

# synchronizationRule resource type

Namespace: microsoft.graph

Defines how the synchronization should be performed for the synchronization engine, including which objects to synchronize and in which direction, how objects from the source directory should be matched with objects in the target directory, and how attributes should be transformed when they're synchronized from the source to the target directory.

> **Note:** Synchronization rules define synchronization in one direction - from the source directory to the target directory. The source and target directories are defined as part of the rule properties.

Synchronization rules are configured in the **synchronizationRules** property of [synchronizationSchema](https://learn.microsoft.com/en-us/graph/api/resources/synchronization-synchronizationschema?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| editable | Boolean | `true` if the synchronization rule can be customized; `false` if this rule is read-only and shouldn't be changed. |
| id | String | Synchronization rule identifier. Must be one of the identifiers recognized by the synchronization engine. Supported rule identifiers can be found in the synchronization template returned by the API. |
| metadata | [stringKeyStringValuePair](https://learn.microsoft.com/en-us/graph/api/resources/synchronization-stringkeystringvaluepair?view=graph-rest-1.0) collection | Additional extension properties. Unless instructed explicitly by the support team, metadata values shouldn't be changed. |
| name | String | Human-readable name of the synchronization rule. Not nullable. |
| objectMappings | [objectMapping](https://learn.microsoft.com/en-us/graph/api/resources/synchronization-objectmapping?view=graph-rest-1.0) collection | Collection of object mappings supported by the rule. Tells the synchronization engine which objects should be synchronized. |
| priority | Integer | Priority relative to other rules in the [synchronizationSchema](https://learn.microsoft.com/en-us/graph/api/resources/synchronization-synchronizationschema?view=graph-rest-1.0). Rules with the lowest priority number will be processed first. |
| sourceDirectoryName | String | Name of the source directory. Must match one of the directory definitions in [synchronizationSchema](https://learn.microsoft.com/en-us/graph/api/resources/synchronization-synchronizationschema?view=graph-rest-1.0). |
| targetDirectoryName | String | Name of the target directory. Must match one of the directory definitions in [synchronizationSchema](https://learn.microsoft.com/en-us/graph/api/resources/synchronization-synchronizationschema?view=graph-rest-1.0). |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "editable": true,
  "id": "String",
  "metadata": [
    {
      "@odata.type": "microsoft.graph.stringKeyStringValuePair"
    }
  ],
  "name": "String",
  "objectMappings": [
    {
      "@odata.type": "microsoft.graph.objectMapping"
    }
  ],
  "priority": 1024,
  "sourceDirectoryName": "String",
  "targetDirectoryName": "String"
}
```
