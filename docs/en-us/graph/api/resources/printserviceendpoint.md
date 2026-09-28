<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/printserviceendpoint?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# printServiceEndpoint resource type

Namespace: microsoft.graph

Represents URI and identifying information for a print service instance.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Get endpoint](https://learn.microsoft.com/en-us/graph/api/printserviceendpoint-get?view=graph-rest-1.0) | [printServiceEndpoint](https://learn.microsoft.com/en-us/graph/api/resources/printserviceendpoint?view=graph-rest-1.0) | Read the properties and relationships of endpoint object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | A human-readable display name for the endpoint. |
| id | String | A unique name that identifies the service that the endpoint provides. The possible values are: `discovery` \(Discovery Service\), `notification` \(Notification Service\), `ipp` \(IPP Service\), and `registration` \(Registration Service\). Read-only. |
| uri | String | The URI that can be used to access the service. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.printServiceEndpoint",
  "id": "String (identifier)",
  "displayName": "String",
  "uri": "String"
}
```
