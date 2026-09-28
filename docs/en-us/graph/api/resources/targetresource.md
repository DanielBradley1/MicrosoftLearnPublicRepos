<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/targetresource?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-07-04 -->

# targetResource resource type

Namespace: microsoft.graph

Represents target resource types associated with audit activity. This object is configured in the **targetResources** property of [directoryAudit](https://learn.microsoft.com/en-us/graph/api/resources/directoryaudit?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | Indicates the visible name defined for the resource. Typically specified when the resource is created. |
| groupType | groupType | When **type** is set to `Group`, this indicates the group type. The possible values are: `unifiedGroups`, `azureAD`, and `unknownFutureValue` |
| id | String | Indicates the unique ID of the resource. |
| modifiedProperties | [modifiedProperty](https://learn.microsoft.com/en-us/graph/api/resources/modifiedproperty?view=graph-rest-1.0) collection | Indicates name, old value and new value of each attribute that changed. Property values depend on the operation **type**. |
| type | String | Describes the resource type. Example values include `Application`, `Group`, `ServicePrincipal`, and `User`. |
| userPrincipalName | String | When **type** is set to `User`, this includes the user name that initiated the action; `null` for other types. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "id": "String",
  "displayName": "String",
  "type": "String",
  "userPrincipalName": "String",
  "groupType": "String",
  "modifiedProperties": [{"@odata.type": "microsoft.graph.modifiedProperty"}]
}
```
