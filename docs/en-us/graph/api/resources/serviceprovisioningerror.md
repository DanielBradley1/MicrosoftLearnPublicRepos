<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/serviceprovisioningerror?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-04-04 -->

# serviceProvisioningError resource type

Namespace: microsoft.graph

An abstract base type that represents information published by a federated service that describes a nontransient, service specific error for the [user](https://learn.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-1.0), [group](https://learn.microsoft.com/en-us/graph/api/resources/group?view=graph-rest-1.0), or [organizational contact](https://learn.microsoft.com/en-us/graph/api/resources/orgcontact?view=graph-rest-1.0) that requires an explicit administrator action to resolve.

Base type of [serviceProvisioningXmlError](https://learn.microsoft.com/en-us/graph/api/resources/serviceprovisioningxmlerror?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| createdDateTime | DateTimeOffset | The date and time at which the error occurred. |
| isResolved | Boolean | Indicates whether the error has been attended to. |
| serviceInstance | String | Qualified service instance \(for example, "SharePoint/Dublin"\) that published the service error information. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "createdDateTime": "2020-01-31T17:45:18.00",
  "isResolved": false,
  "serviceInstance": "exchange/NAMPRD09-001-01"
}
```
