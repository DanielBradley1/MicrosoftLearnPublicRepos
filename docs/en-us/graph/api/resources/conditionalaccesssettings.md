<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/conditionalaccesssettings?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-11-13 -->

# conditionalAccessSettings resource type \(Conditional Access\)

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents tenant-wide Conditional Access settings, including user-action exclusions for policies that target all resources.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta).

Access this singleton through `/identity/conditionalAccess/settings`. The singleton exists automatically; creating or listing settings isn't supported.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Get conditionalAccessSettings \(Conditional Access\)](https://learn.microsoft.com/en-us/graph/api/conditionalaccesssettings-get?view=graph-rest-beta) | [conditionalAccessSettings](https://learn.microsoft.com/en-us/graph/api/resources/conditionalaccesssettings?view=graph-rest-beta) | Get the tenant's Conditional Access settings. |
| [Update conditionalAccessSettings \(Conditional Access\)](https://learn.microsoft.com/en-us/graph/api/conditionalaccesssettings-update?view=graph-rest-beta) | [conditionalAccessSettings](https://learn.microsoft.com/en-us/graph/api/resources/conditionalaccesssettings?view=graph-rest-beta) | Update the tenant's Conditional Access settings. |
| [Delete conditionalAccessSettings](https://learn.microsoft.com/en-us/graph/api/conditionalaccessroot-delete-settings?view=graph-rest-beta) | None | Reset Conditional Access settings to their defaults. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| exclusions | [conditionalAccessExclusions](https://learn.microsoft.com/en-us/graph/api/resources/conditionalaccessexclusions?view=graph-rest-beta) | The tenant-wide exclusions configuration. |
| id | String | The unique identifier of the settings resource. Read-only. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). |
| modifiedDateTime | DateTimeOffset | The date and time the settings were last modified, in ISO 8601 format and UTC. Nullable. Read-only. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.conditionalAccessSettings",
  "id": "String (identifier)",
  "modifiedDateTime": "String (timestamp)",
  "exclusions": {
    "@odata.type": "microsoft.graph.conditionalAccessExclusions"
  }
}
```
