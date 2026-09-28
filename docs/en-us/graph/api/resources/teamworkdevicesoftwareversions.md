<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/teamworkdevicesoftwareversions?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# teamworkDeviceSoftwareVersions resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the details about software versions for a Microsoft Teams-enabled [device](https://learn.microsoft.com/en-us/graph/api/resources/teamworkdevice?view=graph-rest-beta), including firmware, operating system, Microsoft Teams client, and admin agent.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| adminAgentSoftwareVersion | String | The software version for the admin agent running on the device. |
| firmwareSoftwareVersion | String | The software version for the firmware running on the device. |
| operatingSystemSoftwareVersion | String | The software version for the operating system on the device. |
| partnerAgentSoftwareVersion | String | The software version for the partner agent running on the device. |
| teamsClientSoftwareVersion | String | The software version for the Teams client running on the device. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.teamworkDeviceSoftwareVersions",
  "adminAgentSoftwareVersion": "String",
  "firmwareSoftwareVersion": "String",
  "operatingSystemSoftwareVersion": "String",
  "partnerAgentSoftwareVersion": "String",
  "teamsClientSoftwareVersion": "String"
}
```
