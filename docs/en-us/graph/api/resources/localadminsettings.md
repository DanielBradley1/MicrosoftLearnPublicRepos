<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/localadminsettings?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-05-01 -->

# localAdminSettings resource type

Namespace: microsoft.graph

Controls local administrators on Microsoft Entra-joined devices in a device registration policy. Configured on the **localAdmins** property of [azureADJoinPolicy](https://learn.microsoft.com/en-us/graph/api/resources/azureadjoinpolicy?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| enableGlobalAdmins | Boolean | Indicates whether global administrators are local administrators on all Microsoft Entra-joined devices. This setting only applies to future registrations. Default is `true`. |
| registeringUsers | [deviceRegistrationMembership](https://learn.microsoft.com/en-us/graph/api/resources/deviceregistrationmembership?view=graph-rest-1.0) | Determines the users and groups that become local administrators on Microsoft Entra joined devices that they register. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.localAdminSettings",
  "enableGlobalAdmins": "Boolean",
  "registeringUsers": {
    "@odata.type": "microsoft.graph.deviceRegistrationMembership"
  }
}
```
