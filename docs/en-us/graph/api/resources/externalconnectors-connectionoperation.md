<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/externalconnectors-connectionoperation?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# connectionOperation resource type

Namespace: microsoft.graph.externalConnectors

Describes status of an asynchronous request to create a Microsoft Search connection [schema](https://learn.microsoft.com/en-us/graph/api/resources/externalconnectors-schema?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Get operation](https://learn.microsoft.com/en-us/graph/api/externalconnectors-connectionoperation-get?view=graph-rest-1.0) | [connectionOperation](https://learn.microsoft.com/en-us/graph/api/resources/externalconnectors-connectionoperation?view=graph-rest-1.0) | Read the properties and relationships of a [connectionOperation](https://learn.microsoft.com/en-us/graph/api/resources/externalconnectors-connectionoperation?view=graph-rest-1.0) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| error | publicError | If `status` is `failed`, provides more information about the error that caused the failure. |
| id | String | Unique identifier for the connectionOperation. Read-only. |
| status | microsoft.graph.externalConnectors.connectionOperationStatus | Indicates the status of the asynchronous operation. The possible values are: `unspecified`, `inprogress`, `completed`, `failed`, `unknownFutureValue`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "id": "String (identifier)",
  "status": "String"
}
```
