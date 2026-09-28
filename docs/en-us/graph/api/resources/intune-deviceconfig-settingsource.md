<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-settingsource?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-12-03 -->

# settingSource resource type

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String |  |
| displayName | String |  |
| sourceType | [settingSourceType](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-settingsourcetype?view=graph-rest-1.0) | . The possible values are: `deviceConfiguration`, `deviceIntent`. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.settingSource",
  "id": "String (identifier)",
  "displayName": "String",
  "sourceType": "String"
}
```
