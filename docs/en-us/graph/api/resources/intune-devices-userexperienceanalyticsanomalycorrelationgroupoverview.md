<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsanomalycorrelationgroupoverview?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# userExperienceAnalyticsAnomalyCorrelationGroupOverview resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

The user experience analytics anomaly correlation group overview entity contains the information for each correlation group of an anomaly.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List userExperienceAnalyticsAnomalyCorrelationGroupOverviews](https://learn.microsoft.com/en-us/graph/api/intune-devices-userexperienceanalyticsanomalycorrelationgroupoverview-list?view=graph-rest-beta) | [userExperienceAnalyticsAnomalyCorrelationGroupOverview](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsanomalycorrelationgroupoverview?view=graph-rest-beta) collection | List properties and relationships of the [userExperienceAnalyticsAnomalyCorrelationGroupOverview](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsanomalycorrelationgroupoverview?view=graph-rest-beta) objects. |
| [Get userExperienceAnalyticsAnomalyCorrelationGroupOverview](https://learn.microsoft.com/en-us/graph/api/intune-devices-userexperienceanalyticsanomalycorrelationgroupoverview-get?view=graph-rest-beta) | [userExperienceAnalyticsAnomalyCorrelationGroupOverview](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsanomalycorrelationgroupoverview?view=graph-rest-beta) | Read properties and relationships of the [userExperienceAnalyticsAnomalyCorrelationGroupOverview](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsanomalycorrelationgroupoverview?view=graph-rest-beta) object. |
| [Create userExperienceAnalyticsAnomalyCorrelationGroupOverview](https://learn.microsoft.com/en-us/graph/api/api/intune-devices-userexperienceanalyticsanomalycorrelationgroupoverview-create.md?view=graph-rest-beta) | [userExperienceAnalyticsAnomalyCorrelationGroupOverview](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsanomalycorrelationgroupoverview?view=graph-rest-beta) | Create a new [userExperienceAnalyticsAnomalyCorrelationGroupOverview](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsanomalycorrelationgroupoverview?view=graph-rest-beta) object. |
| [Delete userExperienceAnalyticsAnomalyCorrelationGroupOverview](https://learn.microsoft.com/en-us/graph/api/api/intune-devices-userexperienceanalyticsanomalycorrelationgroupoverview-delete.md?view=graph-rest-beta) | None | Deletes a [userExperienceAnalyticsAnomalyCorrelationGroupOverview](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsanomalycorrelationgroupoverview?view=graph-rest-beta). |
| [Update userExperienceAnalyticsAnomalyCorrelationGroupOverview](https://learn.microsoft.com/en-us/graph/api/api/intune-devices-userexperienceanalyticsanomalycorrelationgroupoverview-update.md?view=graph-rest-beta) | [userExperienceAnalyticsAnomalyCorrelationGroupOverview](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsanomalycorrelationgroupoverview?view=graph-rest-beta) | Update the properties of a [userExperienceAnalyticsAnomalyCorrelationGroupOverview](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsanomalycorrelationgroupoverview?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The unique identifier for the user experience analytics anomaly correlation group overview object. |
| anomalyId | String | The unique identifier of the anomaly. Anomaly details such as name and type can be found in the UserExperienceAnalyticsAnomalySeverityOverview entity. |
| correlationGroupId | String | The unique identifier for the correlation group which will uniquely identify one of the correlation group within an anomaly. The correlation Id can be mapped to the correlation group name by concatinating the correlation group features. Example of correlation group name which is the indicative of concatenated features names are for names, Contoso manufacture 4.4.1 and Windows 11.22621.1485. |
| correlationGroupFeatures | [userExperienceAnalyticsAnomalyCorrelationGroupFeature](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsanomalycorrelationgroupfeature?view=graph-rest-beta) collection | Describes the features of a device that are shared between all devices in a correlation group. |
| correlationGroupPrevalence | [userExperienceAnalyticsAnomalyCorrelationGroupPrevalence](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsanomalycorrelationgroupprevalence?view=graph-rest-beta) | The prevalence of the correlation group. Possible values are: high, medium or low. Possible values are: `high`, `medium`, `low`, `unknownFutureValue`. |
| correlationGroupPrevalencePercentage | Double | The percentage of the devices in the correlation group that are anomalous. Valid values -1.79769313486232E+308 to 1.79769313486232E+308 |
| totalDeviceCount | Int32 | Indicates the total number of devices in the tenant. Valid values -2147483648 to 2147483647 |
| anomalyCorrelationGroupCount | Int32 | Indicates the number of correlation groups in the anomaly. Valid values -2147483648 to 2147483647 |
| correlationGroupDeviceCount | Int32 | Indicates the total number of devices in a correlation group. Valid values -2147483648 to 2147483647 |
| correlationGroupAnomalousDeviceCount | Int32 | Indicates the total number of devices affected by the anomaly in the correlation group. Valid values -2147483648 to 2147483647 |
| correlationGroupAtRiskDeviceCount | Int32 | Indicates the total number of devices at risk in the correlation group. Valid values -2147483648 to 2147483647 |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.userExperienceAnalyticsAnomalyCorrelationGroupOverview",
  "id": "String (identifier)",
  "anomalyId": "String",
  "correlationGroupId": "String",
  "correlationGroupFeatures": [
    {
      "@odata.type": "microsoft.graph.userExperienceAnalyticsAnomalyCorrelationGroupFeature",
      "deviceFeatureType": "String",
      "values": [
        "String"
      ]
    }
  ],
  "correlationGroupPrevalence": "String",
  "correlationGroupPrevalencePercentage": "4.2",
  "totalDeviceCount": 1024,
  "anomalyCorrelationGroupCount": 1024,
  "correlationGroupDeviceCount": 1024,
  "correlationGroupAnomalousDeviceCount": 1024,
  "correlationGroupAtRiskDeviceCount": 1024
}
```
