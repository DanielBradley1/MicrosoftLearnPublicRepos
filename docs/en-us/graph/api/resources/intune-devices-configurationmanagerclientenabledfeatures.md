<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-configurationmanagerclientenabledfeatures?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# configurationManagerClientEnabledFeatures resource type

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

configuration Manager client enabled features

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| inventory | Boolean | Whether inventory is managed by Intune |
| modernApps | Boolean | Whether modern application is managed by Intune |
| resourceAccess | Boolean | Whether resource access is managed by Intune |
| deviceConfiguration | Boolean | Whether device configuration is managed by Intune |
| compliancePolicy | Boolean | Whether compliance policy is managed by Intune |
| windowsUpdateForBusiness | Boolean | Whether Windows Update for Business is managed by Intune |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.configurationManagerClientEnabledFeatures",
  "inventory": true,
  "modernApps": true,
  "resourceAccess": true,
  "deviceConfiguration": true,
  "compliancePolicy": true,
  "windowsUpdateForBusiness": true
}
```
