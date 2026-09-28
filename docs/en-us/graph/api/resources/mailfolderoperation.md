<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/mailfolderoperation?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-03-28 -->

# mailFolderOperation resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a long-running operation of a [mailFolder](https://learn.microsoft.com/en-us/graph/api/resources/mailfolder?view=graph-rest-beta) object.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/mailfolder-list-operations?view=graph-rest-beta) | [mailFolderOperation](https://learn.microsoft.com/en-us/graph/api/resources/mailfolderoperation?view=graph-rest-beta) collection | List the long-running folder operations of a [mailFolder](https://learn.microsoft.com/en-us/graph/api/resources/mailfolder?view=graph-rest-beta) object. |
| [Get](https://learn.microsoft.com/en-us/graph/api/mailfolderoperation-get?view=graph-rest-beta) | [mailFolderOperation](https://learn.microsoft.com/en-us/graph/api/resources/mailfolderoperation?view=graph-rest-beta) | Read the properties and relationships of a [mailFolderOperation](https://learn.microsoft.com/en-us/graph/api/resources/mailfolderoperation?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The unique identifier of the long-running operation. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). |
| resourceLocation | String | The location of the long-running operation. |
| status | mailFolderOperationStatus | The status of the long-running operation. The possible values are: `notStarted`, `running`, `succeeded`, `failed`, `unknownFutureValue`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.mailFolderOperation",
  "id": "String (identifier)",
  "resourceLocation": "String",
  "status": "String"
}
```
