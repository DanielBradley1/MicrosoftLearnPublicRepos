<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/azureadregistrationpolicy?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-05-01 -->

# azureADRegistrationPolicy resource type

Namespace: microsoft.graph

Represents the policy scope of the Microsoft Entra tenant that controls the ability for users and groups to register device identities to your organization using **Microsoft Entra registered**. Configured in the **azureADRegistration** property of [device registration policy](https://learn.microsoft.com/en-us/graph/api/resources/deviceregistrationpolicy?view=graph-rest-1.0). For more information, see [What is a device identity?](https://learn.microsoft.com/en-us/azure/active-directory/devices/overview).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| allowedToRegister | [deviceRegistrationMembership](https://learn.microsoft.com/en-us/graph/api/resources/deviceregistrationmembership?view=graph-rest-1.0) | Determines if Microsoft Entra registered is allowed. |
| isAdminConfigurable | Boolean | Determines if administrators can modify this policy. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.azureADRegistrationPolicy",
  "isAdminConfigurable": "Boolean",
  "allowedToRegister": {
    "@odata.type": "microsoft.graph.deviceRegistrationMembership"
  }
}
```
