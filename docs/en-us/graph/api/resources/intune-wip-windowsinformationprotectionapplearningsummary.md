<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-wip-windowsinformationprotectionapplearningsummary?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-01-08 -->

# windowsInformationProtectionAppLearningSummary resource type

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Windows Information Protection AppLearning Summary entity.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List windowsInformationProtectionAppLearningSummaries](https://learn.microsoft.com/en-us/graph/api/intune-wip-windowsinformationprotectionapplearningsummary-list?view=graph-rest-1.0) | [windowsInformationProtectionAppLearningSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-wip-windowsinformationprotectionapplearningsummary?view=graph-rest-1.0) collection | List properties and relationships of the [windowsInformationProtectionAppLearningSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-wip-windowsinformationprotectionapplearningsummary?view=graph-rest-1.0) objects. |
| [Get windowsInformationProtectionAppLearningSummary](https://learn.microsoft.com/en-us/graph/api/intune-wip-windowsinformationprotectionapplearningsummary-get?view=graph-rest-1.0) | [windowsInformationProtectionAppLearningSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-wip-windowsinformationprotectionapplearningsummary?view=graph-rest-1.0) | Read properties and relationships of the [windowsInformationProtectionAppLearningSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-wip-windowsinformationprotectionapplearningsummary?view=graph-rest-1.0) object. |
| [Create windowsInformationProtectionAppLearningSummary](https://learn.microsoft.com/en-us/graph/api/intune-wip-windowsinformationprotectionapplearningsummary-create?view=graph-rest-1.0) | [windowsInformationProtectionAppLearningSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-wip-windowsinformationprotectionapplearningsummary?view=graph-rest-1.0) | Create a new [windowsInformationProtectionAppLearningSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-wip-windowsinformationprotectionapplearningsummary?view=graph-rest-1.0) object. |
| [Delete windowsInformationProtectionAppLearningSummary](https://learn.microsoft.com/en-us/graph/api/intune-wip-windowsinformationprotectionapplearningsummary-delete?view=graph-rest-1.0) | None | Deletes a [windowsInformationProtectionAppLearningSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-wip-windowsinformationprotectionapplearningsummary?view=graph-rest-1.0). |
| [Update windowsInformationProtectionAppLearningSummary](https://learn.microsoft.com/en-us/graph/api/intune-wip-windowsinformationprotectionapplearningsummary-update?view=graph-rest-1.0) | [windowsInformationProtectionAppLearningSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-wip-windowsinformationprotectionapplearningsummary?view=graph-rest-1.0) | Update the properties of a [windowsInformationProtectionAppLearningSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-wip-windowsinformationprotectionapplearningsummary?view=graph-rest-1.0) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Unique Identifier for the WindowsInformationProtectionAppLearningSummary. |
| applicationName | String | Application Name |
| applicationType | [applicationType](https://learn.microsoft.com/en-us/graph/api/resources/intune-wip-applicationtype?view=graph-rest-1.0) | Application Type. The possible values are: `universal`, `desktop`. |
| deviceCount | Int32 | Device Count |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.windowsInformationProtectionAppLearningSummary",
  "id": "String (identifier)",
  "applicationName": "String",
  "applicationType": "String",
  "deviceCount": 1024
}
```
