<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/education/guide/2-baseline/setup/baseline-setup-user-provisioning -->
<!-- Sitemap-Last-Modified: 2026-04-28 -->

# Step 5: Provision users

After you synced your on-premises Active Directory, you're ready to provision users in your Microsoft Office 365 Education tenant.

## Types of users in a workforce tenant

A workforce tenant is designed for managing internal employees and any partner that needs to interact with the tenant. The following are the types of users you can have in your tenant:

- **Internal member:** These users are most likely full-time employees in your organization.
- **Internal guest:** These users have an account in your tenant, but have guest-level privileges. It's possible they were created within your tenant prior to the availability of B2B collaboration.
- **External member:** These users authenticate using an external account, but have member access to your tenant. These types of users are common in [multitenant organizations.](https://learn.microsoft.com/en-us/entra/identity/multi-tenant-organizations/overview#what-is-the-multitenant-organization-scenario)
- **External guest:** These users are true guests of your tenant who authenticate using an external method and who have guest-level privileges.

For more information about the differences between internal and external guests and members, see [B2B collaboration properties.](https://learn.microsoft.com/en-us/entra/external-id/user-properties)

Note

For education scenarios:

- Faculty, Staff, Teachers, and Students normally are classified as Internal members.
- If you have a multitenant architecture, you might have members that are external members from the other tenants.
- External guest or external members could be consultants or any individual that might need access but limited rights and license designation.

## User provisioning

There are multiple ways to provisioning users in your tenant. The following options are available:

- [Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/assign-user-or-group-access-portal?pivots=portal) management interface
- Via [Microsoft Graph API](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/application-provisioning-configuration-api)
- [Microsoft Entra ID sync with Active Directory](https://learn.microsoft.com/en-us/entra/identity/hybrid/cloud-sync/how-to-configure-entra-to-active-directory) \(on-premises\)

Note

For education scenarios:

- Education organizations can also use School Data Sync \(SDS\) via API \(Powerschool\) or \(.csv\) file connection to a qualified Student Information Services \(SIS\)
- Group-based user assignments require Microsoft Entra ID P1 or P2 edition.

## Next steps

Now you're ready to sync your Student Information System \(SIS\) using School Data Sync \(SDS\).

[Next: Sync your SIS using SDS >](https://learn.microsoft.com/en-us/microsoft-365/education/guide/2-baseline/setup/baseline-setup-school-data-sync)
