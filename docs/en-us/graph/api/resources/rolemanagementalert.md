<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/rolemanagementalert?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-04-04 -->

# roleManagementAlert resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents an alert singleton that exposes security alerts, definitions, and configurations in PIM for Microsoft Entra roles.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta).

## Methods

None.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Unique identifier of an alert. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| alertConfigurations | [unifiedRoleManagementAlertConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/unifiedrolemanagementalertconfiguration?view=graph-rest-beta) collection | The various configurations of an alert for Microsoft Entra roles. The configurations are predefined and can't be created or deleted, but some of the configurations can be modified. |
| alertDefinitions | [unifiedRoleManagementAlertDefinition](https://learn.microsoft.com/en-us/graph/api/resources/unifiedrolemanagementalertdefinition?view=graph-rest-beta) collection | Defines an alert, its impact, and measures to mitigate or prevent it. |
| alerts | [unifiedRoleManagementAlert](https://learn.microsoft.com/en-us/graph/api/resources/unifiedrolemanagementalert?view=graph-rest-beta) collection | Represents the alert entity. |
| operations | [longRunningOperation](https://learn.microsoft.com/en-us/graph/api/resources/longrunningoperation?view=graph-rest-beta) collection | Represents operations on resources that take a long time to complete and can run in the background until completion. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.roleManagementAlert",
  "id": "String (identifier)"
}
```
