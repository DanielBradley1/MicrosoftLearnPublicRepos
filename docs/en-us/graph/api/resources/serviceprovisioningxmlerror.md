<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/serviceprovisioningxmlerror?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# serviceProvisioningXmlError resource type

Namespace: microsoft.graph

Represents information that is published by a federated service and describes a nontransient, service specific error that requires an explicit administrator action to resolve. These errors are reported as an xml string on the [user](https://learn.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-1.0), [group](https://learn.microsoft.com/en-us/graph/api/resources/group?view=graph-rest-1.0), or [organizational contact](https://learn.microsoft.com/en-us/graph/api/resources/orgcontact?view=graph-rest-1.0) entities.

Inherits from [serviceProvisioningError](https://learn.microsoft.com/en-us/graph/api/resources/serviceprovisioningerror?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| createdDateTime | DateTimeOffset | The date and time at which the error occurred. |
| errorDetail | String | Error Information published by the Federated Service as an xml string. |
| isResolved | Boolean | Indicates whether the error is resolved. |
| serviceInstance | String | Qualified service instance \(for example "SharePoint/Dublin"\) that published the service error information. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "createdDateTime": "2020-01-31T17:45:18.00",
  "errorDetail": "<a/>",
  "isResolved": false,
  "serviceInstance": "exchange/NAMPRD09-001-01"
}
```
