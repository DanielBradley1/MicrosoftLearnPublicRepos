<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-manageddevicemobileappconfigurationdevicesummary?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# managedDeviceMobileAppConfigurationDeviceSummary resource type

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Contains properties, inherited properties and actions for an MDM mobile app configuration device status summary.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [Get managedDeviceMobileAppConfigurationDeviceSummary](https://learn.microsoft.com/en-us/graph/api/intune-apps-manageddevicemobileappconfigurationdevicesummary-get?view=graph-rest-1.0) | [managedDeviceMobileAppConfigurationDeviceSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-manageddevicemobileappconfigurationdevicesummary?view=graph-rest-1.0) | Read properties and relationships of the [managedDeviceMobileAppConfigurationDeviceSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-manageddevicemobileappconfigurationdevicesummary?view=graph-rest-1.0) object. |
| [Update managedDeviceMobileAppConfigurationDeviceSummary](https://learn.microsoft.com/en-us/graph/api/intune-apps-manageddevicemobileappconfigurationdevicesummary-update?view=graph-rest-1.0) | [managedDeviceMobileAppConfigurationDeviceSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-manageddevicemobileappconfigurationdevicesummary?view=graph-rest-1.0) | Update the properties of a [managedDeviceMobileAppConfigurationDeviceSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-manageddevicemobileappconfigurationdevicesummary?view=graph-rest-1.0) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Key of the entity. |
| pendingCount | Int32 | Number of pending devices |
| notApplicableCount | Int32 | Number of not applicable devices |
| successCount | Int32 | Number of succeeded devices |
| errorCount | Int32 | Number of error devices |
| failedCount | Int32 | Number of failed devices |
| lastUpdateDateTime | DateTimeOffset | Last update time |
| configurationVersion | Int32 | Version of the policy for that overview |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.managedDeviceMobileAppConfigurationDeviceSummary",
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
