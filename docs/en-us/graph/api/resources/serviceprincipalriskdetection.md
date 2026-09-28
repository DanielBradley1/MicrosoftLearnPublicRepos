<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/serviceprincipalriskdetection?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-12-03 -->

# servicePrincipalRiskDetection resource type

Namespace: microsoft.graph

Represents information about detected at-risk service principals in a Microsoft Entra tenant. Microsoft Entra ID continually evaluates risks based on various signals and machine learning. This API provides programmatic access to all service principal risk detections in your Microsoft Entra environment.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0).

For more information about risk events, see [Microsoft Entra ID Protection](https://learn.microsoft.com/en-us/azure/active-directory/identity-protection/overview-identity-protection).

> **Note:** You must have a Microsoft Entra Workload ID Premium license to use the servicePrincipalRiskDetection API.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/identityprotectionroot-list-serviceprincipalriskdetections?view=graph-rest-1.0) | [servicePrincipalRiskDetection](https://learn.microsoft.com/en-us/graph/api/resources/serviceprincipalriskdetection?view=graph-rest-1.0) collection | List service principal risk detections and their properties. |
| [Get](https://learn.microsoft.com/en-us/graph/api/serviceprincipalriskdetection-get?view=graph-rest-1.0) | [servicePrincipalRiskDetection](https://learn.microsoft.com/en-us/graph/api/resources/serviceprincipalriskdetection?view=graph-rest-1.0) | Get a specific service principal risk detection and its properties. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| activity | [activityType](https://learn.microsoft.com/en-us/graph/api/resources/activitytype?view=graph-rest-1.0) | Indicates the activity type the detected risk is linked to. |
| activityDateTime | DateTimeOffset | Date and time when the risky activity occurred. The DateTimeOffset type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z` |
| additionalInfo | String | Additional information associated with the risk detection. This string value is represented as a JSON object with the quotations escaped. |
| appId | String | The unique identifier for the associated application. |
| correlationId | String | Correlation ID of the sign-in activity associated with the risk detection. This property is `null` if the risk detection is not associated with a sign-in activity. |
| detectedDateTime | DateTimeOffset | Date and time when the risk was detected. The DateTimeOffset type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |
| detectionTimingType | riskDetectionTimingType | Timing of the detected risk , whether real-time or offline. The possible values are: `notDefined`, `realtime`, `nearRealtime`, `offline`, `unknownFutureValue`. |
| id | String | Unique identifier of the risk detection. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). |
| ipAddress | String | Provides the IP address of the client from where the risk occurred. |
| keyIds | String collection | The unique identifier for the key credential associated with the risk detection. |
| lastUpdatedDateTime | DateTimeOffset | Date and time when the risk detection was last updated. |
| location | [signInLocation](https://learn.microsoft.com/en-us/graph/api/resources/signinlocation?view=graph-rest-1.0) | Location from where the sign-in was initiated. |
| requestId | String | Request identifier of the sign-in activity associated with the risk detection. This property is `null` if the risk detection is not associated with a sign-in activity. Supports `$filter` \(`eq`\). |
| riskDetail | [riskDetail](https://learn.microsoft.com/en-us/graph/api/resources/riskdetail?view=graph-rest-1.0) | Details of the detected risk.  <br>**Note:** Details for this property are only available for Workload Identities Premium customers. Events in tenants without this license will be returned `hidden`. |
| riskEventType | String | The type of risk event detected. The possible values are: `investigationsThreatIntelligence`, `generic`, `adminConfirmedServicePrincipalCompromised`, `suspiciousSignins`, `leakedCredentials`, `anomalousServicePrincipalActivity`, `maliciousApplication`, `suspiciousApplication`. |
| riskLevel | riskLevel | Level of the detected risk.  <br>**Note:** Details for this property are only available for Workload Identities Premium customers. Events in tenants without this license will be returned `hidden`. The possible values are: `low`, `medium`, `high`, `hidden`, `none`. |
| riskState | riskState | The state of a detected risky service principal or sign-in activity. The possible values are: `none`, `dismissed`, `atRisk`, `confirmedCompromised`. |
| servicePrincipalDisplayName | String | The display name for the service principal. |
| servicePrincipalId | String | The unique identifier for the service principal. Supports `$filter` \(`eq`\). |
| source | String | Source of the risk detection. For example, `identityProtection`. |
| tokenIssuerType | tokenIssuerType | Indicates the type of token issuer for the detected sign-in risk. The possible values are: `AzureAD`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.servicePrincipalRiskDetection",
  "id": "String (identifier)",
  "requestId": "String",
  "correlationId": "String",
  "riskEventType": "String",
  "riskState": "String",
  "riskLevel": "String",
  "riskDetail": "String",
  "source": "String",
  "detectionTimingType": "String",
  "activity": "String",
  "tokenIssuerType": "String",
  "ipAddress": "String",
  "location": {
    "@odata.type": "microsoft.graph.signInLocation"
  },
  "activityDateTime": "String (timestamp)",
  "detectedDateTime": "String (timestamp)",
  "lastUpdatedDateTime": "String (timestamp)",
  "servicePrincipalId": "String",
  "servicePrincipalDisplayName": "String",
  "appId": "String",
  "keyIds": [
    "String"
  ],
  "additionalInfo": "String"
}
```
