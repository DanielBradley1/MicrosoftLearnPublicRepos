<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/unifiedrolemanagementalertincident?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-22 -->

# unifiedRoleManagementAlertIncident resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

An abstract type that represents the details of an incident as part of a security [alert](https://learn.microsoft.com/en-us/graph/api/resources/unifiedrolemanagementalert?view=graph-rest-beta) in [Privileged Identity Management \(PIM\) for Microsoft Entra roles](https://learn.microsoft.com/en-us/graph/api/resources/privilegedidentitymanagementv3-overview?view=graph-rest-beta).

This abstract type is inherited by the following derived types:

- [invalidLicenseAlertIncident](https://learn.microsoft.com/en-us/graph/api/resources/invalidlicensealertincident?view=graph-rest-beta)
- [noMfaOnRoleActivationAlertIncident](https://learn.microsoft.com/en-us/graph/api/resources/nomfaonroleactivationalertincident?view=graph-rest-beta)
- [redundantAssignmentAlertIncident](https://learn.microsoft.com/en-us/graph/api/resources/redundantassignmentalertincident?view=graph-rest-beta)
- [rolesAssignedOutsidePrivilegedIdentityManagementAlertIncident](https://learn.microsoft.com/en-us/graph/api/resources/rolesassignedoutsideprivilegedidentitymanagementalertincident?view=graph-rest-beta)
- [sequentialActivationRenewalsAlertIncident](https://learn.microsoft.com/en-us/graph/api/resources/sequentialactivationrenewalsalertincident?view=graph-rest-beta)
- [staleSignInAlertIncident](https://learn.microsoft.com/en-us/graph/api/resources/stalesigninalertincident?view=graph-rest-beta)
- [tooManyGlobalAdminsAssignedToTenantAlertIncident](https://learn.microsoft.com/en-us/graph/api/resources/toomanyglobaladminsassignedtotenantalertincident?view=graph-rest-beta)

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta).

For more information about working with security alerts for Microsoft Entra roles using PIM APIs, see [Manage security alerts for Microsoft Entra roles using PIM APIs in Microsoft Graph](https://learn.microsoft.com/en-us/graph/how-to-pim-alerts).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/unifiedrolemanagementalert-list-alertincidents?view=graph-rest-beta) | [unifiedRoleManagementAlertIncident](https://learn.microsoft.com/en-us/graph/api/resources/unifiedrolemanagementalertincident?view=graph-rest-beta) collection | Get a list of the [unifiedRoleManagementAlertIncident](https://learn.microsoft.com/en-us/graph/api/resources/unifiedrolemanagementalertincident?view=graph-rest-beta) objects and their properties. |
| [Get](https://learn.microsoft.com/en-us/graph/api/unifiedrolemanagementalertincident-get?view=graph-rest-beta) | [unifiedRoleManagementAlertIncident](https://learn.microsoft.com/en-us/graph/api/resources/unifiedrolemanagementalertincident?view=graph-rest-beta) | Read the properties and relationships of an [unifiedRoleManagementAlertIncident](https://learn.microsoft.com/en-us/graph/api/resources/unifiedrolemanagementalertincident?view=graph-rest-beta) object. |
| [Remediate](https://learn.microsoft.com/en-us/graph/api/unifiedrolemanagementalertincident-remediate?view=graph-rest-beta) | None | Remediate or mitigate an incident of an alert. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The identifier of the alert incident. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). Supports `$filter` \(`eq`, `ne`\). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.unifiedRoleManagementAlertIncident",
  "id": "String (identifier)"
}
```

## Related content

- [Manage security alerts for Microsoft Entra roles using PIM APIs in Microsoft Graph](https://learn.microsoft.com/en-us/graph/how-to-pim-alerts).
