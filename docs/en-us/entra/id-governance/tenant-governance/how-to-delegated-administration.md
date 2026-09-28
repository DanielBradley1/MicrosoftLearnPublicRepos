<!-- Source: https://learn.microsoft.com/en-us/entra/id-governance/tenant-governance/how-to-delegated-administration -->
<!-- Sitemap-Last-Modified: 2026-07-29 -->

# Use cross-tenant delegated administration

This article describes how to sign in to a governed tenant as a delegated administrator and manage delegated administration roles.

Cross-tenant delegated administration enables administrators in a governing tenant to sign in to and manage governed tenants using their governing tenant credentials. This capability doesn't require a local or B2B account in each governed tenant. It uses granular delegated admin privileges \(GDAP\) technology to provide centralized, least-privileged, cross-tenant access.

## Prerequisites

- An active governance relationship between the governing tenant and the governed tenant, with delegated administration configured in the governance policy template. For more information, see [GDAP supported workloads](https://learn.microsoft.com/en-us/partner-center/customers/gdap-supported-workloads).
- The administrator must belong to a security group in the governing tenant that the governance relationship specifies.

## Sign in to a governed tenant as a delegated administrator

After the governance relationship is active and GDAP role assignments are in place, members of the configured security group can sign in to the governed tenant. Confirm that your account is a member of a security group in the governing tenant that's assigned roles in the governance policy template.

You can sign in to a governed tenant in two ways:

- From the **Governed tenants** page in the Microsoft Entra admin center.
- By opening a supported admin portal URL directly.

### Sign in from the Microsoft Entra admin center

Use the **Governed tenants** page to sign in to a governed tenant and choose which admin portal to open.

1. In the governing tenant, go to the **Governed tenants** page in the [Microsoft Entra admin center](https://entra.microsoft.com).
2. Select the governed tenant that you want to sign in to.
3. On the command bar, select **Sign in to tenant**. A side pane opens that shows:

   - Whether you can sign in to the governed tenant.
   - The roles that you'll have in the governed tenant.

4. If your group membership is configured with Privileged Identity Management \(PIM\) and your membership is eligible, the side pane shows an **Activate** button. Select **Activate** to activate your eligible group membership before you sign in.
5. In the side pane, select the admin portal that you want to open. A new tab opens and prompts you to authenticate.
6. Sign in with your governing tenant credentials to access the governed tenant.

Note

If there are multiple active relationships between the same pair of tenants, the side pane might not show all the roles that you get when you sign in to the tenant. The side pane shows only the roles that are in the scope of the selected relationship.

### Sign in by using an admin portal URL

1. Open a supported admin portal URL and append the domain or tenant ID of the governed tenant. For a list of supported portals and workloads, see [GDAP supported workloads](https://learn.microsoft.com/en-us/partner-center/customers/gdap-supported-workloads). For example:

   `https://entra.microsoft.com/{governed-tenant-domain-or-id}`
2. Sign in with your governing tenant credentials.
3. After successful sign-in, perform administrative tasks in the governed tenant based on the roles assigned to your security group.

   Important

   Your user information appears different from a regular user:

   - Your display name appears as `user_{your user object ID in the governing tenant without dashes}`.
   - Sign-in logs and audit logs in the governed tenant show your display name as `{Governing tenant name} Technician`.

## Update delegated administration roles

To add or change the roles available to delegated administrators, update the governance policy template and send a new governance request.

1. In the governing tenant, update the governance policy template to add or modify the Microsoft Entra built-in roles and security group assignments.

   Note

   Updating the template increments its version number by one.
2. Send a new governance request to the governed tenant using the updated policy template.
3. An administrator in the governed tenant reviews and accepts the request to apply the updated roles.

## Related content

- [Monitor governing tenant admin activity](https://learn.microsoft.com/en-us/entra/id-governance/tenant-governance/how-to-monitor-governing-activity)
- [Set up a governance relationship](https://learn.microsoft.com/en-us/entra/id-governance/tenant-governance/how-to-set-up-governance-relationship)
- [Governance policy templates](https://learn.microsoft.com/en-us/entra/id-governance/tenant-governance/governance-policy-templates)
- [Terminate a governance relationship](https://learn.microsoft.com/en-us/entra/id-governance/tenant-governance/how-to-terminate-governance-relationship)
