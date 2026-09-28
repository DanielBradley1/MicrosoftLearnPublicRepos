<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/onpremisesdirectorysynchronization?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-10-03 -->

# onPremisesDirectorySynchronization resource type

Namespace: microsoft.graph

A container for [on-premises directory synchronization](https://learn.microsoft.com/en-us/graph/api/resources/onpremisesdirectorysynchronization?view=graph-rest-1.0) functionalities that are available for the organization. Only the read and update operations are supported on this resource; create and delete aren't supported.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Get](https://learn.microsoft.com/en-us/graph/api/onpremisesdirectorysynchronization-get?view=graph-rest-1.0) | [onPremisesDirectorySynchronization](https://learn.microsoft.com/en-us/graph/api/resources/onpremisesdirectorysynchronization?view=graph-rest-1.0) | Read the properties and relationships of an [onPremisesDirectorySynchronization](https://learn.microsoft.com/en-us/graph/api/resources/onpremisesdirectorysynchronization?view=graph-rest-1.0) object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/onpremisesdirectorysynchronization-update?view=graph-rest-1.0) | [onPremisesDirectorySynchronization](https://learn.microsoft.com/en-us/graph/api/resources/onpremisesdirectorysynchronization?view=graph-rest-1.0) | Update the properties of an [onPremisesDirectorySynchronization](https://learn.microsoft.com/en-us/graph/api/resources/onpremisesdirectorysynchronization?view=graph-rest-1.0) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| configuration | [onPremisesDirectorySynchronizationConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/onpremisesdirectorysynchronizationconfiguration?view=graph-rest-1.0) | Consists of configurations that can be fine-tuned and impact the on-premises directory synchronization process for a tenant. Nullable. |
| features | [onPremisesDirectorySynchronizationFeature](https://learn.microsoft.com/en-us/graph/api/resources/onpremisesdirectorysynchronizationfeature?view=graph-rest-1.0) | Consists of directory synchronization features that can be enabled or disabled. Not nullable. |
| id | String | The unique Microsoft Entra tenant ID. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.onPremisesDirectorySynchronization",
  "id": "String (identifier)",
  "configuration": {
    "@odata.type": "microsoft.graph.onPremisesDirectorySynchronizationConfiguration"
  },
  "features": {
    "@odata.type": "microsoft.graph.onPremisesDirectorySynchronizationFeature"
  }
}
```
