<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-userexperiencesettings?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-01-27 -->

# userExperienceSettings resource type

Namespace: microsoft.graph.windowsUpdates

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Settings that control the user's update experience on a device.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| daysUntilForcedReboot | Int32 | Specifies the number of days after an update is installed, during which the user of the device can control when the device restarts. |
| isHotpatchEnabled | Boolean | Specifies whether the update is offered as a hotpatch. It can only be set to `true` on automatic policies that target monthly security updates. |
| offerAsOptional | Boolean | Specifies whether the update is offered as **Optional** rather than **Required**. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.windowsUpdates.userExperienceSettings",
  "daysUntilForcedReboot": "Int32",
  "isHotpatchEnabled": "Boolean", 
  "offerAsOptional": "Boolean"
}
```
