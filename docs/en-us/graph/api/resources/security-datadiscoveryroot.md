<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-datadiscoveryroot?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-11-19 -->

# dataDiscoveryRoot resource type

Namespace: microsoft.graph.security

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents data discovery entities such as IP addresses, devices, and users who access a cloud app.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta).

## Methods

None.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The unique ID of the discovery stream. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| cloudAppDiscovery | [microsoft.graph.security.dataDiscoveryReport](https://learn.microsoft.com/en-us/graph/api/resources/security-datadiscoveryreport?view=graph-rest-beta) | The available entities are IP addresses, devices, and users who access a cloud app. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.dataDiscoveryRoot",
  "id": "String (identifier)"
}
```
