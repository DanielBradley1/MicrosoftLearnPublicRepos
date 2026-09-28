<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/callrecords-calllogrow?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-12-10 -->

# callLogRow resource type

Namespace: microsoft.graph.callRecords

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the basic properties of the Public Switched Telephone Network \(PSTN\) call log, Direct Routing call log, and SMS log.

The base type for [microsoft.graph.callRecords.pstnCallLogRow](https://learn.microsoft.com/en-us/graph/api/resources/callrecords-pstncalllogrow?view=graph-rest-beta), [microsoft.graph.callRecords.directRoutingLogRow](https://learn.microsoft.com/en-us/graph/api/resources/callrecords-directroutinglogrow?view=graph-rest-beta), and [microsoft.graph.callRecords.smsLogRow](https://learn.microsoft.com/en-us/graph/api/resources/callrecords-smslogrow?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| administrativeUnitInfos | [microsoft.graph.callRecords.administrativeUnitInfo](https://learn.microsoft.com/en-us/graph/api/resources/callrecords-administrativeunitinfo?view=graph-rest-beta) collection | Collection of administrative units associated to a call. |
| id | String | Unique call identifier \(GUID\). |
| otherPartyCountryCode | String | Country/region code of the caller for an incoming call, or callee for an outgoing call. For details, see [ISO 3166-1 alpha-2](https://en.wikipedia.org/wiki/ISO_3166-1_alpha-2). |
| userDisplayName | String | Display name of the user. |
| userId | String | The unique identifier \(GUID\) of the user in Microsoft Entra ID. This and other user info is null/empty for bot call types \(`ucap_in`, `ucap_out`\). |
| userPrincipalName | String | The user principal name \(sign-in name\) in Microsoft Entra ID. It's usually the same as the user's SIP address and can be the same as the user's e-mail address. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.callRecords.callLogRow",
  "administrativeUnitInfos": [{"@odata.type": "microsoft.graph.callRecords.administrativeUnitInfo"}],
  "id": "String (identifier)",
  "otherPartyCountryCode": "String",
  "userDisplayName": "String",
  "userId": "String",
  "userPrincipalName": "String"
}
```
