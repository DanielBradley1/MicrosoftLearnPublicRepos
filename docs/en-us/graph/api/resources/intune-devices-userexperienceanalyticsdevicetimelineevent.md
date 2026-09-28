<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsdevicetimelineevent?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# userExperienceAnalyticsDeviceTimelineEvent resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

The user experience analytics device event entity contains NRT device event details.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List userExperienceAnalyticsDeviceTimelineEvents](https://learn.microsoft.com/en-us/graph/api/api/intune-devices-userexperienceanalyticsdevicetimelineevent-list.md?view=graph-rest-beta) | [userExperienceAnalyticsDeviceTimelineEvent](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsdevicetimelineevent?view=graph-rest-beta) collection | List properties and relationships of the [userExperienceAnalyticsDeviceTimelineEvent](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsdevicetimelineevent?view=graph-rest-beta) objects. |
| [Get userExperienceAnalyticsDeviceTimelineEvent](https://learn.microsoft.com/en-us/graph/api/api/intune-devices-userexperienceanalyticsdevicetimelineevent-get.md?view=graph-rest-beta) | [userExperienceAnalyticsDeviceTimelineEvent](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsdevicetimelineevent?view=graph-rest-beta) | Read properties and relationships of the [userExperienceAnalyticsDeviceTimelineEvent](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsdevicetimelineevent?view=graph-rest-beta) object. |
| [Create userExperienceAnalyticsDeviceTimelineEvent](https://learn.microsoft.com/en-us/graph/api/api/intune-devices-userexperienceanalyticsdevicetimelineevent-create.md?view=graph-rest-beta) | [userExperienceAnalyticsDeviceTimelineEvent](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsdevicetimelineevent?view=graph-rest-beta) | Create a new [userExperienceAnalyticsDeviceTimelineEvent](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsdevicetimelineevent?view=graph-rest-beta) object. |
| [Delete userExperienceAnalyticsDeviceTimelineEvent](https://learn.microsoft.com/en-us/graph/api/api/intune-devices-userexperienceanalyticsdevicetimelineevent-delete.md?view=graph-rest-beta) | None | Deletes a [userExperienceAnalyticsDeviceTimelineEvent](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsdevicetimelineevent?view=graph-rest-beta). |
| [Update userExperienceAnalyticsDeviceTimelineEvent](https://learn.microsoft.com/en-us/graph/api/api/intune-devices-userexperienceanalyticsdevicetimelineevent-update.md?view=graph-rest-beta) | [userExperienceAnalyticsDeviceTimelineEvent](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsdevicetimelineevent?view=graph-rest-beta) | Update the properties of a [userExperienceAnalyticsDeviceTimelineEvent](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsdevicetimelineevent?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The unique identifier of the user experience analytics NRT device timeline event object. |
| deviceId | String | The id of the device where the event occurred. |
| eventDateTime | DateTimeOffset | The time the event occured. |
| eventLevel | [deviceEventLevel](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-deviceeventlevel?view=graph-rest-beta) | The severity level of the event enum. Possible values are: none, verbose, information, warning, error ,critical. Default value: none. Possible values are: `none`, `verbose`, `information`, `warning`, `error`, `critical`, `unknownFutureValue`. |
| eventSource | String | The source of the event. Examples include: Intune, Sccm. |
| eventName | String | The name of the event. Examples include: BootEvent, LogonEvent, AppCrashEvent, AppHangEvent. |
| eventDetails | String | The details provided by the event, format depends on event type. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.userExperienceAnalyticsDeviceTimelineEvent",
  "id": "String (identifier)",
  "deviceId": "String",
  "eventDateTime": "String (timestamp)",
  "eventLevel": "String",
  "eventSource": "String",
  "eventName": "String",
  "eventDetails": "String"
}
```
