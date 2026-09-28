<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-wip-windowsinformationprotectionnetworklearningsummary?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# windowsInformationProtectionNetworkLearningSummary resource type

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Windows Information Protection Network learning Summary entity.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List windowsInformationProtectionNetworkLearningSummaries](https://learn.microsoft.com/en-us/graph/api/intune-wip-windowsinformationprotectionnetworklearningsummary-list?view=graph-rest-1.0) | [windowsInformationProtectionNetworkLearningSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-wip-windowsinformationprotectionnetworklearningsummary?view=graph-rest-1.0) collection | List properties and relationships of the [windowsInformationProtectionNetworkLearningSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-wip-windowsinformationprotectionnetworklearningsummary?view=graph-rest-1.0) objects. |
| [Get windowsInformationProtectionNetworkLearningSummary](https://learn.microsoft.com/en-us/graph/api/intune-wip-windowsinformationprotectionnetworklearningsummary-get?view=graph-rest-1.0) | [windowsInformationProtectionNetworkLearningSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-wip-windowsinformationprotectionnetworklearningsummary?view=graph-rest-1.0) | Read properties and relationships of the [windowsInformationProtectionNetworkLearningSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-wip-windowsinformationprotectionnetworklearningsummary?view=graph-rest-1.0) object. |
| [Create windowsInformationProtectionNetworkLearningSummary](https://learn.microsoft.com/en-us/graph/api/intune-wip-windowsinformationprotectionnetworklearningsummary-create?view=graph-rest-1.0) | [windowsInformationProtectionNetworkLearningSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-wip-windowsinformationprotectionnetworklearningsummary?view=graph-rest-1.0) | Create a new [windowsInformationProtectionNetworkLearningSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-wip-windowsinformationprotectionnetworklearningsummary?view=graph-rest-1.0) object. |
| [Delete windowsInformationProtectionNetworkLearningSummary](https://learn.microsoft.com/en-us/graph/api/intune-wip-windowsinformationprotectionnetworklearningsummary-delete?view=graph-rest-1.0) | None | Deletes a [windowsInformationProtectionNetworkLearningSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-wip-windowsinformationprotectionnetworklearningsummary?view=graph-rest-1.0). |
| [Update windowsInformationProtectionNetworkLearningSummary](https://learn.microsoft.com/en-us/graph/api/intune-wip-windowsinformationprotectionnetworklearningsummary-update?view=graph-rest-1.0) | [windowsInformationProtectionNetworkLearningSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-wip-windowsinformationprotectionnetworklearningsummary?view=graph-rest-1.0) | Update the properties of a [windowsInformationProtectionNetworkLearningSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-wip-windowsinformationprotectionnetworklearningsummary?view=graph-rest-1.0) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Unique Identifier for the WindowsInformationProtectionNetworkLearningSummary. |
| url | String | Website url |
| deviceCount | Int32 | Device Count |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.windowsInformationProtectionNetworkLearningSummary",
  "id": "String (identifier)",
  "url": "String",
  "deviceCount": 1024
}
```
