<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsbatteryhealthcapacitydetails?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# userExperienceAnalyticsBatteryHealthCapacityDetails resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

The user experience analytics battery health capacity entity contains count of devices broken down into 3 categories - devices with capacity > 80%, devices with capacity 50-80% and devices with capacity < 50 %.This API provides the count of devices in these 3 categories..

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [Get userExperienceAnalyticsBatteryHealthCapacityDetails](https://learn.microsoft.com/en-us/graph/api/intune-devices-userexperienceanalyticsbatteryhealthcapacitydetails-get?view=graph-rest-beta) | [userExperienceAnalyticsBatteryHealthCapacityDetails](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsbatteryhealthcapacitydetails?view=graph-rest-beta) | Read properties and relationships of the [userExperienceAnalyticsBatteryHealthCapacityDetails](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsbatteryhealthcapacitydetails?view=graph-rest-beta) object. |
| [Update userExperienceAnalyticsBatteryHealthCapacityDetails](https://learn.microsoft.com/en-us/graph/api/api/intune-devices-userexperienceanalyticsbatteryhealthcapacitydetails-update.md?view=graph-rest-beta) | [userExperienceAnalyticsBatteryHealthCapacityDetails](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsbatteryhealthcapacitydetails?view=graph-rest-beta) | Update the properties of a [userExperienceAnalyticsBatteryHealthCapacityDetails](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsbatteryhealthcapacitydetails?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The unique identifier of the user experience analytics battery health capacity object. |
| activeDevices | Int32 | Number of active devices within the tenant. Valid values 0 to 2147483647 |
| batteryCapacityGood | Int32 | Number of devices whose battery maximum capacity is greater than 80%. Valid values 0 to 2147483647 |
| batteryCapacityFair | Int32 | Number of devices whose battery maximum capacity is greater than 50% but lesser than 80%. Valid values 0 to 2147483647 |
| batteryCapacityPoor | Int32 | Number of devices whose battery maximum capacity is lesser than 50%. Valid values 0 to 2147483647 |
| lastRefreshedDateTime | DateTimeOffset | Recorded date time of this capacity details instance. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.userExperienceAnalyticsBatteryHealthCapacityDetails",
  "id": "String (identifier)",
  "activeDevices": 1024,
  "batteryCapacityGood": 1024,
  "batteryCapacityFair": 1024,
  "batteryCapacityPoor": 1024,
  "lastRefreshedDateTime": "String (timestamp)"
}
```
