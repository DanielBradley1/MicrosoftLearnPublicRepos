<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-omasettingfloatingpoint?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# omaSettingFloatingPoint resource type

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

OMA Settings Floating Point definition.

Inherits from [omaSetting](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-omasetting?view=graph-rest-1.0)

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | Display Name. Inherited from [omaSetting](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-omasetting?view=graph-rest-1.0) |
| description | String | Description. Inherited from [omaSetting](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-omasetting?view=graph-rest-1.0) |
| omaUri | String | OMA. Inherited from [omaSetting](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-omasetting?view=graph-rest-1.0) |
| value | Single | Value. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.omaSettingFloatingPoint",
  "displayName": "String",
  "description": "String",
  "omaUri": "String",
  "value": 4.2
}
```
