<!-- Source: https://learn.microsoft.com/en-us/defender-xdr/governance-relationships -->
<!-- Sitemap-Last-Modified: 2026-09-10 -->

# Configure delegated access with governance relationships for multitenant organizations \(preview\)

This article explains how to configure governance relationships for multitenant organizations and managed security service providers \(MSSPs\) to manage delegated access to customer tenants through the Microsoft Defender portal.

Important

This feature is currently in preview.

## Overview

A governance relationship is a directional connection between two Microsoft Entra tenants that enables a governing tenant \(the home tenant that manages access\) to manage security operations across multiple customer tenants \(the tenants that grant delegated access\) with fine-grained role assignments. This capability supports multitenant organizations \(MTOs\) and managed security service providers \(MSSPs\) that need to provide security services across multiple Microsoft Entra tenants.

Governance relationships for Microsoft Defender use the same model as [Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/id-governance/tenant-governance/governance-relationships) for delegating administrative access, but extended to support [Microsoft Defender XDR](https://learn.microsoft.com/en-us/defender-xdr/microsoft-365-defender) \(cross-domain threat detection and response\) workloads. By configuring governance relationships for Microsoft Defender, you can assign specific security roles to groups in the governing tenant, allowing them to manage security incidents, alerts, and configurations in the governed tenant without granting full administrative access.

Administrators continue to use their accounts in the governing tenant. Tenant Governance doesn't create local administrator accounts or Microsoft Entra B2B guest accounts in the governed tenant. Instead, security groups selected in the governance policy template are represented in the governed tenant as remote tenant groups. You can automate governance relationships and templates by using the [Tenant Governance APIs in Microsoft Graph](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-tenantgovernance-overview).

### Key concepts

The following terms are used throughout this article:

- **Governing tenant**: The home tenant that manages access to other tenants \(also called *home tenant* or *managing tenant*\)
- **Governed tenant**: The customer tenant that grants access to the governing tenant \(also called *target tenant* or *managed tenant*\)
- **Governance relationship**: directional connection between two Microsoft Entra tenants. One tenant acts as the *governing* tenant, and the other acts as the *governed* tenant.
- **CSP**: Cloud Solution Provider - Microsoft partners who sell cloud services

## Prerequisites

Before you configure delegated access, ensure you meet the following requirements:

Licenses:

- Both tenants require at least one Microsoft Entra ID P1 license.
- Both tenants require at least one Microsoft 365 E5 license or Microsoft Sentinel enabled in Microsoft Defender.

Permissions:

- A user with the [Tenant Governance Relationship Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#tenant-governance-relationship-administrator) role in the governing tenant.
- To send an invitation from the governed tenant, the user must have the [Tenant Governance Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#tenant-governance-administrator) role.
- To assign permissions to a remote tenant group, the user must have the [User Access Administrator](https://learn.microsoft.com/en-us/azure/role-based-access-control/built-in-roles/privileged#user-access-administrator) role in Azure RBAC and at least a [User Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#user-administrator) role in Entra RBAC.

## Enable tenant governance settings

Before you can configure delegated access, you must enable the governed tenant to receive governance invitations. The **Enable invitations** setting is disabled by default.

In the governed tenant in the Microsoft Defender portal, go to **System** > **Permissions** > **Delegated Access**, and turn on the **Enable invitations** toggle.

![Screenshot showing governance invitations enabled in tenant settings.](https://learn.microsoft.com/en-us/defender-xdr/media/governance-relationships/enable-invitations.png)

## Set up delegated access

The tenant governance setup process involves three steps: the governed tenant sends an invitation, the governing tenant creates and sends an access request, and the governed tenant approves the request.

### Step 1: Send invitation from governed tenant

The governed tenant initiates the relationship by sending an invitation to the governing tenant.

1. In the governed tenant, sign in to the Microsoft Defender portal.
2. Navigate to **System** > **Permissions** > **Delegated Access**.
3. Select **Send invitation**.

   ![Screenshot of delegated access interface with send invitation option.](https://learn.microsoft.com/en-us/defender-xdr/media/governance-relationships/send-invitation.png)
4. Enter the tenant ID of the governing tenant that you want to invite.

   ![Screenshot showing where to enter the tenant ID for the invitation.](https://learn.microsoft.com/en-us/defender-xdr/media/governance-relationships/tenant-id.png)
5. Select **Send** to send the invitation.

### Step 2: Create and send access request from governing tenant

After the governing tenant receives the invitation, it creates a relationship template that defines delegated access permissions.

1. In the governing tenant, sign in to the Microsoft Defender MTO portal.
2. Navigate to **System** > **Delegated Access**.
3. Select **Create access template**.

   ![Screenshot of create access template interface.](https://learn.microsoft.com/en-us/defender-xdr/media/governance-relationships/access-template.png)
4. Define the access template with the following information:

   - **Template name**: A descriptive name for this access template
   - **Microsoft Entra built-in roles**: Select one or more roles to assign
   - **Security groups**: Select security groups from your governing tenant that will receive the assigned roles


   [![Screenshot showing fields for defining the access template.](https://learn.microsoft.com/en-us/defender-xdr/media/governance-relationships/define-access-template.png)](https://learn.microsoft.com/en-us/defender-xdr/media/governance-relationships/define-access-template.png#lightbox)

5. Select **Send relationship request**.

   ![Screenshot of send relationship request option.](https://learn.microsoft.com/en-us/defender-xdr/media/governance-relationships/send-request.png)
6. Select the governed tenant that invited you, then select **Submit**.

   ![Screenshot showing the governance relationships request submission.](https://learn.microsoft.com/en-us/defender-xdr/media/governance-relationships/submit-request.png)

### Step 3: Approve access request in governed tenant

The governed tenant administrator reviews and approves the delegated access request.

1. In the governed tenant, sign in to the Microsoft Defender portal.
2. Navigate to **System** > **Permissions** > **Microsoft XDR permissions**.
3. Review the pending access request and select **Approve** or **Reject**.

   ![Screenshot showing options to approve or reject the access request.](https://learn.microsoft.com/en-us/defender-xdr/media/governance-relationships/approve-reject.png)
4. After approval, you'll see a confirmation message.

After the approval is complete, users in the specified security groups receive permissions in the governed tenant based on the defined roles.

## Configure tenant governance permissions for Microsoft Sentinel

Security groups used in the relationship template are synchronized to the governed tenant as "remote tenant groups." You can assign these groups to Microsoft Sentinel roles in the governed tenant to enable multitenant management capabilities. You can assign these groups to Azure Resource Manager \(ARM\) resources to enable Microsoft Sentinel management capabilities.

The Microsoft Sentinel Azure RBAC assignments described in this section grant management-plane access to the selected resources. They don't automatically grant data-plane access, such as permission to read Azure Storage blob data or Azure Key Vault secrets. Assign any required data-plane roles separately and follow least-privilege principles.

Assigning Microsoft Sentinel roles enables multitenant management features including:

- Alert and incident management
- Threat intelligence
- Hunting
- Content distribution
- Direct management through the Defender portal

### Assign permissions to resource group

Before you assign permissions, ensure you have the [User Access Administrator](https://learn.microsoft.com/en-us/azure/role-based-access-control/built-in-roles/privileged#user-access-administrator) role in Azure RBAC and at least the [User Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#user-administrator) role in Entra RBAC.

Follow these steps to grant Microsoft Sentinel permissions to your delegated access groups.

1. In the governed tenant, sign in to the [Azure portal](https://portal.azure.com).
2. Navigate to your resource group.
3. Select **Access Control \(IAM\)**.
4. Select **Add** > **Add role assignment**.
5. Select the Microsoft Sentinel role you want to assign \(for example, Microsoft Sentinel Contributor\).

   [![Screenshot of Access Control panel showing role assignments.](https://learn.microsoft.com/en-us/defender-xdr/media/governance-relationships/access-control.png)](https://learn.microsoft.com/en-us/defender-xdr/media/governance-relationships/access-control.png#lightbox)
6. On the **Members** tab, under **Assign access to**, select **Remote tenant group**.
7. Select the synchronized security groups from the governing tenant.

   [![Screenshot showing role assignment to a remote tenant group.](https://learn.microsoft.com/en-us/defender-xdr/media/governance-relationships/add-role-assignment.png)](https://learn.microsoft.com/en-us/defender-xdr/media/governance-relationships/add-role-assignment.png#lightbox)
8. Select **Review + assign** to complete the assignment.

## Troubleshooting

Use the following guidance to resolve common issues when configuring governance relationships.

### Security group not displayed when creating a template

**Symptom**: Your security group doesn't appear in the list when creating a relationship template.

**Cause**: Only security groups that meet specific criteria are supported for governance relationships delegation.

**Resolution**: Ensure your security group meets the following requirements:

- SecurityEnabled property is set to true
- IsAssignableToRole property is set to true
- Not a Microsoft 365 group \(unified group\)

Security groups that don't meet these criteria aren't supported for governance relationships delegation.

## Related content

- [Microsoft Entra governance relationships](https://learn.microsoft.com/en-us/entra/id-governance/tenant-governance/governance-relationships)
- [MSSP portal access](https://learn.microsoft.com/en-us/defender-xdr/mssp-access)
