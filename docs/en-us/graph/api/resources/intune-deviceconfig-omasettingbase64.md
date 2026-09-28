<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-omasettingbase64?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# omaSettingBase64 resource type

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

OMA Settings Base64 definition.

Inherits from [omaSetting](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-omasetting?view=graph-rest-1.0)

## Properties

| Property | Type | Description |  |  |  |
| :--- | :--- | :--- | --- | --- | --- |
| displayName | String | Display Name. Inherited from [omaSetting](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-omasetting?view=graph-rest-1.0) |  |  |  |
| description | String | Description. Inherited from [omaSetting](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-omasetting?view=graph-rest-1.0) |  |  |  |
| omaUri | String | OMA. Inherited from [omaSetting](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-omasetting?view=graph-rest-1.0) |  |  |  |
| fileName | String | File name associated with the Value property \(\*.cer | \*.crt | \*.p7b | \*.bin\). |
| value | String | Value. \(Base64 encoded string\) |  |  |  |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.omaSettingBase64",
  "displayName": "String",
  "description": "String",
  "omaUri": "String",
  "fileName": "String",
  "value": "String"
}
```
