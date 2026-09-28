<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/partner-security-partnersecurityalert?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-05-21 -->

# partnerSecurityAlert resource type

Namespace: microsoft.graph.partner.security

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a security alert or a vulnerability of a CSP partner's customer that the partner must be made aware of for further action.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/partner-security-partnersecurityalert-list-securityalerts?view=graph-rest-beta) | [microsoft.graph.partner.security.partnerSecurityAlert](https://learn.microsoft.com/en-us/graph/api/resources/partner-security-partnersecurityalert?view=graph-rest-beta) collection | Get a list of the [partnerSecurityAlert](https://learn.microsoft.com/en-us/graph/api/resources/partner-security-partnersecurityalert?view=graph-rest-beta) objects and their properties. |
| [Get](https://learn.microsoft.com/en-us/graph/api/partner-security-partnersecurityalert-get?view=graph-rest-beta) | [microsoft.graph.partner.security.partnerSecurityAlert](https://learn.microsoft.com/en-us/graph/api/resources/partner-security-partnersecurityalert?view=graph-rest-beta) | Read the properties and relationships of a [partnerSecurityAlert](https://learn.microsoft.com/en-us/graph/api/resources/partner-security-partnersecurityalert?view=graph-rest-beta) object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/partner-security-partnersecurityalert-update?view=graph-rest-beta) | [microsoft.graph.partner.security.partnerSecurityAlert](https://learn.microsoft.com/en-us/graph/api/resources/partner-security-partnersecurityalert?view=graph-rest-beta) | Update the properties of a [partnerSecurityAlert](https://learn.microsoft.com/en-us/graph/api/resources/partner-security-partnersecurityalert?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| activityLogs | [microsoft.graph.partner.security.activityLog](https://learn.microsoft.com/en-us/graph/api/resources/partner-security-activitylog?view=graph-rest-beta) collection | Represents the activity by a partner and includes details of state transitions, who performed them, and when they occurred. |
| additionalDetails | [microsoft.graph.partner.security.additionalDataDictionary](https://learn.microsoft.com/en-us/graph/api/resources/partner-security-additionaldatadictionary?view=graph-rest-beta) | A bag of name-value pairs that contain more details about an alert. |
| affectedResources | [microsoft.graph.partner.security.affectedResource](https://learn.microsoft.com/en-us/graph/api/resources/partner-security-affectedresource?view=graph-rest-beta) collection | Contains details of the resources affected by the security alert. |
| alertType | String | The type of vulnerability that impacts the customer due to this alert. For more information, see [Security alerts reference guide](https://learn.microsoft.com/en-us/partner-center/security/security-alerts-reference-guide). |
| catalogOfferId | String | The modern offer category ID of the subscription. |
| confidenceLevel | microsoft.graph.partner.security.securityAlertConfidence | Specifies the confidence in the alert. The possible values are: `low`, `medium`, `high`, `unknownFutureValue`. |
| customerTenantId | String | The impacted customer tenant associated with the alert. |
| description | String | The description for each alert. |
| detectedDateTime | DateTimeOffset | Time when the alert was detected or created. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |
| displayName | String | The display name of the alert. |
| firstObservedDateTime | DateTimeOffset | Time of the first activity associated with the alert. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |
| id | String | Unique identifier to represent the alert. Inherited from [microsoft.graph.entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). |
| isTest | Boolean | Indicates whether an alert is a test alert. |
| lastObservedDateTime | DateTimeOffset | Time of the latest activity associated with the alert. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |
| resolvedBy | String | The UPN of the partner user who resolved the alert. |
| resolvedOnDateTime | DateTimeOffset | Time when the alert was resolved. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |
| resolvedReason | microsoft.graph.partner.security.securityAlertResolvedReason | The reason provided by the partner for addressing the alert. The possible values are: `legitimate`, `ignore`, `fraud`, `unknownFutureValue`. |
| severity | microsoft.graph.partner.security.securityAlertSeverity | Indicates the possible impact on assets. The higher the severity the bigger the impact. Typically higher severity items require the most immediate attention. The possible values are: `informational`, `high`, `medium`, `low`, `unknownFutureValue`. |
| status | microsoft.graph.partner.security.securityAlertStatus | The status of the alert. The possible values are: `active`, `resolved`, `investigating`, `unknownFutureValue`. |
| subscriptionId | String | The subscription associated with the alert for the customer. |
| valueAddedResellerTenantId | String | The value-added reseller tenant associated with the partner tenant and customer tenant. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.partner.security.partnerSecurityAlert",
  "activityLogs": [{"@odata.type": "microsoft.graph.partner.security.activityLog"}],
  "additionalDetails": {"@odata.type": "microsoft.graph.partner.security.additionalDataDictionary"},
  "affectedResources": [{"@odata.type": "microsoft.graph.partner.security.affectedResource"}],
  "alertType": "String",
  "catalogOfferId": "String",
  "confidenceLevel": "String",
  "customerTenantId": "String",
  "description": "String",
  "detectedDateTime": "String (timestamp)",
  "displayName": "String",
  "firstObservedDateTime": "String (timestamp)",
  "id": "String (identifier)",
  "isTest": "Boolean",
  "lastObservedDateTime": "String (timestamp)",
  "resolvedBy": "String",
  "resolvedOnDateTime": "String (timestamp)",
  "resolvedReason": "String",
  "severity": "String",
  "status": "String",
  "subscriptionId": "String",
  "valueAddedResellerTenantId": "String"
}
```
