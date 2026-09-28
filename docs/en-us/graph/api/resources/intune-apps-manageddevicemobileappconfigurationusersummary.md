<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-manageddevicemobileappconfigurationusersummary?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# managedDeviceMobileAppConfigurationUserSummary resource type

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Contains properties, inherited properties and actions for an MDM mobile app configuration user status summary.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [Get managedDeviceMobileAppConfigurationUserSummary](https://learn.microsoft.com/en-us/graph/api/intune-apps-manageddevicemobileappconfigurationusersummary-get?view=graph-rest-1.0) | [managedDeviceMobileAppConfigurationUserSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-manageddevicemobileappconfigurationusersummary?view=graph-rest-1.0) | Read properties and relationships of the [managedDeviceMobileAppConfigurationUserSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-manageddevicemobileappconfigurationusersummary?view=graph-rest-1.0) object. |
| [Update managedDeviceMobileAppConfigurationUserSummary](https://learn.microsoft.com/en-us/graph/api/intune-apps-manageddevicemobileappconfigurationusersummary-update?view=graph-rest-1.0) | [managedDeviceMobileAppConfigurationUserSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-manageddevicemobileappconfigurationusersummary?view=graph-rest-1.0) | Update the properties of a [managedDeviceMobileAppConfigurationUserSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-manageddevicemobileappconfigurationusersummary?view=graph-rest-1.0) object. |

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
  "@odata.type": "#microsoft.graph.managedDeviceMobileAppConfigurationUserSummary",
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
