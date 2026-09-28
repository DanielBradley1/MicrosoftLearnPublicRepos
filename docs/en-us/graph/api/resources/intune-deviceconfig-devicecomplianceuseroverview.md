<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-devicecomplianceuseroverview?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# deviceComplianceUserOverview resource type

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [Get deviceComplianceUserOverview](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-devicecomplianceuseroverview-get?view=graph-rest-1.0) | [deviceComplianceUserOverview](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-devicecomplianceuseroverview?view=graph-rest-1.0) | Read properties and relationships of the [deviceComplianceUserOverview](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-devicecomplianceuseroverview?view=graph-rest-1.0) object. |
| [Update deviceComplianceUserOverview](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-devicecomplianceuseroverview-update?view=graph-rest-1.0) | [deviceComplianceUserOverview](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-devicecomplianceuseroverview?view=graph-rest-1.0) | Update the properties of a [deviceComplianceUserOverview](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-devicecomplianceuseroverview?view=graph-rest-1.0) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Key of the entity. |
| pendingCount | Int32 | Number of pending Users |
| notApplicableCount | Int32 | Number of not applicable users |
| successCount | Int32 | Number of succeeded Users |
| errorCount | Int32 | Number of error Users |
| failedCount | Int32 | Number of failed Users |
| lastUpdateDateTime | DateTimeOffset | Last update time |
| configurationVersion | Int32 | Version of the policy for that overview |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.deviceComplianceUserOverview",
  "id": "String (identifier)",
  "pendingCount": 1024,
  "notApplicableCount": 1024,
  "successCount": 1024,
  "errorCount": 1024,
  "failedCount": 1024,
  "lastUpdateDateTime": "String (timestamp)",
  "configurationVersion": 1024
}
```
