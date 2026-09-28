<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/synchronization-synchronizationschema?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-11-04 -->

# synchronizationSchema resource type

Namespace: microsoft.graph

Defines what objects will be synchronized and how they are synchronized. The synchronization schema contains most of the setup information for a particular synchronization job. Typically, you customize some of the [attribute mappings](https://learn.microsoft.com/en-us/graph/api/resources/synchronization-attributemapping?view=graph-rest-1.0), or add a [scoping filter](https://learn.microsoft.com/en-us/graph/api/resources/synchronization-filter?view=graph-rest-1.0) to synchronize only objects that satisfy a certain condition.

The following sections describe the high-level components of the synchronization schema. For more information, see [Understand the Microsoft Entra schema](https://learn.microsoft.com/en-us/entra/identity/hybrid/cloud-sync/concept-attributes) and [Attribute mapping - Active Directory to Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/identity/hybrid/cloud-sync/how-to-attribute-mapping).

## Directory definitions

[Directory definitions](https://learn.microsoft.com/en-us/graph/api/resources/synchronization-directorydefinition?view=graph-rest-1.0) provide the synchronization engine information about directories and their objects. For example, the directory definition tells the synchronization engine that a Microsoft Entra directory has objects named **user** and **group**, which attributes are supported for those objects, and the types for those attributes. In order for a particular object and attribute to be used in synchronization rules/object mappings, they have to be defined as part of the directory definition.

## Synchronization rules

[Synchronization rules](https://learn.microsoft.com/en-us/graph/api/resources/synchronization-synchronizationrule?view=graph-rest-1.0) are the core of the synchronization setup. They define for the synchronization engine how the synchronization should be performed, including what objects should be synchronized, how objects from the source directory should be matched with objects in the target directory, and how attributes should be transformed when they're synchronized from the source to the target directory.

## Object mappings

[Object mappings](https://learn.microsoft.com/en-us/graph/api/resources/synchronization-objectmapping?view=graph-rest-1.0) are the main part of the synchronization rule. Each object mapping defines how a given object should be synchronized from the source to the target directory. In particular, the mapping defines how an object in the source directory should be matched with an object in the target directory, what \(if any\) scoping filters should be used to decide whether to provision an object, and how object attributes should be transformed when they're synchronized from the source to the target directory.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [Get](https://learn.microsoft.com/en-us/graph/api/synchronization-synchronizationschema-get?view=graph-rest-1.0) | [synchronizationSchema](https://learn.microsoft.com/en-us/graph/api/resources/synchronization-synchronizationschema?view=graph-rest-1.0) | Read properties and relationships of the **synchronizationSchema** object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/synchronization-synchronizationschema-update?view=graph-rest-1.0) | None | Update the synchronization schema. |
| [Reset](https://learn.microsoft.com/en-us/graph/api/synchronization-synchronizationschema-delete?view=graph-rest-1.0) | None | Delete the customized schema, resetting the schema to the default configuration. |
| [Get schema filter operators](https://learn.microsoft.com/en-us/graph/api/synchronization-synchronizationschema-filteroperators?view=graph-rest-1.0) | [filterOperatorSchema](https://learn.microsoft.com/en-us/graph/api/resources/synchronization-filteroperatorschema?view=graph-rest-1.0) collection | List all operators supported in the scoping filters. |
| [Get schema functions](https://learn.microsoft.com/en-us/graph/api/synchronization-synchronizationschema-functions?view=graph-rest-1.0) | [attributeMappingFunctionSchema](https://learn.microsoft.com/en-us/graph/api/resources/synchronization-attributemappingfunctionschema?view=graph-rest-1.0) collection | List all functions supported in the attribute mapping expressions. |
| [Parse attribute mapping expression](https://learn.microsoft.com/en-us/graph/api/synchronization-synchronizationschema-parseexpression?view=graph-rest-1.0) | [parseExpressionResponse](https://learn.microsoft.com/en-us/graph/api/resources/synchronization-parseexpressionresponse?view=graph-rest-1.0) | Parse a string expression into an [attributeMappingSource](https://learn.microsoft.com/en-us/graph/api/resources/synchronization-attributemappingsource?view=graph-rest-1.0) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Unique identifier for the schema. |
| synchronizationRules | [synchronizationRule](https://learn.microsoft.com/en-us/graph/api/resources/synchronization-synchronizationrule?view=graph-rest-1.0) collection | A collection of synchronization rules configured for the [synchronizationJob](https://learn.microsoft.com/en-us/graph/api/resources/synchronization-synchronizationjob?view=graph-rest-1.0) or [synchronizationTemplate](https://learn.microsoft.com/en-us/graph/api/resources/synchronization-synchronizationtemplate?view=graph-rest-1.0). |
| version | String | The version of the schema, updated automatically with every schema change. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| directories | [directoryDefinition](https://learn.microsoft.com/en-us/graph/api/resources/synchronization-directorydefinition?view=graph-rest-1.0) collection | Contains the collection of directories and all of their objects. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.synchronizationSchema",
  "id": "String (identifier)",
  "synchronizationRules": [
    {
      "@odata.type": "microsoft.graph.synchronizationRule"
    }
  ],
  "version": "String"
}
```
