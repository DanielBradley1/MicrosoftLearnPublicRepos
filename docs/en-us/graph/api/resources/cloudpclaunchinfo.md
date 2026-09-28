<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/cloudpclaunchinfo?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-10-17 -->

# cloudPcLaunchInfo resource type \(deprecated\)

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Caution

The **cloudPcLaunchInfo** resource is deprecated and will stop returning data on October 30, 2026. Going forward, use the [cloudPcLaunchDetail](https://learn.microsoft.com/en-us/graph/api/resources/cloudpclaunchdetail?view=graph-rest-beta) API.

Contains the information to connect a [cloudPC](https://learn.microsoft.com/en-us/graph/api/resources/cloudpc?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| cloudPcId | String | The unique identifier of the Cloud PC. |
| cloudPcLaunchUrl | String | The connect URL of the Cloud PC. |
| windows365SwitchCompatible | Boolean | Indicates whether the Cloud PC supports switch functionality. If the value is `true`, it supports switch functionality; otherwise, `false`. |
| windows365SwitchNotCompatibleReason | String | Indicates the reason the Cloud PC doesn't support switch. `CPCOsVersionNotMeetRequirement` indicates that the user needs to update their Cloud PC operation system version. `CPCHardwareNotMeetRequirement` indicates that the Cloud PC needs more CPU or RAM to support the functionality. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.cloudPcLaunchInfo",
  "cloudPcId": "String",
  "cloudPcLaunchUrl": "String",
  "windows365SwitchCompatible":"Boolean",
  "windows365SwitchNotCompatibleReason":"String"
}
```
