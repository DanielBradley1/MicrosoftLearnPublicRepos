<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-remoteassistance-remoteassistancesettings?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-01-08 -->

# remoteAssistanceSettings resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Remote assistance settings for the account

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [Get remoteAssistanceSettings](https://learn.microsoft.com/en-us/graph/api/intune-remoteassistance-remoteassistancesettings-get?view=graph-rest-beta) | [remoteAssistanceSettings](https://learn.microsoft.com/en-us/graph/api/resources/intune-remoteassistance-remoteassistancesettings?view=graph-rest-beta) | Read properties and relationships of the [remoteAssistanceSettings](https://learn.microsoft.com/en-us/graph/api/resources/intune-remoteassistance-remoteassistancesettings?view=graph-rest-beta) object. |
| [Update remoteAssistanceSettings](https://learn.microsoft.com/en-us/graph/api/intune-remoteassistance-remoteassistancesettings-update?view=graph-rest-beta) | [remoteAssistanceSettings](https://learn.microsoft.com/en-us/graph/api/resources/intune-remoteassistance-remoteassistancesettings?view=graph-rest-beta) | Update the properties of a [remoteAssistanceSettings](https://learn.microsoft.com/en-us/graph/api/resources/intune-remoteassistance-remoteassistancesettings?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The remote assistance settings identifier |
| remoteAssistanceState | [remoteAssistanceState](https://learn.microsoft.com/en-us/graph/api/resources/intune-remoteassistance-remoteassistancestate?view=graph-rest-beta) | The current state of remote assistance for the account. Possible values are: disabled, enabled. This setting is configurable by the admin. Remote assistance settings that have not yet been configured by the admin have a disabled state. Returned by default. Possible values are: `disabled`, `enabled`. |
| allowSessionsToUnenrolledDevices | Boolean | Indicates if sessions to unenrolled devices are allowed for the account. This setting is configurable by the admin. Default value is false. |
| blockChat | Boolean | Indicates if sessions to block chat function. This setting is configurable by the admin. Default value is false. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.remoteAssistanceSettings",
  "id": "String (identifier)",
  "remoteAssistanceState": "String",
  "allowSessionsToUnenrolledDevices": true,
  "blockChat": true
}
```
