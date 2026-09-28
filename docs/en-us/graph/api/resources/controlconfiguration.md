<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/controlconfiguration?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-06-19 -->

# controlConfiguration resource type

Namespace: microsoft.graph

Defines the lifecycle and access policies of Entitlement Management within a tenant. Abstract type from which the [endUserSettings](https://learn.microsoft.com/en-us/graph/api/resources/endusersettings?view=graph-rest-1.0) resource is derived.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0).

## Methods

None.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| createdBy | String | The userPrincipalName of the user or identity that created the control configuration. |
| createdDateTime | DateTimeOffset | The date and time the control configuration was created. |
| id | String | The unique identifier for the control configuration. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). |
| isEnabled | Boolean | Determines whether or not the control configuration is enabled. |
| modifiedBy | String | The userPrincipalName of the user or identity that modified the control configuration. |
| modifiedDateTime | DateTimeOffset | The date and time the control configuration was modified. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.controlConfiguration",
  "id": "String (identifier)",
  "isEnabled": "Boolean",
  "createdBy": "String",
  "createdDateTime": "String (timestamp)",
  "modifiedBy": "String",
  "modifiedDateTime": "String (timestamp)"
}
```
