<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsdevicetimelineevents?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-12-03 -->

# userExperienceAnalyticsDeviceTimelineEvents resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

The user experience analytics device events entity contains NRT device events details.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List userExperienceAnalyticsDeviceTimelineEventses](https://learn.microsoft.com/en-us/graph/api/api/intune-devices-userexperienceanalyticsdevicetimelineevents-list.md?view=graph-rest-beta) | [userExperienceAnalyticsDeviceTimelineEvents](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsdevicetimelineevents?view=graph-rest-beta) collection | List properties and relationships of the [userExperienceAnalyticsDeviceTimelineEvents](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsdevicetimelineevents?view=graph-rest-beta) objects. |
| [Get userExperienceAnalyticsDeviceTimelineEvents](https://learn.microsoft.com/en-us/graph/api/intune-devices-userexperienceanalyticsdevicetimelineevents-get?view=graph-rest-beta) | [userExperienceAnalyticsDeviceTimelineEvents](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsdevicetimelineevents?view=graph-rest-beta) | Read properties and relationships of the [userExperienceAnalyticsDeviceTimelineEvents](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsdevicetimelineevents?view=graph-rest-beta) object. |
| [Create userExperienceAnalyticsDeviceTimelineEvents](https://learn.microsoft.com/en-us/graph/api/api/intune-devices-userexperienceanalyticsdevicetimelineevents-create.md?view=graph-rest-beta) | [userExperienceAnalyticsDeviceTimelineEvents](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsdevicetimelineevents?view=graph-rest-beta) | Create a new [userExperienceAnalyticsDeviceTimelineEvents](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsdevicetimelineevents?view=graph-rest-beta) object. |
| [Delete userExperienceAnalyticsDeviceTimelineEvents](https://learn.microsoft.com/en-us/graph/api/api/intune-devices-userexperienceanalyticsdevicetimelineevents-delete.md?view=graph-rest-beta) | None | Deletes a [userExperienceAnalyticsDeviceTimelineEvents](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsdevicetimelineevents?view=graph-rest-beta). |
| [Update userExperienceAnalyticsDeviceTimelineEvents](https://learn.microsoft.com/en-us/graph/api/api/intune-devices-userexperienceanalyticsdevicetimelineevents-update.md?view=graph-rest-beta) | [userExperienceAnalyticsDeviceTimelineEvents](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsdevicetimelineevents?view=graph-rest-beta) | Update the properties of a [userExperienceAnalyticsDeviceTimelineEvents](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsdevicetimelineevents?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The unique identifier of the user experience analytics NRT device timeline events object. |
| deviceId | String | The id of the device where the event occurred. |
| eventDateTime | DateTimeOffset | The time the event occured. |
| eventLevel | [deviceEventLevel](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-deviceeventlevel?view=graph-rest-beta) | The severity level of the event enum. The possible values are: `none`, `verbose`, `information`, `warning`, `error` ,`critical`. Default value: `none`. The possible values are: `none`, `verbose`, `information`, `warning`, `error`, `critical`, `unknownFutureValue`. |
| eventSource | String | The source of the event. Examples include: Intune, Sccm. |
| eventName | String | The name of the event. Examples include: BootEvent, LogonEvent, AppCrashEvent, AppHangEvent. |
| eventDetails | String | The details provided by the event, format depends on event type. |
| eventAdditionalInformation | String | Placeholder value for future expansion. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.userExperienceAnalyticsDeviceTimelineEvents",
  "id": "String (identifier)",
  "deviceId": "String",
  "eventDateTime": "String (timestamp)",
  "eventLevel": "String",
  "eventSource": "String",
  "eventName": "String",
  "eventDetails": "String",
  "eventAdditionalInformation": "String"
}
```
