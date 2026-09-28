<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-datadiscoveryreport?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-11-19 -->

# dataDiscoveryReport resource type

Namespace: microsoft.graph.security

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the resources available for generating cloud app discovery report.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List uploaded streams](https://learn.microsoft.com/en-us/graph/api/security-datadiscoveryreport-list-uploadedstreams?view=graph-rest-beta) | [microsoft.graph.security.cloudAppDiscoveryReport](https://learn.microsoft.com/en-us/graph/api/resources/security-cloudappdiscoveryreport?view=graph-rest-beta) collection | Get visibility into all the manually uploaded streams from your firewalls and proxies. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The stream ID. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| uploadedStreams | [microsoft.graph.security.cloudAppDiscoveryReport](https://learn.microsoft.com/en-us/graph/api/resources/security-cloudappdiscoveryreport?view=graph-rest-beta) collection | A collection of streams available for generating cloud discovery report. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.dataDiscoveryReport",
  "id": "String (identifier)"
}
```
