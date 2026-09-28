<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-cloudlogonsessionevidence?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-06-01 -->

# cloudLogonSessionEvidence resource type

Namespace: microsoft.graph.security

Represents a cloud sign-in session created by an account.

Inherits from [alertEvidence](https://learn.microsoft.com/en-us/graph/api/resources/security-alertevidence?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| sessionId | String | The session ID for the account reported in the alert. |
| account | [microsoft.graph.security.userEvidence](https://learn.microsoft.com/en-us/graph/api/resources/security-userevidence?view=graph-rest-1.0) | The account associated with the sign-in session. |
| protocol | String | The authentication protocol that is used in this session, if known. |
| deviceName | String | The friendly name of the device, if known. |
| operatingSystem | String | The operating system that the device is running, if known. |
| browser | String | The browser that is used for the sign-in, if known. |
| userAgent | String | The user agent that is used for the sign-in, if known. |
| startUtcDateTime | DateTime | The session start time, if known. |
| previousLogonDateTime | DateTime | The previous sign-in time for this account, if known. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.cloudLogonSessionEvidence",
  "createdDateTime": "String (timestamp)",
  "verdict": "String",
  "remediationStatus": "String",
  "remediationStatusDetails": "String",
  "roles": [
    "String"
  ],
  "tags": [
    "String"
  ],
  "url": "String",
  "SessionId": "String",
  "Account": "microsoft.graph.security.userEvidence",
  "Protocol": "String",
  "DeviceName": "String",
  "OperatingSystem": "String",
  "Browser": "String",
  "UserAgent": "String",
  "StartUtcDateTime": "String (timestamp)",
  "PreviousLogonDateTime": "String (timestamp)"
}
```
