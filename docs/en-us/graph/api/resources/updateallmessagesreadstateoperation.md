<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/updateallmessagesreadstateoperation?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-03-28 -->

# updateAllMessagesReadStateOperation resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a long-running operation in a [mailFolder](https://learn.microsoft.com/en-us/graph/api/resources/mailfolder?view=graph-rest-beta) of type **updateAllMessagesReadState**.

Inherits from [mailFolderOperation](https://learn.microsoft.com/en-us/graph/api/resources/mailfolderoperation?view=graph-rest-beta).

## Methods

For the list of supported methods, see [mailFolderOperation](https://learn.microsoft.com/en-us/graph/api/resources/mailfolderoperation?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The unique identifier of the long-running operation. Inherited from [mailFolderOperation](https://learn.microsoft.com/en-us/graph/api/resources/mailfolderoperation?view=graph-rest-beta). |
| resourceLocation | String | The location of the long-running operation. Inherited from [mailFolderOperation](https://learn.microsoft.com/en-us/graph/api/resources/mailfolderoperation?view=graph-rest-beta). |
| status | mailFolderOperationStatus | The status of the long-running operation. The possible values are: `notStarted`, `running`, `succeeded`, `failed`, `unknownFutureValue`. Inherited from [mailFolderOperation](https://learn.microsoft.com/en-us/graph/api/resources/mailfolderoperation?view=graph-rest-beta). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.updateAllMessagesReadStateOperation",
  "id": "String (identifier)",
  "resourceLocation": "String",
  "status": "String"
}
```
