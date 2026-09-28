<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-auditing-auditproperty?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# auditProperty resource type

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

A class containing the properties for Audit Property.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | Display name. |
| oldValue | String | Old value. |
| newValue | String | New value. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.auditProperty",
  "displayName": "String",
  "oldValue": "String",
  "newValue": "String"
}
```
