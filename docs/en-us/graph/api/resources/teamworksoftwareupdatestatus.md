<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/teamworksoftwareupdatestatus?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# teamworkSoftwareUpdateStatus resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the details about the update status of the software for various components, such as admin agent, company portal, firmware, operating system, partner agent, and Microsoft Teams client, in a Microsoft Teams-enabled [device](https://learn.microsoft.com/en-us/graph/api/resources/teamworkdevice?view=graph-rest-beta). It indicates whether a software update is required or not.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| availableVersion | String | The available software version to update. |
| currentVersion | String | The current software version. |
| softwareFreshness | teamworkSoftwareFreshness | The update status of the software. The possible values are: `unknown`, `latest`, `updateAvailable`, `unknownFutureValue`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.teamworkSoftwareUpdateStatus",
  "availableVersion": "String",
  "currentVersion": "String",
  "softwareFreshness": "String"
}
```
