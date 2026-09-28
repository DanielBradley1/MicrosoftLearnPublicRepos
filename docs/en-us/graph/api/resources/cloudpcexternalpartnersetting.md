<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/cloudpcexternalpartnersetting?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-10-09 -->

# cloudPcExternalPartnerSetting resource type \(deprecated\)

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents an external partner setting on Cloud PC.

Caution

The external partner setting API is deprecated and will stop returning data on **March 31, 2026**. Please use the new [external partner APIs](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcexternalpartner?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/virtualendpoint-list-externalpartnersettings?view=graph-rest-beta) | [cloudPcExternalPartnerSetting](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcexternalpartnersetting?view=graph-rest-beta) collection | Get a list of the [cloudPcExternalPartnerSetting](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcexternalpartnersetting?view=graph-rest-beta) objects and their properties. |
| [Create](https://learn.microsoft.com/en-us/graph/api/virtualendpoint-post-externalpartnersettings?view=graph-rest-beta) | [cloudPcExternalPartnerSetting](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcexternalpartnersetting?view=graph-rest-beta) | Create a new [cloudPcExternalPartnerSetting](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcexternalpartnersetting?view=graph-rest-beta) object. |
| [Get](https://learn.microsoft.com/en-us/graph/api/cloudpcexternalpartnersetting-get?view=graph-rest-beta) | [cloudPcExternalPartnerSetting](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcexternalpartnersetting?view=graph-rest-beta) | Read the properties and relationships of a [cloudPcExternalPartnerSetting](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcexternalpartnersetting?view=graph-rest-beta) object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/cloudpcexternalpartnersetting-update?view=graph-rest-beta) | [cloudPcExternalPartnerSetting](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcexternalpartnersetting?view=graph-rest-beta) | Update the properties of a [cloudPcExternalPartnerSetting](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcexternalpartnersetting?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| enableConnection | Boolean | Enable or disable the connection to an external partner. If `true`, an external partner API will accept incoming calls from external partners. Required. Supports `$filter` \(`eq`\). |
| id | String | The unique identifier for the Cloud PC external partner setting. Read-only. |
| lastSyncDateTime | DateTimeOffset | Last data sync time for this external partner. The Timestamp type represents the date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 looks like this: '2014-01-01T00:00:00Z'. |
| partnerId | String | The external partner ID. |
| status | [cloudPcExternalPartnerStatus](#cloudpcexternalpartnerstatus-values) | The status of the connection to the external partner. The possible values are: `notAvailable`, `available`, `healthy`, `unhealthy`, `unknownFutureValue`. |
| statusDetails | String | Status details message. |

### cloudPcExternalPartnerStatus values

| Member | Description |
| :--- | :--- |
| notAvailable | The connection hasn't been established or the customer disabled the connection. |
| available | The connection has been enabled, but no heartbeat received yet. |
| healthy | The connection is enabled and heartbeat is being received. |
| unhealthy | The connection is enabled and heartbeat isn't being received. |
| unknownFutureValue | Evolvable enumeration sentinel value. Don't use. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.cloudPcExternalPartnerSetting",
  "enableConnection": "Boolean",  
  "id": "String (identifier)",
  "lastSyncDateTime": "String (timestamp)",
  "partnerId": "String",
  "status": "String",
  "statusDetails": "String"
}
```
