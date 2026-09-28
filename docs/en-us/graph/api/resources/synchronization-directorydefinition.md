<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/synchronization-directorydefinition?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-05-24 -->

# directoryDefinition resource type

Namespace: microsoft.graph

Provides the synchronization engine information about a directory and its objects. This resource tells the synchronization engine, for example, that the directory has objects named **user** and **group**, which attributes are supported for those objects, and the types for those attributes. In order for the object and attribute to participate in [synchronization rules](https://learn.microsoft.com/en-us/graph/api/resources/synchronization-synchronizationrule?view=graph-rest-1.0) and [object mappings](https://learn.microsoft.com/en-us/graph/api/resources/synchronization-objectmapping?view=graph-rest-1.0), they must be defined as part of the directory definition.

In general, the default [synchronization schema](https://learn.microsoft.com/en-us/graph/api/resources/synchronization-synchronizationschema?view=graph-rest-1.0) provided as part of the [synchronization template](https://learn.microsoft.com/en-us/graph/api/resources/synchronization-synchronizationtemplate?view=graph-rest-1.0) defines the most commonly used objects and attributes for that directory. However, if the directory supports the addition of custom attributes, you might want to expand the default definition with your own custom objects or attributes. For more information, see the following articles.

- [Configure synchronization with custom attributes](https://learn.microsoft.com/en-us/graph/synchronization-configure-with-custom-target-attributes)
- [Configure synchronization with directory extension attributes](https://learn.microsoft.com/en-us/graph/synchronization-configure-with-directory-extension-attributes).

Directory definitions are updated as part of the [synchronization schema](https://learn.microsoft.com/en-us/graph/api/resources/synchronization-synchronizationschema?view=graph-rest-1.0).

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0).

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [Discover](https://learn.microsoft.com/en-us/graph/api/synchronization-directorydefinition-discover?view=graph-rest-1.0) | [directoryDefinition](https://learn.microsoft.com/en-us/graph/api/resources/synchronization-directorydefinition?view=graph-rest-1.0) | Discover the schema and supported properties of the directory. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Directory identifier. Not nullable. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). |
| name | String | Name of the directory. Must be unique within the [synchronization schema](https://learn.microsoft.com/en-us/graph/api/resources/synchronization-synchronizationschema?view=graph-rest-1.0). Not nullable. |
| objects | [objectDefinition](https://learn.microsoft.com/en-us/graph/api/resources/synchronization-objectdefinition?view=graph-rest-1.0) collection | Collection of objects supported by the directory. |
| readOnly | Boolean | Whether this object is read-only. |
| version | String | Read only value that indicates version discovered. `null` if discovery hasn't yet occurred. |
| discoveryDateTime | DateTimeOffset | Represents the discovery date and time using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |
| discoverabilities | directoryDefinitionDiscoverabilities | Read-only value indicating what type of discovery the app supports. The possible values are: `None`, `AttributeNames`, `AttributeDataTypes`, `AttributeReadOnly`, `ReferenceAttributes`, `UnknownFutureValue`. This is a multi-valued object. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "discoverabilities": "String",
  "discoveryDateTime": "DateTimeOffset",
  "id": "String",
  "name": "String",
  "objects": [
    {
      "@odata.type": "microsoft.graph.objectDefinition"
    }
  ],
  "version": "String"
}
```
