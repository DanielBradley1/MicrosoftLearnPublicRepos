<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-devicemanagementsettings?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-10-11 -->

# deviceManagementSettings resource type

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| deviceComplianceCheckinThresholdDays | Int32 | The number of days a device is allowed to go without checking in to remain compliant. |
| isScheduledActionEnabled | Boolean | Is feature enabled or not for scheduled action for rule. |
| secureByDefault | Boolean | Device should be noncompliant when there is no compliance policy targeted when this is true |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.deviceManagementSettings",
  "deviceComplianceCheckinThresholdDays": 1024,
  "isScheduledActionEnabled": true,
  "secureByDefault": true
}
```
