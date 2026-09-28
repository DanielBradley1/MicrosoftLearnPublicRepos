<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/synchronization-referencedobject?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-07-03 -->

# referencedObject resource type

Namespace: microsoft.graph

Describes a reference to another object defined in the same [directory definition](https://learn.microsoft.com/en-us/graph/api/resources/synchronization-directorydefinition?view=graph-rest-1.0). This object is configured in the **referencedObjects** property of [attributeDefinition](https://learn.microsoft.com/en-us/graph/api/resources/synchronization-attributedefinition?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| referencedObjectName | String | Name of the referenced object. Must match one of the objects in the [directory definition](https://learn.microsoft.com/en-us/graph/api/resources/synchronization-directorydefinition?view=graph-rest-1.0). |
| referencedProperty | String | **Currently not supported**. Name of the property in the referenced object, the value for which is used as the reference. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "referencedObjectName": "String",
  "referencedProperty": "String"
}
```
