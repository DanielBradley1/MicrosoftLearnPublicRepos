<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/teamworkdatetimeconfiguration?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# teamworkDateTimeConfiguration resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents date and time configuration details for a Microsoft Teams-enabled [device](https://learn.microsoft.com/en-us/graph/api/resources/teamworkdevice?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| dateFormat | String | The date format for the device. |
| officeHoursEndTime | TimeOfDay | The time of the day when the device is turned off. |
| officeHoursStartTime | TimeOfDay | The time of the day when the device is turned on. |
| timeFormat | String | The time format for the device. |
| timeZone | String | The time zone to which the office hours apply. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.teamworkDateTimeConfiguration",
  "dateFormat": "String",
  "officeHoursEndTime": "String (time of day)",
  "officeHoursStartTime": "String (time of day)",
  "timeFormat": "String",
  "timeZone": "String"
}
```
