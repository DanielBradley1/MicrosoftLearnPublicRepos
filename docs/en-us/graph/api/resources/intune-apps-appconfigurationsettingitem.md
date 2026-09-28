<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-appconfigurationsettingitem?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# appConfigurationSettingItem resource type

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Contains properties for App configuration setting item.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| appConfigKey | String | app configuration key. |
| appConfigKeyType | [mdmAppConfigKeyType](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mdmappconfigkeytype?view=graph-rest-1.0) | app configuration key type. The possible values are: `stringType`, `integerType`, `realType`, `booleanType`, `tokenType`. |
| appConfigKeyValue | String | app configuration key value. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.appConfigurationSettingItem",
  "appConfigKey": "String",
  "appConfigKeyType": "String",
  "appConfigKeyValue": "String"
}
```
