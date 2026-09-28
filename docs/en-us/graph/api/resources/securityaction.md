<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/securityaction?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-22 -->

# securityAction resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Take immediate action to defend against threats using the Microsoft Graph Security securityAction entity. When a security analyst discovers a new indicator, such as a malicious file, URL, domain, or IP address, protection can be instantly enabled in your Microsoft security solutions. Invoke an action for a specific provider, see all actions taken, and cancel an action if needed. Try security actions with [Windows Defender for Endpoint](https://learn.microsoft.com/en-us/windows/security/threat-protection/windows-defender-atp/windows-defender-advanced-threat-protection) to block malicious activity on your Windows endpoints using properties seen in alerts or identified during investigations.

> **Note:** Currently security actions only support application permissions.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [Get security action](https://learn.microsoft.com/en-us/graph/api/securityaction-get?view=graph-rest-beta) | [securityAction](https://learn.microsoft.com/en-us/graph/api/resources/securityaction?view=graph-rest-beta) | Read properties and relationships of securityAction object. |
| [Create security action](https://learn.microsoft.com/en-us/graph/api/securityactions-post?view=graph-rest-beta) | [securityAction](https://learn.microsoft.com/en-us/graph/api/resources/securityaction?view=graph-rest-beta) | Create a new securityAction by posting to the securityActions collection. |
| [List security actions](https://learn.microsoft.com/en-us/graph/api/securityactions-list?view=graph-rest-beta) | [securityAction](https://learn.microsoft.com/en-us/graph/api/resources/securityaction?view=graph-rest-beta) collection | Get a securityAction object collection. |
| [Cancel security action](https://learn.microsoft.com/en-us/graph/api/securityaction-cancelsecurityaction?view=graph-rest-beta) | None | Cancel a security operation. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| actionReason | String | Reason for invoking this action. |
| appId | String | The Application ID of the calling application that submitted \(POST\) the action. The appId should be extracted from the auth token and not entered manually by the calling application. |
| azureTenantId | String | Azure tenant ID of the entity to determine which tenant the entity belongs to \(multi-tenancy support\). The azureTenantId should be extracted from the auth token and not entered manually by the calling application. |
| clientContext | String | Unique client context string. Can have a maximum of 256 characters. |
| completedDateTime | DateTimeOffset | Timestamp when the action was completed. The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |
| createdDateTime | DateTimeOffset | Timestamp when the action is created. The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |
| errorInfo | [resultInfo](https://learn.microsoft.com/en-us/graph/api/resources/resultinfo?view=graph-rest-beta) | Error info when the action fails. |
| id | String | Created by the system when the action is ingested. Generated GUID/unique identifier. Read-only. |
| lastActionDateTime | DateTimeOffset | Timestamp when this action was last updated. The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |
| name | String | Action name. |
| parameters | [keyValuePair](https://learn.microsoft.com/en-us/graph/api/resources/keyvaluepair?view=graph-rest-beta) collection | Collection of parameters \(key-value pairs\) necessary to invoke the action, for example, URL or fileHash to block.\). **Required**. |
| states | [securityActionState](https://learn.microsoft.com/en-us/graph/api/resources/securityactionstate?view=graph-rest-beta) collection | Collection of securityActionState to keep the history of an action. |
| status | string | Status of the action. The possible values are: `NotStarted`, `Running`, `Completed`, `Failed`. |
| user | String | The user principal name of the signed-in user that submitted \(POST\) the action. The user should be extracted from the auth token and not entered manually by the calling application. |
| vendorInformation | [securityVendorInformation](https://learn.microsoft.com/en-us/graph/api/resources/securityvendorinformation?view=graph-rest-beta) | Complex Type containing details about the Security product/service vendor, provider, and sub-provider \(for example, vendor=Microsoft; provider=Windows Defender ATP; sub-provider=AppLocker\). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "actionReason": "String",
  "appId": "String",
  "azureTenantId": "String",
  "clientContext": "String",
  "completedDateTime": "String (timestamp)",
  "createdDateTime": "String (timestamp)",
  "errorInfo": {"@odata.type": "microsoft.graph.resultInfo"},
  "id": "String (identifier)",
  "lastActionDateTime": "String (timestamp)",
  "name": "String",
  "parameters": [{"@odata.type": "microsoft.graph.keyValuePair"}],
  "states": [{"@odata.type": "microsoft.graph.securityActionState"}],
  "status": "string",
  "user": "String",
  "vendorInformation": {"@odata.type": "microsoft.graph.securityVendorInformation"}
}
```
