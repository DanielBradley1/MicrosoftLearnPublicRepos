<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/unifiedrolemanagementalertdefinition?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-06-12 -->

# unifiedRoleManagementAlertDefinition resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the alert definition that contains the description, impact, and measures to mitigate or prevent a security [alert](https://learn.microsoft.com/en-us/graph/api/resources/unifiedrolemanagementalert?view=graph-rest-beta) from being triggered in your tenant in [Privileged Identity Management \(PIM\) for Microsoft Entra roles](https://learn.microsoft.com/en-us/graph/api/resources/privilegedidentitymanagementv3-overview?view=graph-rest-beta).

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/rolemanagementalert-list-alertdefinitions?view=graph-rest-beta) | [unifiedRoleManagementAlertDefinition](https://learn.microsoft.com/en-us/graph/api/resources/unifiedrolemanagementalertdefinition?view=graph-rest-beta) collection | Get a list of the [unifiedRoleManagementAlertDefinition](https://learn.microsoft.com/en-us/graph/api/resources/unifiedrolemanagementalertdefinition?view=graph-rest-beta) objects and their properties. |
| [Get](https://learn.microsoft.com/en-us/graph/api/unifiedrolemanagementalertdefinition-get?view=graph-rest-beta) | [unifiedRoleManagementAlertDefinition](https://learn.microsoft.com/en-us/graph/api/resources/unifiedrolemanagementalertdefinition?view=graph-rest-beta) | Read the properties and relationships of an [unifiedRoleManagementAlertDefinition](https://learn.microsoft.com/en-us/graph/api/resources/unifiedrolemanagementalertdefinition?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| description | String | The description of the alert. |
| displayName | String | The friendly display name that renders in Privileged Identity Management \(PIM\) alerts in the Microsoft Entra admin center. |
| howToPrevent | String | Long-form text that indicates the ways to prevent the alert from being triggered in your tenant. |
| id | String | The identifier of the alert definition. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). |
| isConfigurable | Boolean | `true` if the alert configuration can be customized in the tenant, and `false` otherwise. For example, the number and percentage thresholds of the 'There are too many global administrators' alert can be configured by users, while the 'This organization doesn't have Microsoft Entra ID P2' can't be configured, because the criteria are restricted. |
| isRemediatable | Boolean | `true` if the alert can be remediated, and `false` otherwise. |
| mitigationSteps | String | The methods to mitigate the alert when it's triggered in the tenant. For example, to mitigate the 'There are too many global administrators', you could remove redundant privileged role assignments. |
| scopeId | String | The identifier of the scope where the alert is related. `/` is the only supported one for the tenant. Supports `$filter` \(`eq`, `ne`\). |
| scopeType | String | The type of scope where the alert is created. `DirectoryRole` is the only currently supported scope type for Microsoft Entra roles. |
| securityImpact | String | Security impact of the alert. For example, it could be information leaks or unauthorized access. |
| severityLevel | alertSeverity | Severity level of the alert. The possible values are: `unknown`, `informational`, `low`, `medium`, `high`, `unknownFutureValue`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.unifiedRoleManagementAlertDefinition",
  "id": "String (identifier)",
  "displayName": "String",
  "scopeType": "String",
  "scopeId": "String",
  "description": "String",
  "severityLevel": "String",
  "securityImpact": "String",
  "mitigationSteps": "String",
  "howToPrevent": "String",
  "isRemediatable": "Boolean",
  "isConfigurable": "Boolean"
}
```
