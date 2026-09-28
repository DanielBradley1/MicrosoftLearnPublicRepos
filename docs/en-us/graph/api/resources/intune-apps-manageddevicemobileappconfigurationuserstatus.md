<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-manageddevicemobileappconfigurationuserstatus?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# managedDeviceMobileAppConfigurationUserStatus resource type

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Contains properties, inherited properties and actions for an MDM mobile app configuration status for a user.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List managedDeviceMobileAppConfigurationUserStatuses](https://learn.microsoft.com/en-us/graph/api/intune-apps-manageddevicemobileappconfigurationuserstatus-list?view=graph-rest-1.0) | [managedDeviceMobileAppConfigurationUserStatus](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-manageddevicemobileappconfigurationuserstatus?view=graph-rest-1.0) collection | List properties and relationships of the [managedDeviceMobileAppConfigurationUserStatus](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-manageddevicemobileappconfigurationuserstatus?view=graph-rest-1.0) objects. |
| [Get managedDeviceMobileAppConfigurationUserStatus](https://learn.microsoft.com/en-us/graph/api/intune-apps-manageddevicemobileappconfigurationuserstatus-get?view=graph-rest-1.0) | [managedDeviceMobileAppConfigurationUserStatus](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-manageddevicemobileappconfigurationuserstatus?view=graph-rest-1.0) | Read properties and relationships of the [managedDeviceMobileAppConfigurationUserStatus](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-manageddevicemobileappconfigurationuserstatus?view=graph-rest-1.0) object. |
| [Create managedDeviceMobileAppConfigurationUserStatus](https://learn.microsoft.com/en-us/graph/api/intune-apps-manageddevicemobileappconfigurationuserstatus-create?view=graph-rest-1.0) | [managedDeviceMobileAppConfigurationUserStatus](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-manageddevicemobileappconfigurationuserstatus?view=graph-rest-1.0) | Create a new [managedDeviceMobileAppConfigurationUserStatus](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-manageddevicemobileappconfigurationuserstatus?view=graph-rest-1.0) object. |
| [Delete managedDeviceMobileAppConfigurationUserStatus](https://learn.microsoft.com/en-us/graph/api/intune-apps-manageddevicemobileappconfigurationuserstatus-delete?view=graph-rest-1.0) | None | Deletes a [managedDeviceMobileAppConfigurationUserStatus](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-manageddevicemobileappconfigurationuserstatus?view=graph-rest-1.0). |
| [Update managedDeviceMobileAppConfigurationUserStatus](https://learn.microsoft.com/en-us/graph/api/intune-apps-manageddevicemobileappconfigurationuserstatus-update?view=graph-rest-1.0) | [managedDeviceMobileAppConfigurationUserStatus](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-manageddevicemobileappconfigurationuserstatus?view=graph-rest-1.0) | Update the properties of a [managedDeviceMobileAppConfigurationUserStatus](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-manageddevicemobileappconfigurationuserstatus?view=graph-rest-1.0) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Key of the entity. |
| userDisplayName | String | User name of the DevicePolicyStatus. |
| devicesCount | Int32 | Devices count for that user. |
| status | [complianceStatus](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-compliancestatus?view=graph-rest-1.0) | Compliance status of the policy report. The possible values are: `unknown`, `notApplicable`, `compliant`, `remediated`, `nonCompliant`, `error`, `conflict`, `notAssigned`. |
| lastReportedDateTime | DateTimeOffset | Last modified date time of the policy report. |
| userPrincipalName | String | UserPrincipalName. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.managedDeviceMobileAppConfigurationUserStatus",
  "id": "String (identifier)",
  "userDisplayName": "String",
  "devicesCount": 1024,
  "status": "String",
  "lastReportedDateTime": "String (timestamp)",
  "userPrincipalName": "String"
}
```
