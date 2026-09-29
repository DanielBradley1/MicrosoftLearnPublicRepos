<!-- Source: https://learn.microsoft.com/en-us/defender-xdr/mto-requirements -->
<!-- Sitemap-Last-Modified: 2026-09-10 -->

# Set up Microsoft Defender multitenant management

This article describes the steps you need to take to start using multitenant management for Microsoft Defender XDR and Microsoft Sentinel in the Defender portal.

1. [Review the requirements](#review-the-requirements)
2. [Verify your tenant access](#verify-your-tenant-access)
3. [Set up Microsoft Defender multitenant management](#set-up-multitenant-management)

Note

- In multitenant management, interactions between the multitenant user and the managed tenants could involve accessing data and managing configurations. The ability to undertake these actions is determined by the permissions a managed tenant has granted the multitenant user.
- [Data privacy](https://learn.microsoft.com/en-us/defender-xdr/data-privacy), [role-based access control \(RBAC\)](https://learn.microsoft.com/en-us/defender-xdr/m365d-permissions) and [Licensing](https://learn.microsoft.com/en-us/defender-xdr/prerequisites#licensing-requirements) are respected by Microsoft Defender multi-tenant management.

## Review the requirements

The following table lists the basic requirements you need to use multitenant management for Microsoft Defender XDR and Microsoft Sentinel in the Defender portal.

| Requirement | Description |
| :--- | :--- |
| Microsoft Defender XDR prerequisites | Verify you meet the [Microsoft Defender XDR prerequisites](https://learn.microsoft.com/en-us/defender-xdr/prerequisites) |
| Microsoft Defender XDR for US Government customers | Check if you have the following applicable [licensing requirements](https://learn.microsoft.com/en-us/defender-xdr/usgov#licensing-requirements) |
| Multitenant access | To view and manage the data you have access to in multitenant management, you need to ensure you have the necessary access.  <br>  <br>**For Microsoft Defender data**, you must have either:  <br>- [Granular delegated admin privileges \(GDAP\)](https://learn.microsoft.com/en-us/partner-center/gdap-introduction)  <br>- [Microsoft Entra B2B authentication](https://learn.microsoft.com/en-us/azure/active-directory/external-identities/what-is-b2b)  <br>  <br>**To run cross-tenant queries on Microsoft Sentinel data**, you must set up [Azure Lighthouse](https://learn.microsoft.com/en-us/azure/lighthouse/overview). For example, to run cross-workspace queries with the `workspace()` operator in advanced hunting and analytics rules. |
| Permissions | Users must be assigned the correct roles and permissions at the individual tenant level, in order to view and manage the associated data in multitenant management. To learn more, see:  <br>  <br>- [Manage access to Microsoft Defender XDR with Microsoft Entra global roles](https://learn.microsoft.com/en-us/defender-xdr/m365d-permissions)  <br>- [Custom roles in role-based access control for Microsoft Defender XDR](https://learn.microsoft.com/en-us/defender-xdr/custom-roles)  <br>  <br>To learn how to grant permissions for multiple users at scale, see [What is entitlement management](https://learn.microsoft.com/en-us/azure/active-directory/governance/entitlement-management-overview). |
| Security information and event management \(SIEM\) data \(Optional\) | To include SIEM data with the extended detection and response \(XDR\) data, one or more tenants must include a Microsoft Sentinel workspace onboarded to Microsoft Defender. For more information, see [Connect Microsoft Sentinel to Microsoft Defender XDR](https://learn.microsoft.com/en-us/azure/sentinel/microsoft-sentinel-onboard).  <br>  <br>The Defender portal allows you to connect to one primary workspace and multiple secondary workspaces for Microsoft Sentinel. For more information, see [Multiple Microsoft Sentinel workspaces in the Defender portal](https://go.microsoft.com/fwlink/p/?linkid=2310579).  <br>  <br>Access to Microsoft Sentinel data is available through [Microsoft Entra B2B authentication](https://learn.microsoft.com/en-us/azure/active-directory/external-identities/what-is-b2b). Microsoft Sentinel doesn't support [granular delegated admin privileges \(GDAP\)](https://learn.microsoft.com/en-us/partner-center/gdap-introduction) at this time. |

We recommend that you set up [multifactor authentication trust](https://learn.microsoft.com/en-us/azure/active-directory/external-identities/authentication-conditional-access) for each tenant to avoid missing data in Microsoft Defender multitenant management.

## Verify your tenant access

In order to view and manage the data you have access to in Microsoft Defender multitenant management, you need to ensure you have the necessary permissions. For each tenant you want to view and manage, you need to either:

- [Verify your tenant access with Microsoft Entra B2B](#verify-your-tenant-access-with-microsoft-entra-b2b)
- [Verify your tenant access with GDAP](#verify-your-tenant-access-with-gdap)

### Verify your tenant access with Microsoft Entra B2B

Perform the following steps to verify your tenant access with Microsoft Entra B2B:

1. Go to [My account](https://myaccount.microsoft.com/organizations).
2. Under **Organizations > Other organizations you collaborate with** see the list of organizations you have guest access to.

   [![Screenshot of organizations in the myaccount portal](https://learn.microsoft.com/en-us/defender-xdr/media/mto-requirements/mto-myaccount.png)](https://learn.microsoft.com/en-us/defender-xdr/media/mto-requirements/mto-myaccount.png#lightbox)
3. Verify all the tenants you plan to manage appear in the list.
4. For each tenant, go to the [Microsoft Defender portal](https://security.microsoft.com/?tid=tenant_id) and sign in to validate you can successfully access the tenant.

### Verify your tenant access with GDAP

GDAP is not supported for Microsoft Sentinel data, and provides access to Defender data only.

1. Go to the [Microsoft Partner Center](https://partner.microsoft.com/commerce/granularadminaccess/list).
2. Under **Customers** you can find the list of organizations you have guest access to.
3. Verify all the tenants you plan to manage appear in the list.
4. For each tenant, go to the [Microsoft Defender portal](https://security.microsoft.com/?tid=tenant_id) and sign in to validate you can successfully access the tenant.

## Set up multitenant management

The first time you use Microsoft Defender multitenant management, you need setup the tenants you want to view and manage. To get started:

1. Sign in to [Microsoft Defender multitenant management](https://mto.security.microsoft.com/)
2. Select **Add tenants**.

   [![Screenshot of the Microsoft Defender multi-tenant portal setup screen](https://learn.microsoft.com/en-us/defender-xdr/media/mto-requirements/mto-add-tenants.png)](https://learn.microsoft.com/en-us/defender-xdr/media/mto-requirements/mto-add-tenants.png#lightbox)
3. Choose the tenants you want to manage and select **Add**

Note

The Microsoft Defender multitenant view currently has a limit of 100 target tenants.

The features available in multitenant management now appear on the navigation bar and you're ready to view and manage security data across all your tenants.

[![Screenshot of Microsoft Defender multitenant management.](https://learn.microsoft.com/en-us/defender-xdr/media/mto-requirements/mto-tenant-selection.png)](https://learn.microsoft.com/en-us/defender-xdr/media/mto-requirements/mto-tenant-selection.png#lightbox)

## Related content

- [View and manage incidents and alerts in Microsoft Defender multitenant management](https://learn.microsoft.com/en-us/defender-xdr/mto-incidents-alerts)
- [Advanced hunting in Microsoft Defender multitenant management](https://learn.microsoft.com/en-us/defender-xdr/mto-advanced-hunting)
- [Devices in multitenant management](https://learn.microsoft.com/en-us/defender-xdr/mto-tenant-devices)
- [Vulnerability management in multi-tenant management](https://learn.microsoft.com/en-us/defender-xdr/mto-dashboard)
- [Manage tenants with Microsoft Defender multitenant management](https://learn.microsoft.com/en-us/defender-xdr/mto-tenants)
