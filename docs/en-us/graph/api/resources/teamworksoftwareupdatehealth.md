<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/teamworksoftwareupdatehealth?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# teamworkSoftwareUpdateHealth resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the details about the software updates available for different components, such as admin agent, company portal, firmware, operating system, partner agent, and Microsoft Teams client, in a Microsoft Teams-enabled [device](https://learn.microsoft.com/en-us/graph/api/resources/teamworkdevice?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| adminAgentSoftwareUpdateStatus | [teamworkSoftwareUpdateStatus](https://learn.microsoft.com/en-us/graph/api/resources/teamworksoftwareupdatestatus?view=graph-rest-beta) | The software update available for the admin agent. |
| companyPortalSoftwareUpdateStatus | [teamworkSoftwareUpdateStatus](https://learn.microsoft.com/en-us/graph/api/resources/teamworksoftwareupdatestatus?view=graph-rest-beta) | The software update available for the company portal. |
| firmwareSoftwareUpdateStatus | [teamworkSoftwareUpdateStatus](https://learn.microsoft.com/en-us/graph/api/resources/teamworksoftwareupdatestatus?view=graph-rest-beta) | The software update available for the firmware. |
| operatingSystemSoftwareUpdateStatus | [teamworkSoftwareUpdateStatus](https://learn.microsoft.com/en-us/graph/api/resources/teamworksoftwareupdatestatus?view=graph-rest-beta) | The software update available for the operating system. |
| partnerAgentSoftwareUpdateStatus | [teamworkSoftwareUpdateStatus](https://learn.microsoft.com/en-us/graph/api/resources/teamworksoftwareupdatestatus?view=graph-rest-beta) | The software update available for the partner agent. |
| teamsClientSoftwareUpdateStatus | [teamworkSoftwareUpdateStatus](https://learn.microsoft.com/en-us/graph/api/resources/teamworksoftwareupdatestatus?view=graph-rest-beta) | The software update available for the Teams client. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.teamworkSoftwareUpdateHealth",
  "adminAgentSoftwareUpdateStatus": {
    "@odata.type": "microsoft.graph.teamworkSoftwareUpdateStatus"
  },
  "companyPortalSoftwareUpdateStatus": {
    "@odata.type": "microsoft.graph.teamworkSoftwareUpdateStatus"
  },
  "firmwareSoftwareUpdateStatus": {
    "@odata.type": "microsoft.graph.teamworkSoftwareUpdateStatus"
  },
  "operatingSystemSoftwareUpdateStatus": {
    "@odata.type": "microsoft.graph.teamworkSoftwareUpdateStatus"
  },
  "partnerAgentSoftwareUpdateStatus": {
    "@odata.type": "microsoft.graph.teamworkSoftwareUpdateStatus"
  },
  "teamsClientSoftwareUpdateStatus": {
    "@odata.type": "microsoft.graph.teamworkSoftwareUpdateStatus"
  }
}
```
