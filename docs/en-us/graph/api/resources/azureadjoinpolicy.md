<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/azureadjoinpolicy?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-05-01 -->

# azureADJoinPolicy resource type

Namespace: microsoft.graph

Represents the policy scope of the Microsoft Entra tenant that controls the ability for users and groups to register device identities to your organization using Microsoft Entra join. Configured in the **azureADJoin** property of [deviceRegistrationPolicy](https://learn.microsoft.com/en-us/graph/api/resources/deviceregistrationpolicy?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| allowedToJoin | [deviceRegistrationMembership](https://learn.microsoft.com/en-us/graph/api/resources/deviceregistrationmembership?view=graph-rest-1.0) | Determines if Microsoft Entra join is allowed. |
| isAdminConfigurable | Boolean | Determines if administrators can modify this policy. |
| localAdmins | [localAdminSettings](https://learn.microsoft.com/en-us/graph/api/resources/localadminsettings?view=graph-rest-1.0) | Determines who becomes a local administrator on joined devices. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.azureADJoinPolicy",
  "isAdminConfigurable": "Boolean",
  "allowedToJoin": {
    "@odata.type": "microsoft.graph.deviceRegistrationMembership"
  },
  "localAdmins": {
    "@odata.type": "microsoft.graph.localAdminSettings"
  }
}
```
