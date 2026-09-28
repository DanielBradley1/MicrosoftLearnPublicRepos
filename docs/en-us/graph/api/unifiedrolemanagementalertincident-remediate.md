<!-- Source: https://learn.microsoft.com/en-us/graph/api/unifiedrolemanagementalertincident-remediate?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-11-08 -->

# unifiedRoleManagementAlertIncident: remediate

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Remediate or mitigate an incident of an alert. Run this action to fix an incident for a remediable alert, automatically applying the recommended **mitigationSteps**.

The alert incident can be one of the following types that are derived from the [unifiedRoleManagementAlertIncident](https://learn.microsoft.com/en-us/graph/api/resources/unifiedrolemanagementalertincident?view=graph-rest-beta) object:

- [invalidLicenseAlertIncident](https://learn.microsoft.com/en-us/graph/api/resources/invalidlicensealertincident?view=graph-rest-beta)
- [noMfaOnRoleActivationAlertIncident](https://learn.microsoft.com/en-us/graph/api/resources/nomfaonroleactivationalertincident?view=graph-rest-beta)
- [redundantAssignmentAlertIncident](https://learn.microsoft.com/en-us/graph/api/resources/redundantassignmentalertincident?view=graph-rest-beta)
- [rolesAssignedOutsidePrivilegedIdentityManagementAlertConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/rolesassignedoutsideprivilegedidentitymanagementalertconfiguration?view=graph-rest-beta)
- [sequentialActivationRenewalsAlertIncident](https://learn.microsoft.com/en-us/graph/api/resources/sequentialactivationrenewalsalertincident?view=graph-rest-beta)
- [staleSignInAlertIncident](https://learn.microsoft.com/en-us/graph/api/resources/stalesigninalertincident?view=graph-rest-beta)
- [tooManyGlobalAdminsAssignedToTenantAlertIncident](https://learn.microsoft.com/en-us/graph/api/resources/toomanyglobaladminsassignedtotenantalertincident?view=graph-rest-beta)

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | RoleManagementAlert.ReadWrite.Directory | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | RoleManagementAlert.ReadWrite.Directory | Not available. |

Important

For delegated access using work or school accounts, the signed-in user must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role that grants the permissions required for this operation. *Privileged Role Administrator* is the least privileged role supported for this operation.

## HTTP request

```http
POST /identityGovernance/roleManagementAlerts/alerts/{unifiedRoleManagementAlertId}/alertIncidents/{unifiedRoleManagementAlertIncidentId}/remediate
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this action returns a `200 OK` response code. Calling this API for an incident that has an alert definition with **isRemediatable** set to `false` returns in a `400 Bad Request` error response.

## Examples

### Request

The following example shows a request.

```http
POST https://graph.microsoft.com/beta/beta/identityGovernance/roleManagementAlerts/alerts/DirectoryRole_67b47f38-0f0b-4e62-a3be-859140c2061f_TooManyGlobalAdminsAssignedToTenantAlert/incident/0645231d-16ba-4ebf-851a-0875df4052bd/remediate
```

### Response

The following example shows the response.

```http
HTTP/1.1 200 OK
```
