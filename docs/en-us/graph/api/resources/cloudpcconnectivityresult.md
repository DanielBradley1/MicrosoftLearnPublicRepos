<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/cloudpcconnectivityresult?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-03-21 -->

# cloudPcConnectivityResult resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the details of the Cloud PC connectivity status, including whether the Cloud PC is available, and if not, the failed health check items.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| failedHealthCheckItems | [cloudPcHealthCheckItem](https://learn.microsoft.com/en-us/graph/api/resources/cloudpchealthcheckitem?view=graph-rest-beta) collection | A list of failed health check items. If the status property is `available`, this property is empty. |
| status | [cloudPcConnectivityStatus](#cloudpcconnectivitystatus-values) | Connectivity status of the Cloud PC. The possible values are: `unknown`, `available`, `availableWithWarning`, `unavailable`, `unknownFutureValue`, `underServiceMaintenance`, `inUse`. Use the `Prefer: include-unknown-enum-members` request header to get the following values in this [evolvable enum](https://learn.microsoft.com/en-us/graph/best-practices-concept#handling-future-members-in-evolvable-enumerations): `underServiceMaintenance`, `inUse`. |
| updatedDateTime \(deprecated\) | string | Datetime when the status was updated. This property is deprecated and will no longer be supported effective August 31, 2024. Use lastModifiedDateTime instead. Read-Only. |
| lastModifiedDateTime | string | The last modified time for connectivity status of the Cloud PC. The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 would look like this: `2014-01-01T00:00:00Z`. |

### cloudPcConnectivityStatus values

| Member | Description |
| :--- | :--- |
| unknown | Default. Indicates that the Cloud PC connectivity status is unknown. |
| available | Indicates that the Cloud PC is able to be connected. |
| availableWithWarning | Indicates that the Cloud PC is able to be connected but warnings exist. |
| unavailable | Indicates that the Cloud PC is unable to be connected. |
| unknownFutureValue | Evolvable enumeration sentinel value. Don't use. |
| underServiceMaintenance | Indicates that the Cloud PC is temporarily unavailable for service-initiated maintenance. |
| inUse | Indicates that the Cloud PC is currently in use by a user. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.cloudPcConnectivityResult",
  "failedHealthCheckItems": [{"@odata.type": "microsoft.graph.cloudPcHealthCheckItem"}],
  "status": "String",
  "updatedDateTime": "String (timestamp)",
  "lastModifiedDateTime": "String (timestamp)"
}
```
