<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/agreementacceptance?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-22 -->

# agreementAcceptance resource type

Namespace: microsoft.graph

Represents the current status of a user's response to a company's customizable terms of use agreement powered by Microsoft Entra ID Governance.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List agreement acceptances for a user](https://learn.microsoft.com/en-us/graph/api/user-list-agreementacceptances?view=graph-rest-1.0) | [agreementAcceptance](https://learn.microsoft.com/en-us/graph/api/resources/agreementacceptance?view=graph-rest-1.0) | Retrieve a user's agreementAcceptance objects. |
| [List acceptances](https://learn.microsoft.com/en-us/graph/api/agreement-list-acceptances?view=graph-rest-1.0) | [agreementAcceptance](https://learn.microsoft.com/en-us/graph/api/resources/agreementacceptance?view=graph-rest-1.0) | Retrieve acceptance for an agreement. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| agreementFileId | String | The identifier of the agreement file accepted by the user. |
| agreementId | String | The identifier of the agreement. |
| deviceDisplayName | String | The display name of the device used for accepting the agreement. |
| deviceId | String | The unique identifier of the device used for accepting the agreement. Supports `$filter` \(`eq`\) and `eq` for `null` values. |
| deviceOSType | String | The operating system used to accept the agreement. |
| deviceOSVersion | String | The operating system version of the device used to accept the agreement. |
| expirationDateTime | DateTimeOffset | The expiration date time of the acceptance. The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. Supports `$filter` \(`eq`, `ge`, `le`\) and `eq` for `null` values. |
| id | String | The identifier of the agreement acceptance. Read-only. Supports `$filter` \(`eq`\). |
| recordedDateTime | DateTimeOffset | The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |
| state | string | The state of the agreement acceptance. The possible values are: `accepted`, `declined`. Supports `$filter` \(`eq`\). |
| userDisplayName | String | Display name of the user when the acceptance was recorded. |
| userEmail | String | Email of the user when the acceptance was recorded. |
| userId | String | The identifier of the user who accepted the agreement. Supports `$filter` \(`eq`\). |
| userPrincipalName | String | UPN of the user when the acceptance was recorded. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
      "@odata.type": "microsoft.graph.agreementAcceptance",
      "agreementFileId": "String",
      "agreementId": "String",
      "deviceDisplayName": "String",
      "deviceId": "String",
      "deviceOSType": "String",
      "deviceOSVersion": "String",
      "expirationDateTime": "String",
      "id": "String (identifier)",
      "recordedDateTime": "String (timestamp)",
      "state": "String",
      "userDisplayName": "String",
      "userEmail": "String",
      "userId": "String",
      "userPrincipalName": "String",
}
```
