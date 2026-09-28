<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/devicemanagement-rulecondition?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-09-10 -->

# ruleCondition resource type

Namespace: microsoft.graph.deviceManagement

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the rule conditions for an [alert rule](https://learn.microsoft.com/en-us/graph/api/resources/devicemanagement-alertrule?view=graph-rest-beta).

Note

This API is part of the [alert monitoring API set](https://learn.microsoft.com/en-us/graph/api/resources/devicemanagement-monitoring?view=graph-rest-beta&preserve-view=true) which currently supports only [Windows 365](https://learn.microsoft.com/en-us/windows-365/overview) and Cloud PC scenarios. The API set allows admins to set up rules to alert issues with provisioning Cloud PCs, uploading Cloud PC images, and checking Azure network connections.

Have a different scenario that can use additional programmatic alert support on the Microsoft Endpoint Manager admin center? [Suggest the feature or vote for existing feature requests](https://developer.microsoft.com/en-us/graph/support).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| aggregation | [microsoft.graph.deviceManagement.aggregationType](#aggregationtype-values) | The built-in aggregation method for the rule condition. The possible values are: `count`, `percentage`, `affectedCloudPcCount`, `affectedCloudPcPercentage`, `unknownFutureValue`. |
| conditionCategory | [microsoft.graph.deviceManagement.conditionCategory](#conditioncategory-values) | The property that the rule condition monitors. The possible values are: `provisionFailures`, `imageUploadFailures`, `azureNetworkConnectionCheckFailures`, `cloudPcInGracePeriod`, `frontlineInsufficientLicenses`, `cloudPcConnectionErrors`, `cloudPcHostHealthCheckFailures`, `cloudPcZoneOutage`, `unknownFutureValue`, `frontlineBufferUsageDuration`, `frontlineBufferUsageThreshold`, `cloudPcUserSettingsPersistenceUsageThreshold`, `cloudPcDeprovisionedThreshold`, `cloudPcReserveDeprovisionFailedThreshold`. Use the `Prefer: include-unknown-enum-members` request header to get the following values from this [evolvable enum](https://learn.microsoft.com/en-us/graph/best-practices-concept#handling-future-members-in-evolvable-enumerations): `frontlineBufferUsageDuration`, `frontlineBufferUsageThreshold`, `cloudPcUserSettingsPersistenceUsageThreshold`, `cloudPcDeprovisionedThreshold`, `cloudPcReserveDeprovisionFailedThreshold`. |
| operator | [microsoft.graph.deviceManagement.operatorType](#operatortype-values) | The built-in operator for the rule condition. The possible values are: `greaterOrEqual`, `equal`, `greater`, `less`, `lessOrEqual`, `notEqual`, `unknownFutureValue`. |
| relationshipType | [microsoft.graph.deviceManagement.relationshipType](#relationshiptype-values) | The relationship type. The possible values are: `and`, `or`. |
| thresholdValue | String | The threshold value of the alert condition. The threshold value can be a number in string form or string like "WestUS". |

### relationshipType values

| Member | Description |
| :--- | :--- |
| and | The rule conditions have an "and" relationship |
| or | The rule conditions have an "or" relationship. |
| unknownFutureValue | Evolvable enumeration sentinel value. Don't use. |

### conditionCategory values

| Member | Description |
| :--- | :--- |
| provisionFailures | The rule condition targets provision failures. |
| imageUploadFailures | The rule condition targets image upload failures. |
| azureNetworkConnectionCheckFailures | The rule condition targets Azure network connection check failures. |
| cloudPcInGracePeriod | The rule condition targets Cloud PCs entering grace period state. |
| frontlineInsufficientLicenses | The rule condition targets Frontline insufficient licenses. |
| cloudPcConnectionErrors | The rule condition targets Cloud PC connection errors. |
| cloudPcHostHealthCheckFailures | The rule condition targets Cloud PC host health check failures. |
| cloudPcZoneOutage | The rule condition targets Cloud PC zone outage. |
| unknownFutureValue | Evolvable enumeration sentinel value. Don't use. |
| frontlineBufferUsageDuration | The alert rule condition targets Frontline buffer usage exceeds time duration. |
| frontlineBufferUsageThreshold | The alert rule condition targets Frontline buffer usage exceeds limiting frequency. |
| cloudPcUserSettingsPersistenceUsageThreshold | Indicates that the alert rule condition targets user experience sync storage that exceeds the usage threshold. |
| cloudPcDeprovisionedThreshold | Indicates that the alert rule condition targets the count of Windows 365 Cloud PCs that entered deprovision. |
| cloudPcReserveDeprovisionFailedThreshold | Indicates that the alert rule condition targets the count of Windows 365 Reserve Cloud PCs that entered a failed deprovisioning process. |

### aggregationType values

| Member | Description |
| :--- | :--- |
| count | The number of items that match the rule conditions. |
| percentage | The percentage of the items that match the rule conditions. |
| affectedCloudPcCount | The total number of Cloud PCs that meet the rule conditions. |
| affectedCloudPcPercentage | The percentage of Cloud PCs that meet the rule conditions. |
| unknownFutureValue | Evolvable enumeration sentinel value. Don't use. |
| durationInMinutes | The time range during which Cloud PCs that meet the alert rule conditions are affected. |

### operatorType values

| Member | Description |
| :--- | :--- |
| greaterOrEqual | The operator is greater than or equal to the threshold target. |
| equal | The operator is equal to the threshold target. |
| greater | The operator is greater than the threshold target. |
| less | The operator is less than the threshold target. |
| lessOrEqual | The operator is less than or equal to the threshold target. |
| notEqual | The operator isn't equal to the threshold target. |
| unknownFutureValue | Evolvable enumeration sentinel value. Don't use. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.deviceManagement.ruleCondition",
  "relationshipType": "String",
  "conditionCategory": "String",
  "aggregation": "String",
  "operator": "String",
  "thresholdValue": "String"
}
```
