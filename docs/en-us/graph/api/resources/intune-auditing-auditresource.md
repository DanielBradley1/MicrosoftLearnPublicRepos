<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-auditing-auditresource?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# auditResource resource type

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

A class containing the properties for Audit Resource.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | Display name. |
| modifiedProperties | [auditProperty](https://learn.microsoft.com/en-us/graph/api/resources/intune-auditing-auditproperty?view=graph-rest-1.0) collection | List of modified properties. |
| type | String | Audit resource's type. |
| auditResourceType | String | Audit resource's type. |
| resourceId | String | Audit resource's Id. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.auditResource",
  "displayName": "String",
  "modifiedProperties": [
    {
      "@odata.type": "microsoft.graph.auditProperty",
      "displayName": "String",
      "oldValue": "String",
      "newValue": "String"
    }
  ],
  "type": "String",
  "auditResourceType": "String",
  "resourceId": "String"
}
```
