<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/synchronization-objectdefinitionmetadataentry?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-07-03 -->

# objectDefinitionMetadataEntry resource type

Namespace: microsoft.graph

Metadata for the given object. This object is configured in the **metadata** property of [objectDefinition](https://learn.microsoft.com/en-us/graph/api/resources/synchronization-objectdefinition?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| key | objectDefinitionMetadata | The possible values are: `PropertyNameAccountEnabled`, `PropertyNameSoftDeleted`, `IsSoftDeletionSupported`, `IsSynchronizeAllSupported`, `ConnectorDataStorageRequired`, `Extensions`, `LinkTypeName`. |
| value | String | Value of the metadata property. |

### Supported key-value pairs

| Key | Value |
| :--- | :--- |
| PropertyNameAccountEnabled | Indicates that the object is enabled. |
| PropertyNameSoftDeleted | Indicates that the object is soft-deleted. |
| IsSoftDeletionSupported | Indicates whether the object supports soft deletion. |
| IsSynchronizeAllSupported | Indicates whether the object supports `SyncAll`. |
| ConnectorDataStorageRequired | Indicates whether this object requires mapping storage. The service stores mapping for properties of types that will be mapped, like User and Group. |
| Extensions | A JSON containing a list of attributes and values that extends the base object that this object inherits from. |
| BaseObjectName | If this object inherits another object, this is the name of the parent base object. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.objectDefinitionMetadataEntry",
  "key": "String",
  "value": "String"
}
```
