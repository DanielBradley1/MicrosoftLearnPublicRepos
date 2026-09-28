<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/cloudpcexternalpartner?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-03-05 -->

# cloudPcExternalPartner resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents an external partner on Cloud PC.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/virtualendpoint-list-externalpartners?view=graph-rest-beta) | [cloudPcExternalPartner](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcexternalpartner?view=graph-rest-beta) collection | Get a list of the [cloudPcExternalPartner](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcexternalpartner?view=graph-rest-beta) objects and their properties. |
| [Create](https://learn.microsoft.com/en-us/graph/api/virtualendpoint-post-externalpartners?view=graph-rest-beta) | [cloudPcExternalPartner](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcexternalpartner?view=graph-rest-beta) | Create a new [cloudPcExternalPartner](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcexternalpartner?view=graph-rest-beta) object. |
| [Get](https://learn.microsoft.com/en-us/graph/api/cloudpcexternalpartner-get?view=graph-rest-beta) | [cloudPcExternalPartner](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcexternalpartner?view=graph-rest-beta) | Read the properties and relationships of a [cloudPcExternalPartner](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcexternalpartner?view=graph-rest-beta) object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/cloudpcexternalpartner-update?view=graph-rest-beta) | [cloudPcExternalPartner](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcexternalpartner?view=graph-rest-beta) | Update the properties of a [cloudPcExternalPartner](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcexternalpartner?view=graph-rest-beta) object. |
| [Configure agent](https://learn.microsoft.com/en-us/graph/api/cloudpcexternalpartner-configureagent?view=graph-rest-beta) | None | Configure the agent setting of a [cloudPcExternalPartner](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcexternalpartner?view=graph-rest-beta) object. |
| [Deploy agent](https://learn.microsoft.com/en-us/graph/api/cloudpcexternalpartner-deployagent?view=graph-rest-beta) | String | Trigger agent deployment for a set of Windows 365 Cloud PCs that provisioned on a [cloudPcExternalPartner](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcexternalpartner?view=graph-rest-beta) object. |
| [Retrieve deploy agent action results](https://learn.microsoft.com/en-us/graph/api/cloudpcexternalpartner-retrievedeployagentactionresults?view=graph-rest-beta) | [cloudPcExternalPartnerActionResult](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcexternalpartneractionresult?view=graph-rest-beta) collection | Retrieve the status of deployment actions on a [cloudPcExternalPartner](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcexternalpartner?view=graph-rest-beta) object. |
| [Retrieve action reports](https://learn.microsoft.com/en-us/graph/api/cloudpcexternalpartner-retrieveactionreports?view=graph-rest-beta) | [cloudPcExternalPartnerActionReport](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcexternalpartneractionreport?view=graph-rest-beta) collection | Retrieve action reports on a [cloudPcExternalPartner](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcexternalpartner?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| connectionStatus | [cloudPcExternalPartnerStatus](#cloudpcexternalpartnerstatus-values) | The status of external partner connection. Possible values are `notAvailable`, `available`, `healthy`, `unhealthy`, and `unknownFutureValue`. Default value is `available`. Read-only. |
| enableConnection | Boolean | Enable or disable the connection to an external partner. If `true`, an external partner API accepts incoming calls from external partners. Required. Supports `$filter` \(`eq`\). |
| id | String | The unique identifier for the Cloud PC external partner entity record. Automatically generated when created. Read-only. |
| lastSyncDateTime | DateTimeOffset | Last data sync time for this external partner. The timeStamp type represents date and time information in ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 looks like this: '2014-01-01T00:00:00Z'. |
| partnerId | String | The partner identifier used to identify the external partner. When the Cloud PC service is ready to integrate with a new external partner, it generates a GUID to represent this partner. The Cloud PC service provides this partner ID to the partner, which can then use it to call this Microsoft Graph API and external partner APIs. Read-only. |
| statusDetails | String | Status details message. Read-only. |
| agentSetting | [cloudPcExternalPartnerAgentSetting](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcexternalpartneragentsetting?view=graph-rest-beta) | The agent settings associated with the external partner. |

### cloudPcExternalPartnerStatus values

| Member | Description |
| :--- | :--- |
| notAvailable | The connection isn't established or the customer disabled the connection. |
| available | The connection is established, but no heartbeat received yet. |
| healthy | The connection is enabled and heartbeat is being received. |
| unhealthy | The connection is enabled and heartbeat isn't being received. |
| unknownFutureValue | Evolvable enumeration sentinel value. Don't use. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.cloudPcExternalPartner",
  "id": "String (identifier)",
  "partnerId": "String",
  "enableConnection": "Boolean",
  "lastSyncDateTime": "String (timestamp)",
  "connectionStatus": "String",
  "statusDetails": "String",
  "agentSetting": {
    "@odata.type": "microsoft.graph.cloudPcExternalPartnerAgentSetting"
  }
}
```
