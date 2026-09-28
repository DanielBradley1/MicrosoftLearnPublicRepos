<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/enterprise/manage-multitenant-org-settings?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2026-07-06 -->

# Manage multitenant org settings

Management of various multitenant org settings can be found in the Microsoft admin center. Some settings may only be managed by owners in the MTO while others can be managed by each tenant themselves. Below are details regarding the available multitenant org settings in the Microsoft Admin center.

## Edit multitenant organization name

Only an owner tenant can edit the MTO name in an MTO.

Important

Microsoft recommends that you use roles with the fewest permissions. Using least-privileged accounts helps improve security for your organization. Global Administrator is a highly privileged role that should be limited to emergency scenarios when you can't use an existing role.

To edit the multitenant organization name for your MTO:

1. Sign in to the [Microsoft 365 admin center](https://admin.microsoft.com/) as a global administrator.
2. Expand **Settings** and select **Org settings**.
3. On the **Organization profile** tab, select **Multitenant collaboration**.
4. Select **Manage settings**.
5. Select **Edit** under **Multitenant organization name**.
6. Enter the new multitenant org name.
7. Select **Save changes**.

## Edit tenant role for multitenant org tenant

Only an owner tenant can change a tenant's role in an MTO.

Important

Microsoft recommends that you use roles with the fewest permissions. Using least-privileged accounts helps improve security for your organization. Global Administrator is a highly privileged role that should be limited to emergency scenarios when you can't use an existing role.

To edit the tenant role for a tenant in your MTO:

1. Sign in to the [Microsoft 365 admin center](https://admin.microsoft.com/) as a global administrator.
2. Expand **Settings** and select **Org settings**.
3. On the **Organization profile** tab, select **Multitenant collaboration**.
4. Select the associated tenant for which you would like to change their role.
5. Under Details select **Edit** under **Tenant role**.
6. Select either **Owner** or **Member**.
7. Select **Save changes**.

## Manage calendar sharing for tenants in your MTO

Calendar sharing allows users in each multitenant organization \(MTO\) tenant to view free/busy \(time only\) calendar availability information.

Note

Calendar sharing via Multitenant collaboration portal is currently not available in Microsoft 365 GCC, GCC High, DoD, or Microsoft 365 China \(operated by 21Vianet\).

Important

Microsoft recommends that you use roles with the fewest permissions. Using least-privileged accounts helps improve security for your organization. Global Administrator is a highly privileged role that should be limited to emergency scenarios when you can't use an existing role.

To manage free/busy calendar sharing for tenants in your MTO:

1. Sign in to the [Microsoft 365 admin center](https://admin.microsoft.com/) as a global administrator.
2. Expand **Settings** and select **Org settings**.
3. On the **Organization profile** tab, select **Multitenant collaboration**.
4. Select **Manage settings**.
5. Select **Edit calendar settings** under **Calendar**.
6. Select tenants to enable free/busy calendar sharing.
7. Select **Save changes**.

The calendar sharing feature for MTO utilizes [Organization relationships in Exchange Online](https://learn.microsoft.com/en-us/exchange/sharing/organization-relationships/organization-relationships). The organization relationship will share all users calendar availability and must also be set up by the other tenants in your MTO for free/busy information to be shared.

#### Troubleshoot calendar sharing issues

There are a couple of reasons that calendar sharing enablement might not work as it should:

1. "Failed to edit or create an organization relationship with \[tenant\]. Please try again later"

   This error typically only requires a refresh after some time. If error persists, review the setting in [Exchange Online](https://admin.exchange.microsoft.com/#/organizationsharing) to see if there's an existing organization relationship with this tenant.
2. "Failed to create an organization relationship for {tenantName}. This is a temporary delay caused by Active Directory replication after organization customization was enabled. Please try again in 15-20 minutes."

   1. When the Multitenant admin portal creates an organization relationship, Exchange Online might first need to enable organization customization by running `Enable-OrganizationCustomization`. This is a one-time tenant operation that can take time to replicate across the service.
   2. The portal has already initiated this operation for you. Wait up to 20 minutes, and then retry enabling calendar sharing.
   3. To learn more, see [Enable-OrganizationCustomization](https://learn.microsoft.com/en-us/powershell/module/exchangepowershell/enable-organizationcustomization?view=exchange-ps&preserve-view=true).

3. "Failed to get all domain names for \[tenant\]. This is an issue with how \[tenant\] has their primary domain name configured."

   This error typically requires the partner \[tenant\] to manage the status of their default domain here: [https://admin.microsoft.com/#/Domains](https://admin.microsoft.com/#/Domains). Additional details regarding domain troubleshooting can be found here: [Manage domains](https://learn.microsoft.com/en-us/microsoft-365/admin/get-help-with-domains/find-and-fix-issues)
4. "Failed to create a new organization relationship with \[tenant\]. This could be due to a duplicate organization relationship."

   The Multitenant admin portal creates or updates an organization relationship that includes the partner tenant's accepted domains. In Exchange Online, an accepted domain can only be associated with one organization relationship. If an organization relationship already exists that includes one of the partner domains, creating another one can fail with a duplicate error.

   Review existing organization relationships in [Exchange Online](https://admin.exchange.microsoft.com/#/organizationsharing). Then decide whether you want to manage organization relationships in the Multitenant admin portal or directly in the Exchange admin center \(EAC\) or Exchange Online PowerShell:

   1. Manage organization relationships in the Multitenant admin portal. Remove or update any existing organization relationship in Exchange Online that already includes the partner accepted domain\(s\), and then retry enabling calendar sharing.
   2. Manage organization relationships directly in Exchange Online \(EAC or PowerShell\). Keep the existing organization relationship, and manage free/busy settings there instead of enabling calendar sharing for that tenant in the Multitenant collaboration portal.

5. Free/busy availability fails with a "Forbidden" error.

   Calendar availability \(free/busy\) scenarios depend on Exchange Online permissions. If enabling free/busy sharing fails with a "Forbidden" error, validate that the account running the operation has the required Exchange Online RBAC permissions.

   In Exchange Online, administrators typically create or update organization relationships by using the `New-OrganizationRelationship` cmdlet. Exchange Online RBAC can restrict either the cmdlet itself or specific parameters on the cmdlet. A common failure pattern is that you can run `New-OrganizationRelationship`, but enabling free/busy fails because you don't have permission to use the `-FreeBusyAccessEnabled` parameter.

   The Exchange error message for this condition might look like this:

   "The FreeBusyAccessEnabled parameter can't be used on the New-OrganizationRelationship cmdlet because it isn't present in the role definition for the current user."

   To troubleshoot and resolve this issue:

   1. Confirm you're using an Exchange Online admin account that has the required RBAC permissions.
   2. Check whether Exchange Online RBAC role groups or role entries were customized in the tenant. By default, the **Organization Management** role group includes the **Federated Sharing** management role.
   3. Determine which management roles are assigned to the operator by using `Get-ManagementRoleAssignment`. To learn more, see [Get-ManagementRoleAssignment](https://learn.microsoft.com/en-us/powershell/module/exchangepowershell/get-managementroleassignment?view=exchange-ps&preserve-view=true). For example:

      ```powershell
      # List management roles assigned to the operator.
      Get-ManagementRoleAssignment -RoleAssignee <userUPN> | Select-Object Role, RoleAssigneeName, AssignmentMethod
      ```


      If you suspect a parameter-level restriction, verify that the operator is assigned a role that exposes `New-OrganizationRelationship` with the `FreeBusyAccessEnabled` parameter. You can correlate role assignments with role entries by searching for the cmdlet and parameter. For example:


      ```powershell
      # Find role entries for the cmdlet and check whether FreeBusyAccessEnabled is included.
      Get-ManagementRoleEntry "*\New-OrganizationRelationship" | Where-Object { $_.Parameters -contains "FreeBusyAccessEnabled" }

      # After you identify the required role (for example, Federated Sharing), confirm that role is assigned to the operator.
      Get-ManagementRoleAssignment -RoleAssignee <userUPN> | Where-Object { $_.Role -eq "Federated Sharing" }
      ```

6. Federation validation errors occur when you enable free/busy sharing.

   When calendar sharing is enabled, Exchange Online validates the partner tenant's domain and federation/autodiscover configuration. If validation fails, you might see errors like these:

   1. "Failed to validate the domain {domainName} for {tenantName}. Verify the domain name is correct and try again."
   2. "The domain {domainName} could not be found in DNS. Ensure the domain has valid DNS records configured."
   3. "The Autodiscover CNAME record is missing for {domainName}. DNS configuration may be incomplete."
   4. "{domainName} is not federated. Federation must be configured before enabling free/busy sharing."
   5. "A DNS query error occurred for {domainName}. This might be a temporary network issue. Try again later."
   6. "The federation endpoint for {tenantName} does not support the required security protocol."
   7. "Unable to connect to the Autodiscover service for {tenantName}."


   To troubleshoot:


   1. Validate the partner domain's DNS records and autodiscover configuration.
   2. Confirm the partner domain's autodiscover record points to the correct service:

      1. If the partner tenant uses Exchange Online for mailboxes, the public \(external\) autodiscover CNAME record should typically point to the global Exchange Online endpoint, `autodiscover.outlook.com`. To learn how to add or update DNS records for Microsoft 365 services, see [Connect your domain by adding DNS records](https://learn.microsoft.com/en-us/microsoft-365/admin/get-help-with-domains/create-dns-records-at-any-dns-hosting-provider?view=o365-worldwide&tabs=domain-connect&preserve-view=true).
      2. If the partner tenant uses a customer-managed Exchange deployment \(for example, Exchange Server on-premises or a hybrid configuration\), the autodiscover record should point to the tenant's published autodiscover endpoint.

   3. If you can reproduce the issue outside the portal, run `Get-FederationInformation` from Exchange Online PowerShell to validate federation and autodiscover for the domain. To learn more, see [Get-FederationInformation](https://learn.microsoft.com/en-us/powershell/module/exchangepowershell/get-federationinformation?view=exchange-ps&preserve-view=true). For example:

      ```powershell
      # Validate federation and autodiscover for the partner domain.
      Get-FederationInformation -DomainName <domain-name>
      ```

## Manage Teams collaboration setting

The Teams collaboration setting allows users to communicate with synced users from other multitenant organization \(MTO\) member tenants in Microsoft Teams. When enabled, users can collaborate across tenants through scenarios such as Teams search, calling, chat, and meeting scheduling.

Important

Microsoft recommends that you use roles with the fewest permissions. Using least-privileged accounts helps improve security for your organization. Global Administrator is a highly privileged role that should be limited to emergency scenarios when you can't use an existing role.

To manage Teams collaboration for tenants in your MTO:

1. Sign in to the [Microsoft 365 admin center](https://admin.microsoft.com/) as a global administrator.
2. Expand **Settings** and select **Org settings**.
3. On the **Organization profile** tab, select **Multitenant collaboration**.
4. Select **Manage settings**.
5. Select **Edit** under **Teams collaboration**.
6. Select **Edit in Microsoft Teams admin center** to make update.

This is a mutual configuration, meaning that all participating tenants must enable this setting for cross-tenant Teams collaboration to function.

## Set up MTO user labels in Teams for tenants in your MTO

MTO group admins can now configure an optional label for each tenant that will be displayed alongside MTO synced user's display name in Teams. This allows MTO synced users to be distinguishable within the MTO in Teams interactions.

![Teams people card shows MTO user label US.](https://learn.microsoft.com/en-us/microsoft-365/enterprise/media/manage-multitenant-org-settings/teams-mto-label-people-card.png?view=o365-worldwide)

> *Fig 1: Teams people card shows MTO user label "US"*

![Teams MTO search.](https://learn.microsoft.com/en-us/microsoft-365/enterprise/media/manage-multitenant-org-settings/teams-mto-search.png?view=o365-worldwide)

> *Fig 2: Teams search experience shows MTO user label "US"*

Only MTO owners can manage the MTO user labels. Label changes may take some time to process and will only apply to active tenants.

Important

Microsoft recommends that you use roles with the fewest permissions. Using least-privileged accounts helps improve security for your organization. Global Administrator is a highly privileged role that should be limited to emergency scenarios when you can't use an existing role.

To manage MTO user labels for tenants in your MTO:

1. Sign in to the [Microsoft 365 admin center](https://admin.microsoft.com/) as a global administrator.
2. Expand **Settings** and select **Org settings**.
3. On the **Organization profile** tab, select **Multitenant collaboration**.
4. Select **Manage settings**.
5. Select **Edit** under **Tenant label**.
6. Select either:

   1. No label.
   2. Use the multitenant organization name for all tenants.
   3. Custom \(assign a label for each tenant, which can't be blank\).

7. Select **Save changes**.

## Manage multitenant org notifications

Admins can opt-in for MTO notifications to ensure they don't miss any updates or changes to their MTO. Receive email notifications regarding any updates to the MTO such as: a new tenant joined the MTO, a tenant left the MTO, an MTO setting changed \(user labels, owner/member role, MTO name\), or user sync status changed \(Must have full-mesh sync set up via Microsoft 365 admin center\). Email notifications are sent daily, as long as any updates were made to the MTO. No notification is sent if nothing has changed.

Additionally, in the MAC MTO portal you can review the updates and see any Microsoft recommended actions. Opt-in and select the user\(s\) in your org who you would like to receive the notifications.

![activity center.](https://learn.microsoft.com/en-us/microsoft-365/enterprise/media/manage-multitenant-org-settings/activity-center.png?view=o365-worldwide)

Important

Microsoft recommends that you use roles with the fewest permissions. Using least-privileged accounts helps improve security for your organization. Global Administrator is a highly privileged role that should be limited to emergency scenarios when you can't use an existing role.

To manage MTO notifications:

1. Sign in to the [Microsoft 365 admin center](https://admin.microsoft.com/) as a global administrator.
2. Expand **Settings** and select **Org settings**.
3. On the **Organization profile** tab, select **Multitenant collaboration**.
4. Select **Manage settings**.
5. Select **Edit** under **Email notifications**.
6. Select **Allow email notifications**.
7. Enter the email addresses you would like to receive the notifications.
8. Select **Save changes**.
9. Grant permissions requested in dialog box.

#### Permissions

To enable multitenant org notifications, you must grant application [permissions](https://learn.microsoft.com/en-us/graph/permissions-reference) for the following actions:

These permissions are required to fetch cross-tenant synchronization details and to gather the status of the cross-tenant sync jobs.

- Reading cross-tenant sync information

  - [Application.Read.All](https://learn.microsoft.com/en-us/graph/permissions-reference#applicationreadall)
  - [Synchronization.Read.All](https://learn.microsoft.com/en-us/graph/permissions-reference#synchronizationreadall)

This permission is required to gather details regarding the multitenant organization.

- Reading MTO details

  - [MultiTenantOrganization.Read.All](https://learn.microsoft.com/en-us/graph/permissions-reference#multitenantorganizationreadall)

## Manage Outlook external tag removal for MTO members

If a tenant has enabled external tags in Outlook to help users identify content from external tenants, MTO group admins can now choose to suppress these tags for members of the multitenant organization. This setting allows for a more seamless collaboration experience and admins can enable this setting in the MAC MTO portal.

![Screenshot that shows suppression of Outlook external tag for MTO members.](https://learn.microsoft.com/en-us/microsoft-365/enterprise/media/manage-multitenant-org-settings/edit-external-tag-setting.png?view=o365-worldwide)

If the tenant hasn't enabled external tags in Outlook, checking the **External tag suppression** option will automatically create a remote domain for the partner tenant and mark it as internal \(i.e., IsInternal = true\), but it won't have effect in end user experience. In this case, external tags aren't displayed to members in MTO.

Important

Microsoft recommends that you use roles with the fewest permissions. Using least-privileged accounts helps improve security for your organization. Global Administrator is a highly privileged role that should be limited to emergency scenarios when you can't use an existing role.

To suppress Outlook external tag for tenants in your MTO:

1. Sign in to the [Microsoft 365 admin center](https://admin.microsoft.com/) as a global administrator.
2. Expand **Settings** and select **Org settings**.
3. On the **Organization profile** tab, select **Multitenant collaboration**.
4. Select **Manage settings**.
5. Select **Edit external tag settings** under **External tag**.
6. Select **Suppress Outlook external tag for MTO members**.
7. Select **Save changes**.

## Update the MTO cross-tenant sync job schema with newly supported attributes \(Private Preview\)

Important

Update the MTO cross-tenant sync job schema with newly supported attributes is currently available in preview. Features and availability may change before general availability \(GA\).

Some MTO collaboration features depend on Exchange attributes that aren't part of the default MTO cross-tenant synchronization schema. As Microsoft adds support for new cross-tenant scenarios, Microsoft 365 admins can extend the MTO MAC-created sync job schema with newly supported attributes from the Microsoft 365 admin center.

Important

Microsoft recommends that you use roles with the fewest permissions. Using least-privileged accounts helps improve security for your organization. Global Administrator is a highly privileged role that should be limited to emergency scenarios when you can't use an existing role.

### Newly supported attributes

The following Exchange recipient attributes can be added to the MTO-managed cross-tenant sync job schema:

| Attribute | Enables |
| --- | --- |
| MSExchRecipientDisplayType | Allows the target tenant to recognize a synchronized object as a meeting room instead of a standard user object in GAL. |
| MSExchRecipientTypeDetails | Allows the target tenant to recognize a synchronized object as a meeting room instead of a standard user object in GAL. |
| userSMIMECertificate | Synchronizes S/MIME certificates to the target tenant for encrypted and signed email scenarios. |
| userCertificate | Synchronizes S/MIME certificates to the target tenant for encrypted and signed email scenarios. |

These attributes are synchronized only for new or updated values after the attribute mappings are enabled. Existing attribute values aren't automatically synchronized.

In addition, users that were synchronized before the attribute mappings were enabled won't automatically receive these attributes in the target tenant. To make these attributes available for previously synchronized users, re-synchronize those users after enabling the mappings. Once re-synchronized, only new or updated attribute values are synchronized.

### Add attributes to the MTO MAC-created sync job schema

[![Screenshot that shows Microsoft 365 admin center showing Multitenant Collaboration settings and schema update panel.](https://learn.microsoft.com/en-us/microsoft-365/enterprise/media/manage-multitenant-org-settings/image.png?view=o365-worldwide)](https://learn.microsoft.com/en-us/microsoft-365/enterprise/media/manage-multitenant-org-settings/image.png?view=o365-worldwide#lightbox)

To update MTO MAC-created sync job schema with newly supported attributes:

1. Sign in to the [Microsoft 365 admin center](https://admin.microsoft.com/) as a global administrator.
2. Expand **Settings** and select **Org settings**.
3. On the **Organization profile** tab, select **Multitenant collaboration**.
4. Select **Schema update is recommended to unlock new capabilities** notification card.
5. On the right panel, review the list of newly supported attributes, and then select **Update schema**.

The added attributes are picked up by the cross-tenant sync jobs on the next sync cycle. The notification card is dismissed automatically after the schema is updated.

For information on enabling room discovery capability with newly supported attributes, see [Enable cross-tenant room discovery for MTO](https://learn.microsoft.com/en-us/microsoft-365/enterprise/enable-cross-tenant-room-discovery-for-mto).

Follow [this guidance](https://learn.microsoft.com/en-us/microsoft-365/enterprise/manage-multitenant-org-settings) to manually update CTS sync job schema for newly supported attributes.
