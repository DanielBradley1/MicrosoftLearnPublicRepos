<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsresourceperformance?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# userExperienceAnalyticsResourcePerformance resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

The user experience analytics resource performance entity.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List userExperienceAnalyticsResourcePerformances](https://learn.microsoft.com/en-us/graph/api/intune-devices-userexperienceanalyticsresourceperformance-list?view=graph-rest-beta) | [userExperienceAnalyticsResourcePerformance](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsresourceperformance?view=graph-rest-beta) collection | List properties and relationships of the [userExperienceAnalyticsResourcePerformance](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsresourceperformance?view=graph-rest-beta) objects. |
| [Get userExperienceAnalyticsResourcePerformance](https://learn.microsoft.com/en-us/graph/api/intune-devices-userexperienceanalyticsresourceperformance-get?view=graph-rest-beta) | [userExperienceAnalyticsResourcePerformance](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsresourceperformance?view=graph-rest-beta) | Read properties and relationships of the [userExperienceAnalyticsResourcePerformance](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsresourceperformance?view=graph-rest-beta) object. |
| [Create userExperienceAnalyticsResourcePerformance](https://learn.microsoft.com/en-us/graph/api/api/intune-devices-userexperienceanalyticsresourceperformance-create.md?view=graph-rest-beta) | [userExperienceAnalyticsResourcePerformance](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsresourceperformance?view=graph-rest-beta) | Create a new [userExperienceAnalyticsResourcePerformance](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsresourceperformance?view=graph-rest-beta) object. |
| [Delete userExperienceAnalyticsResourcePerformance](https://learn.microsoft.com/en-us/graph/api/api/intune-devices-userexperienceanalyticsresourceperformance-delete.md?view=graph-rest-beta) | None | Deletes a [userExperienceAnalyticsResourcePerformance](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsresourceperformance?view=graph-rest-beta). |
| [Update userExperienceAnalyticsResourcePerformance](https://learn.microsoft.com/en-us/graph/api/api/intune-devices-userexperienceanalyticsresourceperformance-update.md?view=graph-rest-beta) | [userExperienceAnalyticsResourcePerformance](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsresourceperformance?view=graph-rest-beta) | Update the properties of a [userExperienceAnalyticsResourcePerformance](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsresourceperformance?view=graph-rest-beta) object. |
| [summarizeDeviceResourcePerformance function](https://learn.microsoft.com/en-us/graph/api/intune-devices-userexperienceanalyticsresourceperformance-summarizedeviceresourceperformance?view=graph-rest-beta) | [userExperienceAnalyticsResourcePerformance](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsresourceperformance?view=graph-rest-beta) collection |  |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The unique identifier of the user experience analytics resource performance entity. |
| deviceId | String | The id of the device. |
| deviceName | String | The name of the device. |
| model | String | The user experience analytics device model. |
| deviceCount | Int64 | User experience analytics summarized device count. |
| manufacturer | String | The user experience analytics device manufacturer. |
| cpuSpikeTimePercentage | Double | CPU spike time in percentage. Valid values 0 to 100 |
| ramSpikeTimePercentage | Double | RAM spike time in percentage. Valid values 0 to 100 |
| cpuSpikeTimeScore | Int32 | The user experience analytics device CPU spike time score. Valid values 0 to 100 |
| cpuSpikeTimePercentageThreshold | Double | Threshold of cpuSpikeTimeScore. Valid values 0 to 100 |
| ramSpikeTimeScore | Int32 | The user experience analytics device RAM spike time score. Valid values 0 to 100 |
| ramSpikeTimePercentageThreshold | Double | Threshold of ramSpikeTimeScore. Valid values 0 to 100 |
| deviceResourcePerformanceScore | Int32 | Resource performance score of a specific device. Valid values 0 to 100 |
| averageSpikeTimeScore | Int32 | AverageSpikeTimeScore of a device or a model type. Valid values 0 to 100 |
| machineType | [userExperienceAnalyticsMachineType](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsmachinetype?view=graph-rest-beta) | Helps to identify if device is a physical device or virtual. Possible values are: `unknown`, `physical`, `virtual`, `unknownFutureValue`. |
| cpuDisplayName | String | The name of the processor on the device, For example, 11th Gen Intel\(R\) Core\(TM\) i7. |
| totalProcessorCoreCount | Int32 | The count of cores of the processor of device. Valid values 0 to 512 |
| cpuClockSpeedInMHz | Double | The clock speed of the processor, in MHz. Valid values 0 to 1000000 |
| totalRamInMB | Double | The total RAM of the device, in MB. Valid values 0 to 1000000 |
| diskType | [diskType](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-disktype?view=graph-rest-beta) | The type of disk storage used on the device. Possible values are: `unknown`, `hdd`, `ssd`, `unknownFutureValue`. |
| healthStatus | [userExperienceAnalyticsHealthState](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticshealthstate?view=graph-rest-beta) | The health state of the user experience analytics model. Possible values are: `unknown`, `insufficientData`, `needsAttention`, `meetingGoals`, `unknownFutureValue`. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.userExperienceAnalyticsResourcePerformance",
  "id": "String (identifier)",
  "deviceId": "String",
  "deviceName": "String",
  "model": "String",
  "deviceCount": 1024,
  "manufacturer": "String",
  "cpuSpikeTimePercentage": "4.2",
  "ramSpikeTimePercentage": "4.2",
  "cpuSpikeTimeScore": 1024,
  "cpuSpikeTimePercentageThreshold": "4.2",
  "ramSpikeTimeScore": 1024,
  "ramSpikeTimePercentageThreshold": "4.2",
  "deviceResourcePerformanceScore": 1024,
  "averageSpikeTimeScore": 1024,
  "machineType": "String",
  "cpuDisplayName": "String",
  "totalProcessorCoreCount": 1024,
  "cpuClockSpeedInMHz": "4.2",
  "totalRamInMB": "4.2",
  "diskType": "String",
  "healthStatus": "String"
}
```
