<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/nomfaonroleactivationalertincident?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-09-20 -->

# noMfaOnRoleActivationAlertIncident resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the details of an alert incident that is triggered if roles don't require multi-factor authentication for activation.

Inherits from [unifiedRoleManagementAlertIncident](https://learn.microsoft.com/en-us/graph/api/resources/unifiedrolemanagementalertincident?view=graph-rest-beta).

## Methods

None.

For the list of API operations for managing this resource type, see the [unifiedRoleManagementAlertIncident](https://learn.microsoft.com/en-us/graph/api/resources/unifiedrolemanagementalertincident?view=graph-rest-beta) resource type.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The identifier for an alert incident. For example, it could be a role assignment ID if the incident represents a role assignment. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). Supports `$filter` \(`eq`, `ne`\). |
| roleDisplayName | String | The name of the Microsoft Entra ID [directory role](https://learn.microsoft.com/en-us/graph/api/resources/unifiedroledefinition?view=graph-rest-beta). |
| roleTemplateId | String | The globally unique identifier for a [directory role](https://learn.microsoft.com/en-us/graph/api/resources/unifiedroledefinition?view=graph-rest-beta). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.noMfaOnRoleActivationAlertIncident",
  "id": "String (identifier)",
  "roleTemplateId": "String",
  "roleDisplayName": "String"
}
```
