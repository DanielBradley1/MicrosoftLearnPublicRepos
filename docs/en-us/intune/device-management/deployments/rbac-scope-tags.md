<!-- Source: https://learn.microsoft.com/en-us/intune/device-management/deployments/rbac-scope-tags -->
<!-- Sitemap-Last-Modified: 2026-09-21 -->

# Permissions, scope tags, and approvals for deployments in Microsoft Intune

Note

This feature is in public preview. For more information, see [Public preview in Microsoft Intune](https://learn.microsoft.com/en-us/intune/fundamentals/public-preview).

This article describes role-based access control \(RBAC\) permissions, scope tag behavior, and Multi Admin Approval for deployment plans and deployments. For general information about Intune RBAC, see [Role-based access control with Microsoft Intune](https://learn.microsoft.com/en-us/intune/fundamentals/role-based-access-control/overview).

## Deployment plan permissions

The following permissions are available for deployment plans:

| Permission | Action | Description |
| --- | --- | --- |
| Deployment plan | Create \(C\) | Create a plan |
| Deployment plan | Read \(R\) | Read a plan |
| Deployment plan | Update \(U\) | Edit or modify a plan |
| Deployment plan | Delete \(D\) | Delete a plan |

Intune built-in roles include deployment plan permissions that align with each role's management category, such as device configurations or mobile apps, and its supported actions. For example, the **Policy and Profile Manager** role has CRUD permissions for device configurations, so it also has CRUD permissions for deployment plans.

Deployment plan permissions are included in the following built-in roles:

| Built-in role | Deployment plan permissions |
| --- | --- |
| Application Manager | Create, Read, Update, Delete |
| Read Only Operator | Read |
| Endpoint Security Manager | Create, Read, Update, Delete |
| Help Desk Operator | Read |
| Policy and Profile Manager | Create, Read, Update, Delete |
| School Administrator | Create, Read, Update, Delete |

## Deployment permissions

Deployments don't have a dedicated permission. Permissions are based on the selected payload's category.

| Action | Payload type | Required permission |
| --- | --- | --- |
| Create a deployment | Device configuration | Read and Assign permissions for the **Device configurations** category |
| Create a deployment | Apps | Read and Assign permissions for the **Mobile apps** category |
| View a deployment | Device configuration | Read permission for the **Device configurations** category |
| View a deployment | Apps | Read permission for the **Mobile apps** category |

## Scope tags

Scope tags control object visibility in Intune. Administrators can only view objects that have scope tags within their assigned scope.

| Action | Scope tags enforced | Behavior |
| --- | --- | --- |
| View deployments in the **Deployments** list | Yes | An administrator can only see deployments whose payload is within the administrator's scope. |
| View plans in the **Deployment plans** list | Yes | An administrator can only see plans within the administrator's scope. |
| Select a payload when creating a deployment | Yes | The payload list only displays payloads within the administrator's scope. |

You can assign scope tags directly to deployment plans. You can't assign scope tags to deployments. Because apps and policies support scope tags, the selected payload is the visibility control plane for its deployment.

For general information, see [Use scope tags for distributed IT](https://learn.microsoft.com/en-us/intune/fundamentals/role-based-access-control/scope-tags).

## Multi Admin Approval

Intune deployments support Multi Admin Approval \(MAA\). When an MAA access policy is configured for a policy type that deployments support, Intune enforces the approval flow. For example, if you create a deployment for a Windows app and an access policy protects the **App Windows** platform, the deployment requires approval.

The following deployment actions trigger an MAA approval flow:

- Create
- Resume
- Cancel
- Delete

Note

An MAA approver needs Read permission for the payload to access the deployment properties link in the approval request.

When a deployment creation request requires approval, the deployment doesn't appear in the **Deployments** list until the approval is complete.

For more information, see [Use Multi Admin Approval in Intune](https://learn.microsoft.com/en-us/intune/fundamentals/role-based-access-control/multi-admin-approval).

## Related articles

- [Deployment plans and deployments overview](https://learn.microsoft.com/en-us/intune/device-management/deployments/overview)
- [Create a deployment plan in Microsoft Intune](https://learn.microsoft.com/en-us/intune/device-management/deployments/create-deployment-plan)
- [Create and manage a deployment in Microsoft Intune](https://learn.microsoft.com/en-us/intune/device-management/deployments/create-deployment)
- [Known issues with deployments \(preview\)](https://learn.microsoft.com/en-us/intune/device-management/deployments/known-issues)
- [Create a custom role in Intune](https://learn.microsoft.com/en-us/intune/fundamentals/role-based-access-control/create-custom-role)
