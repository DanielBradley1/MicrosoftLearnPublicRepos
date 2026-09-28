<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/invalidlicensealertincident?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-09-20 -->

# invalidLicenseAlertIncident resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the details of an alert incident that is triggered if the current tenant doesn't have a valid Microsoft Entra ID P2 license.

Inherits from [unifiedRoleManagementAlertIncident](https://learn.microsoft.com/en-us/graph/api/resources/unifiedrolemanagementalertincident?view=graph-rest-beta).

## Methods

None.

For the list of API operations for managing this resource type, see the [unifiedRoleManagementAlertIncident](https://learn.microsoft.com/en-us/graph/api/resources/unifiedrolemanagementalertincident?view=graph-rest-beta) resource type.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The identifier for the alert incident. For example, it could be a role assignment ID if the incident represents a role assignment. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). Supports `$filter` \(`eq`, `ne`\). |
| tenantLicenseStatus | String | Status of the tenant's Microsoft Entra ID P2 license. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.invalidLicenseAlertIncident",
  "id": "String (identifier)",
  "tenantLicenseStatus": "String"
}
```
