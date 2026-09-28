<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/printservice?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-05-24 -->

# printService resource type

Namespace: microsoft.graph

Represents a Microsoft Entra tenant-specific description of a print service instance. Services exist for each component of the printing infrastructure \(discovery, notifications, registration, and IPP\) and have one or more endpoints.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/print-list-services?view=graph-rest-1.0) | [printService](https://learn.microsoft.com/en-us/graph/api/resources/printservice?view=graph-rest-1.0) collection | Get a list of Universal Print services. |
| [Get](https://learn.microsoft.com/en-us/graph/api/printservice-get?view=graph-rest-1.0) | [printService](https://learn.microsoft.com/en-us/graph/api/resources/printservice?view=graph-rest-1.0) | Read the properties and relationships of service object. |
| [List a service's endpoints](https://learn.microsoft.com/en-us/graph/api/printservice-list-endpoints?view=graph-rest-1.0) | [printServiceEndpoint](https://learn.microsoft.com/en-us/graph/api/resources/printserviceendpoint?view=graph-rest-1.0) collection | Get a list of endpoints that a service provides. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The identifier of the service. Read-only. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| endpoints | [printServiceEndpoint](https://learn.microsoft.com/en-us/graph/api/resources/printserviceendpoint?view=graph-rest-1.0) collection | Endpoints that can be used to access the service. Read-only. Nullable. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.printService",
  "id": "String (identifier)"
}
```
