<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-tenantattachrbacstate?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# tenantAttachRBACState resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Represents result of GetState API.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| enabled | Boolean | Indicates whether the tenant is enabled for Tenant Attach with role management. TRUE if enabled, FALSE if the Tenant Attach with rolemanagement is disabled. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.tenantAttachRBACState",
  "enabled": true
}
```
