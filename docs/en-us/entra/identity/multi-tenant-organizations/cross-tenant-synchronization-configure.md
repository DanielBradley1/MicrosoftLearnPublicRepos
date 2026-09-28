<!-- Source: https://learn.microsoft.com/en-us/entra/identity/multi-tenant-organizations/cross-tenant-synchronization-configure -->
<!-- Sitemap-Last-Modified: 2026-08-06 -->

# Configure cross-tenant synchronization

## Overview

This article describes the steps to configure cross-tenant synchronization using the Microsoft Entra admin center. When configured, Microsoft Entra ID automatically provisions and de-provisions B2B users and security groups in your target tenant.

For important details on what this service does, how it works, and frequently asked questions, see [Automate user provisioning and deprovisioning to SaaS applications with Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/user-provisioning).

[![Diagram that shows cross-tenant synchronization between source tenant and target tenant.](https://learn.microsoft.com/en-us/entra/identity/multi-tenant-organizations/media/common/configure-diagram.png)](https://learn.microsoft.com/en-us/entra/identity/multi-tenant-organizations/media/common/configure-diagram.png#lightbox)

This article describes the steps to configure cross-tenant synchronization between Microsoft clouds. When configured, Microsoft Entra ID automatically provisions and de-provisions B2B users in your target tenant. While this tutorial focuses on synchronizing identities from the commercial cloud --> US Government, the same steps apply for Government --> Commercial and Commercial --> China.

For important details on what this service does, how it works, and frequently asked questions, see [Automate user provisioning and deprovisioning to SaaS applications with Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/user-provisioning). For differences between cross-tenant synchronization and cross-cloud synchronization, see [Cross-cloud synchronization in Frequently asked questions](https://learn.microsoft.com/en-us/entra/identity/multi-tenant-organizations/cross-tenant-synchronization-overview#clouds).

[![Diagram that shows cross-cloud synchronization between source tenant and target tenant.](https://learn.microsoft.com/en-us/entra/identity/multi-tenant-organizations/media/cross-tenant-synchronization-configure/configure-cross-cloud-diagram.png)](https://learn.microsoft.com/en-us/entra/identity/multi-tenant-organizations/media/cross-tenant-synchronization-configure/configure-cross-cloud-diagram.png#lightbox)

## Supported cloud pairs

Cross-tenant synchronization supports these cloud pairs:

| Source | Target | Azure portal link domains |
| --- | --- | --- |
| Azure commercial | Azure commercial | `portal.azure.com` --> `portal.azure.com` |
| Azure Government | Azure Government | `portal.azure.us` --> `portal.azure.us` |
| 21Vianet \(China\) | 21Vianet \(China\) | `portal.azure.cn` --> `portal.azure.cn` |

Cross-cloud synchronization supports these cloud pairs:

| Source | Target | Azure portal link domains |
| --- | --- | --- |
| Azure commercial | Azure Government | `portal.azure.com` --> `portal.azure.us` |
| Azure Government | Azure commercial | `portal.azure.us` --> `portal.azure.com` |
| Azure commercial | Azure operated by 21Vianet  <br>\(Azure in China\) | `portal.azure.com` --> `portal.azure.cn` |

## Learning objectives

By the end of this article, you'll be able to:

- Create B2B users and security groups in your target tenant
- Remove B2B users and security groups in your target tenant
- Keep user attributes synchronized between your source and target tenants

- Create B2B users in your target tenant
- Remove B2B users in your target tenant
- Keep user attributes synchronized between your source and target tenants

## Prerequisites

![Icon for the source tenant.](https://learn.microsoft.com/en-us/entra/media/common/icons/entra-id-purple.png)  
**Source tenant**

- Microsoft Entra ID P1 or P2 license for cross-tenant user sync. Microsoft Entra ID Governance or Microsoft Entra Suite licenses for cross-tenant group sync. For more information, see [License requirements](https://learn.microsoft.com/en-us/entra/identity/multi-tenant-organizations/cross-tenant-synchronization-overview#license-requirements).
- [Security Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#security-administrator) role to configure cross-tenant access settings.
- [Hybrid Identity Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#hybrid-identity-administrator) role to configure cross-tenant synchronization.
- [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator) or [Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#application-administrator) role to assign users to a configuration and to delete a configuration.

- Microsoft Entra ID Governance or Microsoft Entra Suite license. For more information, see [License requirements](https://learn.microsoft.com/en-us/entra/identity/multi-tenant-organizations/cross-tenant-synchronization-overview#license-requirements).
- [Security Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#security-administrator) role to configure cross-tenant access settings.
- [Hybrid Identity Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#hybrid-identity-administrator) role to configure cross-tenant synchronization.
- [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator) or [Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#application-administrator) role to assign users to a configuration and to delete a configuration.

![Icon for the target tenant.](https://learn.microsoft.com/en-us/entra/media/common/icons/entra-id.png)  
**Target tenant**

- [Security Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#security-administrator) role to configure cross-tenant access settings.

## Step 1: Plan your provisioning deployment

1. Define how you would like to [structure the tenants in your organization](https://learn.microsoft.com/en-us/entra/identity/multi-tenant-organizations/cross-tenant-synchronization-topology).
2. Learn about [how the provisioning service works](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/how-provisioning-works).
3. Determine who will be in [scope for provisioning](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts?toc=/entra/identity/multi-tenant-organizations/toc.json&pivots=cross-tenant-synchronization).
4. Determine what data to [map between tenants](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/customize-application-attributes).

## Step 1: Enable cross-cloud settings in both tenants

![Icon for the source tenant.](https://learn.microsoft.com/en-us/entra/media/common/icons/entra-id-purple.png)  
**Source tenant**

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) of the source tenant.
2. Browse to **Entra ID** > **External Identities** > **Cross-tenant access settings**.
3. On the **Microsoft cloud settings** tab, select the checkbox of the cloud you want to collaborate with, such as **Microsoft Azure Government**.

   The list of clouds will vary based on the cloud you are in. For more information, see [Microsoft cloud settings](https://learn.microsoft.com/en-us/entra/external-id/cross-tenant-access-overview#microsoft-cloud-settings).

   [![Screenshot of Microsoft cloud settings that shows checkboxes for different Microsoft clouds to collaborate with.](https://learn.microsoft.com/en-us/entra/identity/multi-tenant-organizations/media/cross-tenant-synchronization-configure/access-settings-cloud-settings.png)](https://learn.microsoft.com/en-us/entra/identity/multi-tenant-organizations/media/cross-tenant-synchronization-configure/access-settings-cloud-settings.png#lightbox)
4. Select **Save**.

![Icon for the target tenant.](https://learn.microsoft.com/en-us/entra/media/common/icons/entra-id.png)  
**Target**

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) of the target tenant.
2. Browse to **Entra ID** > **External Identities** > **Cross-tenant access settings**.
3. On the **Microsoft cloud settings** tab, select the cross-cloud synchronization checkbox for the source tenant, such as **Microsoft Azure Commercial**.

   [![Screenshot of Microsoft cloud settings that shows checkbox to enable cross-cloud synchronization.](https://learn.microsoft.com/en-us/entra/identity/multi-tenant-organizations/media/cross-tenant-synchronization-configure/access-settings-cross-cloud-sync.png)](https://learn.microsoft.com/en-us/entra/identity/multi-tenant-organizations/media/cross-tenant-synchronization-configure/access-settings-cross-cloud-sync.png#lightbox)

   When you select this checkbox, it creates a service principal with the following permissions:

   - User.ReadWrite.CrossCloud
   - User.Invite.All
   - Organization.Read.All
   - Policy.Read.All

4. Select **Save**.

## Step 2: Enable user and group synchronization in the target tenant

## Step 2: Enable user synchronization in the target tenant

![Icon for the target tenant.](https://learn.microsoft.com/en-us/entra/media/common/icons/entra-id.png)  
**Target tenant**

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) of the target tenant.
2. Browse to **Entra ID** > **External Identities** > **Cross-tenant access settings**.
3. On the **Organization settings** tab, select **Add organization**.
4. Add the source tenant by typing the tenant ID or domain name and selecting **Add**.

   [![Screenshot that shows the Add organization pane to add the source tenant.](https://learn.microsoft.com/en-us/entra/identity/multi-tenant-organizations/media/cross-tenant-synchronization-configure/access-settings-organization-add.png)](https://learn.microsoft.com/en-us/entra/identity/multi-tenant-organizations/media/cross-tenant-synchronization-configure/access-settings-organization-add.png#lightbox)
5. Under **Inbound access** of the added organization, select **Inherited from default**.
6. Select the **Cross-tenant sync** tab.

7. Select the **Allow user synchronization into this tenant** checkbox.

   Optionally, select the **Allow group synchronization into this tenant** checkbox.

   For more information, see [Group synchronization](https://learn.microsoft.com/en-us/entra/identity/multi-tenant-organizations/cross-tenant-synchronization-overview#group-synchronization).

   [![Screenshot that shows the Cross-tenant sync tab with the Allow user synchronization into this tenant and Allow group synchronization into this tenant checkboxes.](https://learn.microsoft.com/en-us/entra/media/external-identities/access-settings-users-sync.png)](https://learn.microsoft.com/en-us/entra/media/external-identities/access-settings-users-sync.png#lightbox)

7. Select the **Allow user synchronization into this tenant** checkbox.

8. Select **Save**.
9. If you see an **Enable cross-tenant sync and auto-redemption** dialog box asking if you want to enable auto-redemption, select **Yes**.

   Selecting **Yes** will automatically redeem invitations in the target tenant.

   [![Screenshot that shows the Enable cross-tenant sync and auto-redemption dialog box to automatically redeem invitations in the target tenant.](https://learn.microsoft.com/en-us/entra/identity/multi-tenant-organizations/media/cross-tenant-synchronization-configure/access-settings-users-sync-auto-redemption.png)](https://learn.microsoft.com/en-us/entra/identity/multi-tenant-organizations/media/cross-tenant-synchronization-configure/access-settings-users-sync-auto-redemption.png#lightbox)

## Step 3: Automatically redeem invitations in the target tenant

![Icon for the target tenant.](https://learn.microsoft.com/en-us/entra/media/common/icons/entra-id.png)  
**Target tenant**

In this step, you automatically redeem invitations so users from the source tenant don't have to accept the consent prompt. This setting must be checked in both the source tenant \(outbound\) and target tenant \(inbound\). For more information, see [Automatic redemption setting](https://learn.microsoft.com/en-us/entra/identity/multi-tenant-organizations/cross-tenant-synchronization-overview#automatic-redemption-setting).

1. In the target tenant, on the same **Inbound access settings** page, select the **Trust settings** tab.
2. Check the **Automatically redeem invitations with the tenant** <tenant> checkbox.

   This box might already be checked if you previously selected **Yes** in the **Enable cross-tenant sync and auto-redemption** dialog box.

   [![Screenshot that shows the inbound Automatic redemption checkbox.](https://learn.microsoft.com/en-us/entra/media/external-identities/inbound-consent-prompt-setting.png)](https://learn.microsoft.com/en-us/entra/media/external-identities/inbound-consent-prompt-setting.png#lightbox)
3. Select **Save**.

## Step 4: Automatically redeem invitations in the source tenant

![Icon for the source tenant.](https://learn.microsoft.com/en-us/entra/media/common/icons/entra-id-purple.png)  
**Source tenant**

In this step, you automatically redeem invitations in the source tenant.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) of the source tenant.
2. Browse to **Entra ID** > **External Identities** > **Cross-tenant access settings**.
3. On the **Organization settings** tab, select **Add organization**.
4. Add the target tenant by typing the tenant ID or domain name and selecting **Add**.

   [![Screenshot that shows the Add organization pane to add the target tenant.](https://learn.microsoft.com/en-us/entra/identity/multi-tenant-organizations/media/cross-tenant-synchronization-configure/access-settings-organization-add-target.png)](https://learn.microsoft.com/en-us/entra/identity/multi-tenant-organizations/media/cross-tenant-synchronization-configure/access-settings-organization-add-target.png#lightbox)
5. Under **Outbound access** for the target organization, select **Inherited from default**.
6. Select the **Trust settings** tab.
7. Check the **Automatically redeem invitations with the tenant** <tenant> checkbox.

   [![Screenshot that shows the outbound Automatic redemption checkbox.](https://learn.microsoft.com/en-us/entra/media/external-identities/outbound-consent-prompt-setting.png)](https://learn.microsoft.com/en-us/entra/media/external-identities/outbound-consent-prompt-setting.png#lightbox)
8. Select **Save**.

## Step 5: Create a configuration in the source tenant

![Icon for the source tenant.](https://learn.microsoft.com/en-us/entra/media/common/icons/entra-id-purple.png)  
**Source tenant**

1. In the source tenant, browse to **Entra ID** > **Cross-tenant synchronization**.

   [![Screenshot that shows the Cross-tenant synchronization navigation in the Microsoft Entra admin center.](https://learn.microsoft.com/en-us/entra/identity/multi-tenant-organizations/media/cross-tenant-synchronization-configure/navigation-cross-tenant-sync-entra.png)](https://learn.microsoft.com/en-us/entra/identity/multi-tenant-organizations/media/cross-tenant-synchronization-configure/navigation-cross-tenant-sync-entra.png#lightbox)

   If you are using the Azure portal, browse to **Microsoft Entra ID** > **Manage** > **Cross-tenant synchronization**.

   [![Screenshot that shows the Cross-tenant synchronization navigation in the Azure portal.](https://learn.microsoft.com/en-us/entra/identity/multi-tenant-organizations/media/cross-tenant-synchronization-configure/navigation-cross-tenant-sync-azure.png)](https://learn.microsoft.com/en-us/entra/identity/multi-tenant-organizations/media/cross-tenant-synchronization-configure/navigation-cross-tenant-sync-azure.png#lightbox)
2. Select **Configurations**.
3. At the top of the page, select **New configuration**.

4. Provide a name for the configuration.

   [![Screenshot of a new configuration that shows the name.](https://learn.microsoft.com/en-us/entra/identity/multi-tenant-organizations/media/cross-tenant-synchronization-configure/configuration-name.png)](https://learn.microsoft.com/en-us/entra/identity/multi-tenant-organizations/media/cross-tenant-synchronization-configure/configuration-name.png#lightbox)
5. Select **Create**.

   It can take up to 15 seconds for the configuration that you just created to appear in the list.

4. Provide a name for the configuration.
5. Select the **Setup cross-tenant synchronization across Microsoft clouds** checkbox.

   [![Screenshot of a new configuration that shows the name and cross-cloud synchronization checkbox.](https://learn.microsoft.com/en-us/entra/identity/multi-tenant-organizations/media/cross-tenant-synchronization-configure/configuration-name-cross-cloud-sync.png)](https://learn.microsoft.com/en-us/entra/identity/multi-tenant-organizations/media/cross-tenant-synchronization-configure/configuration-name-cross-cloud-sync.png#lightbox)
6. Select **Create**.

   It can take up to 15 seconds for the configuration that you just created to appear in the list.

   On the Configurations page for cross-cloud synchronization, the **Tenant Name** and **Tenant ID** columns will be empty.

## Step 6: Test the connection to the target tenant

![Icon for the source tenant.](https://learn.microsoft.com/en-us/entra/media/common/icons/entra-id-purple.png)  
**Source tenant**

1. In the source tenant, you should see your new configuration. If not, in the configuration list, select your configuration.

   [![Screenshot that shows the Cross-tenant synchronization Configurations page and a new configuration.](https://learn.microsoft.com/en-us/entra/identity/multi-tenant-organizations/media/cross-tenant-synchronization-configure/configuration-select.png)](https://learn.microsoft.com/en-us/entra/identity/multi-tenant-organizations/media/cross-tenant-synchronization-configure/configuration-select.png#lightbox)
2. Select **New configuration** to create a new provisioning configuration.
3. Under the **Admin credentials** section, in the **Tenant Id** box, enter the tenant ID of the target tenant.

   [![Screenshot that shows the Provisioning page with the Cross-tenant Synchronization Policy selected.](https://learn.microsoft.com/en-us/entra/identity/multi-tenant-organizations/media/cross-tenant-synchronization-configure/provisioning-policy.png)](https://learn.microsoft.com/en-us/entra/identity/multi-tenant-organizations/media/cross-tenant-synchronization-configure/provisioning-policy.png#lightbox)
4. Select **Test connection** to test the connection.

   You should see a message that the supplied credentials are authorized to enable provisioning. If the test connection fails, see [Troubleshoot common cross-tenant synchronization scenarios](#troubleshoot-common-cross-tenant-synchronization-scenarios) later in this article.

   [![Screenshot that shows a testing connection notification.](https://learn.microsoft.com/en-us/entra/identity/multi-tenant-organizations/media/cross-tenant-synchronization-configure/provisioning-test-connection-success.png)](https://learn.microsoft.com/en-us/entra/identity/multi-tenant-organizations/media/cross-tenant-synchronization-configure/provisioning-test-connection-success.png#lightbox)
5. Select **Create**.

   It can take a few seconds to create the new provisioning configuration.

## Step 7: Define who is in scope for provisioning

![Icon for the source tenant.](https://learn.microsoft.com/en-us/entra/media/common/icons/entra-id-purple.png)  
**Source tenant**

The Microsoft Entra provisioning service allows you to define who will be provisioned in one or both of the following ways:

- Based on assignment to the configuration
- Based on attributes of the user

Start small. Test with a small set of users before rolling out to everyone. When the scope for provisioning is set to assigned users and groups, you can control it by assigning one or two users to the configuration. You can further refine who is in scope for provisioning by creating attribute-based scoping filters, described in the [next step](#step-8-optional-define-who-is-in-scope-for-provisioning-with-scoping-filters).

1. In the source tenant, on the **Overview** page, select the **Properties** tab.

   [![Screenshot of the Overview page that shows the Properties tab.](https://learn.microsoft.com/en-us/entra/identity/multi-tenant-organizations/media/cross-tenant-synchronization-configure/provisioning-settings.png)](https://learn.microsoft.com/en-us/entra/identity/multi-tenant-organizations/media/cross-tenant-synchronization-configure/provisioning-settings.png#lightbox)
2. Next to the **Basics** heading, select the pencil icon to open the **Basics** pane.

   [![Screenshot of the Provisioning page that shows the Settings section with the Scope and Provisioning Status options.](https://learn.microsoft.com/en-us/entra/identity/multi-tenant-organizations/media/cross-tenant-synchronization-configure/provisioning-settings-edit.png)](https://learn.microsoft.com/en-us/entra/identity/multi-tenant-organizations/media/cross-tenant-synchronization-configure/provisioning-settings-edit.png#lightbox)
3. In the **Scope** list, select whether to synchronize all users in the source tenant or only users assigned to the configuration.

   It's recommended that you select **Sync only assigned users** instead of **Sync all users**. Reducing the number of users in scope improves performance.

   If you want to synchronize groups, you must select **Sync only assigned users and groups**.
4. If you made any changes, select **Apply**.
5. On the configuration page, select **Users and groups**.

   For cross-tenant synchronization to work, at least one internal user must be assigned to the configuration.
6. Select **Add user/group**.
7. On the **Add Assignment** page, under **Users and groups**, select **None Selected**.
8. On the **Users and groups** pane, search for and select one or more internal users and groups you want to assign to the configuration.

   If you select a group to assign to the configuration, only users that are direct members in the group will be in scope for provisioning. You can select a static group or a dynamic group. The assignment doesn't cascade to nested groups.
9. Select **Select**.
10. Select **Assign**.

    [![Screenshot that shows the Users and groups page with a user assigned to the configuration.](https://learn.microsoft.com/en-us/entra/identity/multi-tenant-organizations/media/cross-tenant-synchronization-configure/users-and-groups.png)](https://learn.microsoft.com/en-us/entra/identity/multi-tenant-organizations/media/cross-tenant-synchronization-configure/users-and-groups.png#lightbox)

    For more information, see [Assign users and groups to an application](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/assign-user-or-group-access-portal).

## Step 8: \(Optional\) Define who is in scope for provisioning with scoping filters

![Icon for the source tenant.](https://learn.microsoft.com/en-us/entra/media/common/icons/entra-id-purple.png)  
**Source tenant**

Regardless of the value you selected for **Scope** in the previous step, you can further limit which users are synchronized by creating attribute-based scoping filters.

1. In the source tenant, select **Provisioning** and expand the **Mappings** section.

   [![Screenshot that shows the Provisioning page with the Mappings section expanded.](https://learn.microsoft.com/en-us/entra/identity/multi-tenant-organizations/media/common/provisioning-mappings.png)](https://learn.microsoft.com/en-us/entra/identity/multi-tenant-organizations/media/common/provisioning-mappings.png#lightbox)
2. Select **Provision Microsoft Entra ID Users** to open the **Attribute Mapping** page.
3. Under **Source Object Scope**, select **All records**.

   [![Screenshot that shows the Attribute Mapping page with the Source Object Scope.](https://learn.microsoft.com/en-us/entra/identity/multi-tenant-organizations/media/cross-tenant-synchronization-configure/provisioning-attribute-mapping-scope.png)](https://learn.microsoft.com/en-us/entra/identity/multi-tenant-organizations/media/cross-tenant-synchronization-configure/provisioning-attribute-mapping-scope.png#lightbox)
4. On the **Source Object Scope** page, select **Add scoping filter**.
5. Add any scoping filters to define which users are in scope for provisioning.

   To configure scoping filters, refer to the instructions provided in [Scoping users or groups to be provisioned with scoping filters](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts?toc=/entra/identity/multi-tenant-organizations/toc.json&pivots=cross-tenant-synchronization).

   [![Screenshot that shows the Add Scoping Filter page with sample filter.](https://learn.microsoft.com/en-us/entra/identity/multi-tenant-organizations/media/cross-tenant-synchronization-configure/provisioning-attribute-mapping-scoping-filter.png)](https://learn.microsoft.com/en-us/entra/identity/multi-tenant-organizations/media/cross-tenant-synchronization-configure/provisioning-attribute-mapping-scoping-filter.png#lightbox)
6. Select **Ok** and **Save** to save any changes.

   If you added a filter, you'll see a message that saving your changes will result in all assigned users and groups being resynchronized. This may take a long time depending on the size of your directory.
7. Select **Yes** and close the **Attribute Mapping** page.

8. On the **Provisioning** page, under the **Mappings** section, select **Provision Microsoft Entra ID Groups** to open the **Attribute Mapping** page.
9. If you want to synchronize groups, set the **Enabled** toggle to **Yes**.

   By default, this toggle is set to **No**.
10. If you want to scoping filters for groups, follow similar previous steps as users.

## Step 9: Review attribute mappings

![Icon for the source tenant.](https://learn.microsoft.com/en-us/entra/media/common/icons/entra-id-purple.png)  
**Source tenant**

Attribute mappings allow you to define how data should flow between the source tenant and target tenant. For information on how to customize the default attribute mappings, see [Tutorial - Customize user provisioning attribute-mappings for SaaS applications in Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/customize-application-attributes).

1. In the source tenant, select **Attribute mapping**.
2. On the **Attribute mapping** page, scroll down to review the user attributes that are synchronized between tenants.

   The **AltSecIdFromNetId\(\[netId\]\) \(alternativeSecurityIds\)** is an internal attribute used to uniquely identify the user across tenants, match users in the source tenant with existing users in the target tenant, and ensure that each user only has one account. The matching attribute can't be changed. Attempting to change the matching attribute or adding additional matching attributes will result in a `schemaInvalid` error.

   [![Screenshot of the Attribute Mapping page that shows the list of Microsoft Entra attributes.](https://learn.microsoft.com/en-us/entra/identity/multi-tenant-organizations/media/cross-tenant-synchronization-configure/provisioning-attribute-mapping.png)](https://learn.microsoft.com/en-us/entra/identity/multi-tenant-organizations/media/cross-tenant-synchronization-configure/provisioning-attribute-mapping.png#lightbox)
3. For the **Member \(userType\)** attribute, select the pencil icon to open the **Edit Attribute Mapping** page.
4. Review the **Constant attribute** setting, which by default is set to **Member**.

   This setting defines the type of user that will be created in the target tenant and can be one of the values in the following table. By default, users will be created as external member \(B2B collaboration users\). For more information, see [Properties of a Microsoft Entra B2B collaboration user](https://learn.microsoft.com/en-us/entra/external-id/user-properties).

   | Constant attribute | Description |
   | --- | --- |
   | **Member** | Default. Users will be created as external member \(B2B collaboration users\) in the target tenant. Users will be able to function as any internal member of the target tenant. |
   | **Guest** | Users will be created as external guests \(B2B collaboration users\) in the target tenant. |


   Note


   If the B2B user already exists in the target tenant, then **Member \(userType\)** won't be changed to **Member**, unless the **Apply this mapping** setting is set to **Always**.


   The user type you choose has the following limitations for apps or services \(but aren't limited to\):


   | App or service | Limitations |
   | --- | --- |
   | Azure Virtual Desktop | For limitations, see [Prerequisites for Azure Virtual Desktop](https://learn.microsoft.com/en-us/azure/virtual-desktop/prerequisites#users). |
   | Microsoft Teams | For limitations, see [Collaborate with guests from other Microsoft 365 cloud environments](https://learn.microsoft.com/en-us/microsoft-365/solutions/collaborate-guests-cross-cloud). |


   [![Screenshot of the Edit Attribute page that shows the Member attribute.](https://learn.microsoft.com/en-us/entra/identity/multi-tenant-organizations/media/cross-tenant-synchronization-configure/provisioning-attribute-mapping-member.png)](https://learn.microsoft.com/en-us/entra/identity/multi-tenant-organizations/media/cross-tenant-synchronization-configure/provisioning-attribute-mapping-member.png#lightbox)

5. If you want to define any transformations, on the **Attribute mapping** page, select the pencil icon for the attribute you want to transform, such as **displayName**.
6. Set the **Mapping type** to **Expression**.
7. In the **Expression** box, enter the transformation expression. For example with the display name, you can do the following:

   - Flip the first name and last name and add a comma in between.
   - Add the domain name in parentheses at the end of the display name.


   For examples, see [Reference for writing expressions for attribute mappings in Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/functions-for-customizing-application-data?toc=/entra/identity/multi-tenant-organizations/toc.json#examples).


   [![Screenshot of the Edit Attribute page that shows the displayName attribute with the Expression box.](https://learn.microsoft.com/en-us/entra/identity/multi-tenant-organizations/media/cross-tenant-synchronization-configure/provisioning-attribute-mapping-displayname-expression.png)](https://learn.microsoft.com/en-us/entra/identity/multi-tenant-organizations/media/cross-tenant-synchronization-configure/provisioning-attribute-mapping-displayname-expression.png#lightbox)

9. On the **Provisioning** page, under the **Mappings** section, select **Provision Microsoft Entra ID Groups** to open the **Attribute Mapping** page.
10. If you want to modify attribute mappings for groups, follow similar previous steps as users.

Tip

You can map directory extensions by updating the schema of the cross-tenant synchronization. For more information, see [Map directory extensions in cross-tenant synchronization](https://learn.microsoft.com/en-us/entra/identity/multi-tenant-organizations/cross-tenant-synchronization-directory-extensions).

## Step 10: Specify additional provisioning settings

![Icon for the source tenant.](https://learn.microsoft.com/en-us/entra/media/common/icons/entra-id-purple.png)  
**Source tenant**

1. In the source tenant, on the **Overview** page, select the **Properties** tab.
2. Next to the **Basics** heading, select the pencil icon to open the **Basics** pane.

   [![Screenshot of the Provisioning page that shows the Settings section with the Scope and Provisioning Status options.](https://learn.microsoft.com/en-us/entra/identity/multi-tenant-organizations/media/cross-tenant-synchronization-configure/provisioning-settings-edit.png)](https://learn.microsoft.com/en-us/entra/identity/multi-tenant-organizations/media/cross-tenant-synchronization-configure/provisioning-settings-edit.png#lightbox)
3. In the **Notification email** box, enter the email address of a person or group who should receive provisioning error notifications.

   Email notifications are sent within 24 hours of the job entering quarantine state. For custom alerts, see [Understand how provisioning integrates with Azure Monitor logs](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/application-provisioning-log-analytics).
4. To prevent accidental deletion, select **Prevent accidental deletion** and specify a threshold value. By default, the threshold is set to 500.

   For more information, see [Enable accidental deletions prevention in the Microsoft Entra provisioning service](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/accidental-deletions?toc=/entra/identity/multi-tenant-organizations/toc.json&pivots=cross-tenant-synchronization).
5. Select **Apply** to save any changes.

## Step 11: Test provision on demand

![Icon for the source tenant.](https://learn.microsoft.com/en-us/entra/media/common/icons/entra-id-purple.png)  
**Source tenant**

Now that you have a configuration, you can test on-demand provisioning with one of your users.

1. In the source tenant, browse to **Entra ID** > **Cross-tenant synchronization**.
2. Select **Configurations** and then select your configuration.
3. Select **Provision on demand**.
4. In the **Select a user or group** box, search for and select one of your test users.

   [![Screenshot of the Provision on demand page that shows a test user selected.](https://learn.microsoft.com/en-us/entra/identity/multi-tenant-organizations/media/cross-tenant-synchronization-configure/provision-on-demand.png)](https://learn.microsoft.com/en-us/entra/identity/multi-tenant-organizations/media/cross-tenant-synchronization-configure/provision-on-demand.png#lightbox)
5. Select **Provision**.

   After a few moments, the **Perform action** page appears with information about the provisioning of the test user in the target tenant.

   [![Screenshot of the Perform action page that shows the test user and list of modified attributes.](https://learn.microsoft.com/en-us/entra/identity/multi-tenant-organizations/media/cross-tenant-synchronization-configure/provision-on-demand-provision.png)](https://learn.microsoft.com/en-us/entra/identity/multi-tenant-organizations/media/cross-tenant-synchronization-configure/provision-on-demand-provision.png#lightbox)

   If the user isn't in scope, you'll see a page with information about why the test user was skipped.

   [![Screenshot that shows information about why the test user was skipped on the Determine if user is in scope page.](https://learn.microsoft.com/en-us/entra/identity/multi-tenant-organizations/media/cross-tenant-synchronization-configure/provision-on-demand-provision-skipped.png)](https://learn.microsoft.com/en-us/entra/identity/multi-tenant-organizations/media/cross-tenant-synchronization-configure/provision-on-demand-provision-skipped.png#lightbox)

   On the **Provision on demand** page, you can view details about the provision and have the option to retry.

   [![Screenshot of the Provision on demand page that shows details about the provision.](https://learn.microsoft.com/en-us/entra/identity/multi-tenant-organizations/media/cross-tenant-synchronization-configure/provision-on-demand-provision-details.png)](https://learn.microsoft.com/en-us/entra/identity/multi-tenant-organizations/media/cross-tenant-synchronization-configure/provision-on-demand-provision-details.png#lightbox)
6. In the target tenant, verify that the test user was provisioned.

   [![Screenshot of the Users page of the target tenant that shows the test user provisioned.](https://learn.microsoft.com/en-us/entra/identity/multi-tenant-organizations/media/cross-tenant-synchronization-configure/provision-on-demand-users-target.png)](https://learn.microsoft.com/en-us/entra/identity/multi-tenant-organizations/media/cross-tenant-synchronization-configure/provision-on-demand-users-target.png#lightbox)
7. If all is working as expected, assign additional users to the configuration.

   For more information, see [On-demand provisioning in Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/provision-on-demand?toc=/entra/identity/multi-tenant-organizations/toc.json&pivots=cross-tenant-synchronization).

## Step 12: Start the provisioning job

![Icon for the source tenant.](https://learn.microsoft.com/en-us/entra/media/common/icons/entra-id-purple.png)  
**Source tenant**

The provisioning job starts the initial synchronization cycle of all users defined in **Scope** of the **Settings** section. The initial cycle takes longer to perform than subsequent cycles, which occur approximately every 40 minutes as long as the Microsoft Entra provisioning service is running.

1. In the source tenant, browse to **Entra ID** > **Cross-tenant synchronization**.
2. Select **Configurations** and then select your configuration.
3. On the **Overview** page, review the provisioning details.

   [![Screenshot of the Configurations Overview page that lists provisioning details.](https://learn.microsoft.com/en-us/entra/identity/multi-tenant-organizations/media/cross-tenant-synchronization-configure/configuration-overview-provisioning.png)](https://learn.microsoft.com/en-us/entra/identity/multi-tenant-organizations/media/cross-tenant-synchronization-configure/configuration-overview-provisioning.png#lightbox)
4. Select **Start provisioning** to start the provisioning job.

## Step 13: Monitor provisioning

![Icon for the source tenant.](https://learn.microsoft.com/en-us/entra/media/common/icons/entra-id-purple.png) ![Icon for the target tenant.](https://learn.microsoft.com/en-us/entra/media/common/icons/entra-id.png)  
**Source and target tenants**

Once you've started a provisioning job, you can monitor the status.

1. In the source tenant, on the **Overview** page, check the progress bar to see the status of the provisioning cycle and how close it's to completion. For more information, see [Check the status of user provisioning](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/application-provisioning-when-will-provisioning-finish-specific-user).

   If provisioning seems to be in an unhealthy state, the configuration will go into quarantine. For more information, see [Application provisioning in quarantine status](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/application-provisioning-quarantine-status).

   [![Screenshot of the Configurations Overview page that shows the status of the provisioning cycle.](https://learn.microsoft.com/en-us/entra/identity/multi-tenant-organizations/media/cross-tenant-synchronization-configure/provisioning-job-start.png)](https://learn.microsoft.com/en-us/entra/identity/multi-tenant-organizations/media/cross-tenant-synchronization-configure/provisioning-job-start.png#lightbox)
2. Select **Provisioning logs** to determine which users have been provisioned successfully or unsuccessfully. By default, the logs are filtered by the service principal ID of the configuration. For more information, see [Provisioning logs in Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/identity/monitoring-health/concept-provisioning-logs?toc=/entra/identity/multi-tenant-organizations/toc.json).

   [![Screenshot of the Provisioning logs page that lists the log entries and their status.](https://learn.microsoft.com/en-us/entra/identity/multi-tenant-organizations/media/cross-tenant-synchronization-configure/provisioning-logs.png)](https://learn.microsoft.com/en-us/entra/identity/multi-tenant-organizations/media/cross-tenant-synchronization-configure/provisioning-logs.png#lightbox)
3. Select **Audit logs** to view all logged events in Microsoft Entra ID. For more information, see [Audit logs in Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/identity/monitoring-health/concept-audit-logs).

   [![Screenshot of the Audit logs page that lists the log entries and their status.](https://learn.microsoft.com/en-us/entra/identity/multi-tenant-organizations/media/cross-tenant-synchronization-configure/audit-logs-source.png)](https://learn.microsoft.com/en-us/entra/identity/multi-tenant-organizations/media/cross-tenant-synchronization-configure/audit-logs-source.png#lightbox)

   You can also view audit logs in the target tenant.
4. In the target tenant, select **Users** > **Audit logs** to view logged events for user management. Cross-tenant synchronization in the target tenant will be logged as the actor being the "Microsoft.Azure.SyncFabric" application.

   [![Screenshot of the Audit logs page in the target tenant that lists the log entries for user management.](https://learn.microsoft.com/en-us/entra/identity/multi-tenant-organizations/media/cross-tenant-synchronization-configure/audit-logs-users-target.png)](https://learn.microsoft.com/en-us/entra/identity/multi-tenant-organizations/media/cross-tenant-synchronization-configure/audit-logs-users-target.png#lightbox)

## Step 14: Configure leave settings

![Icon for the target tenant.](https://learn.microsoft.com/en-us/entra/media/common/icons/entra-id.png)  
**Target tenant**

Even though users are being provisioned in the target tenant, they still might be able to remove themselves. If users remove themselves and they are in scope, they'll be provisioned again during the next provisioning cycle. If you want to disallow the ability for users to remove themselves from your organization, you must configure the **External user leave settings**.

1. In the target tenant, browse to **Entra ID** > **External Identities** > **External collaboration settings**.
2. Under **External user leave settings**, choose whether to allow external users to leave your organization themselves.

This setting also applies to B2B collaboration and B2B direct connect, so if you set **External user leave settings** to **No**, B2B collaboration users and B2B direct connect users can't leave your organization themselves. For more information, see [Leave an organization as an external user](https://learn.microsoft.com/en-us/entra/external-id/leave-the-organization#more-information-for-administrators).

## Troubleshoot common cross-tenant synchronization scenarios

### Symptom - Test connection fails with AzureActiveDirectoryCrossTenantSyncPolicyCheckFailure

When configuring cross-tenant synchronization in the source tenant and you test the connection, it fails with one of the following error messages:

*Automatic redemption is not set up in the source tenant*

```
You appear to have entered invalid credentials. Please confirm you are using the correct information for an administrative account.
Error code: AzureActiveDirectoryCrossTenantSyncPolicyCheckFailure
Details: The source tenant has not enabled automatic user consent with the target tenant. Please enable the outbound cross-tenant access policy for automatic user consent in the source tenant. aka.ms/TroubleshootingCrossTenantSyncPolicyCheck
```

*Automatic redemption is not set up in the target tenant*

```
You appear to have entered invalid credentials. Please confirm you are using the correct information for an administrative account.
Error code: AzureActiveDirectoryCrossTenantSyncPolicyCheckFailure
Details: The target tenant has not enabled inbound synchronization with this tenant. Please request the target tenant admin to enable the inbound synchronization on their cross-tenant access policy. Learn more: aka.ms/TroubleshootingCrossTenantSyncPolicyCheck
```

**Cause**

This error indicates the policy to automatically redeem invitations in the source and / or target tenants wasn't set up.

**Solution**

Follow the steps in [Step 3: Automatically redeem invitations in the target tenant](#step-3-automatically-redeem-invitations-in-the-target-tenant) and [Step 4: Automatically redeem invitations in the source tenant](#step-4-automatically-redeem-invitations-in-the-source-tenant).

### Symptom - Test connection fails with ExternalTenantNotFound

When configuring cross-cloud synchronization in the source tenant and you test the connection, it fails with the following error message:

```
You appear to have entered invalid credentials. Please confirm you are using the correct information for an administrative account.
Error code: ExternalTenantNotFound
Details: This tenant was not found by the authentication authority of the current cloud: <targetTenantId>. The authentication authority is https://login.microsoftonline.com/<targetTenantId>.
```

**Cause**

This error indicates the **Setup cross-tenant synchronization across Microsoft clouds** checkbox is not checked.

**Solution**

1. In the source tenant, delete the configuration you created that fails to connect.
2. In the target tenant, create a new configuration and be sure to check the **Setup cross-tenant synchronization across Microsoft clouds** checkbox as described in [Step 5: Create a configuration in the source tenant](#step-5-create-a-configuration-in-the-source-tenant).

### Symptom - Test connection fails with AzureActiveDirectoryTokenExpired

When configuring cross-cloud synchronization in the source tenant and you test the connection, it fails with the following error message:

```
You appear to have entered invalid credentials. Please confirm you are using the correct information for an administrative account.
Error code: AzureActiveDirectoryTokenExpired
Details: The identity of the calling application could not be established.
```

**Cause**

This error indicates the cross-cloud setting for synchronization has not been enabled.

**Solution**

In the target tenant, on the **Microsoft cloud settings** tab, select the cross-cloud synchronization checkbox for the source tenant. Follow the steps in [Step 1: Enable cross-cloud settings in both tenants](#step-1-enable-cross-cloud-settings-in-both-tenants).

### Symptom - Automatic redemption checkbox is disabled

When configuring cross-tenant synchronization, the **Automatic redemption** checkbox is disabled.

[![Screenshot that shows the Automatic redemption checkbox as disabled.](https://learn.microsoft.com/en-us/entra/identity/multi-tenant-organizations/media/cross-tenant-synchronization-configure/consent-prompt-setting-disabled.png)](https://learn.microsoft.com/en-us/entra/identity/multi-tenant-organizations/media/cross-tenant-synchronization-configure/consent-prompt-setting-disabled.png#lightbox)

**Cause**

Your tenant doesn't have a Microsoft Entra ID P1 or P2 license.

**Solution**

You must have Microsoft Entra ID P1 or P2 to configure trust settings.

### Symptom - Recently deleted user in the target tenant is not restored

After soft deleting a synchronized user in the target tenant, the user isn't restored during the next synchronization cycle. If you try to soft delete a user with on-demand provisioning and then restore the user, it can result in duplicate users.

**Cause**

Restoring a previously soft-deleted user in the target tenant isn't supported.

**Solution**

Manually restore the soft-deleted user in the target tenant. For more information, see [Restore or remove a recently deleted user using Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/fundamentals/users-restore).

### Symptom - Users are skipped because SMS sign-in is enabled on the user

Users are skipped from synchronization. The scoping step includes the following filter with status false: "Filter external users.alternativeSecurityIds EQUALS 'None'"

**Cause**

If SMS sign-in is enabled for a user, they will be skipped by the provisioning service.

**Solution**

Disable SMS Sign-in for the users. The script below shows how you can disable SMS Sign-in using PowerShell.

```powershell
##### Disable SMS Sign-in options for the users

#### Import module
Install-Module Microsoft.Graph.Users.Actions
Install-Module Microsoft.Graph.Identity.SignIns
Import-Module Microsoft.Graph.Users.Actions

Connect-MgGraph -Scopes "User.Read.All", "Group.ReadWrite.All", "UserAuthenticationMethod.Read.All","UserAuthenticationMethod.ReadWrite","UserAuthenticationMethod.ReadWrite.All"

##### The value for phoneAuthenticationMethodId is 3179e48a-750b-4051-897c-87b9720928f7

$phoneAuthenticationMethodId = "3179e48a-750b-4051-897c-87b9720928f7"

#### Get the User Details

$userId = "objectid_of_the_user_in_Entra_ID"

#### validate the value for SmsSignInState

$smssignin = Get-MgUserAuthenticationPhoneMethod -UserId $userId


    if($smssignin.SmsSignInState -eq "ready"){   
      #### Disable Sms Sign-In for the user is set to ready

      Disable-MgUserAuthenticationPhoneMethodSmsSignIn -UserId $userId -PhoneAuthenticationMethodId $phoneAuthenticationMethodId
      Write-Host "SMS sign-in disabled for the user" -ForegroundColor Green
    }
    else{
    Write-Host "SMS sign-in status not set or found for the user " -ForegroundColor Yellow
    }



##### End the script
```

### Symptom - Group skipped due to EntityTypeNotSupported

Group is skipped from synchronization because EntityTypeNotSupported.

[![Screenshot that shows a group being skipped due to EntityTypeNotSupported.](https://learn.microsoft.com/en-us/entra/identity/multi-tenant-organizations/media/cross-tenant-synchronization-configure/group-skipped-message.png)](https://learn.microsoft.com/en-us/entra/identity/multi-tenant-organizations/media/cross-tenant-synchronization-configure/group-skipped-message.png#lightbox)

**Cause**

This message likely indicates that group synchronization is not enabled in the source tenant.

**Solution**

In the source tenant, on the **Provisioning** page, under the **Mappings** section, select **Provision Microsoft Entra ID Groups** to open the **Attribute Mapping** page. Make sure the **Enabled** toggle is set to **Yes**. For more information, see [Step 8: \(Optional\) Define who is in scope for provisioning with scoping filters](#step-8-optional-define-who-is-in-scope-for-provisioning-with-scoping-filters).

### Symptom - Users fail to provision with error AzureActiveDirectoryForbidden

Users in scope fail to provision. The provisioning logs details include the following error message:

`Guest invitations not allowed for your company. Contact your company administrator for more details.`

**Cause**

This error indicates the Guest invite settings in the target tenant are configured with the most restrictive setting: "No one in the organization can invite guest users including admins \(most restrictive\)".

**Solution**

Change the Guest invite settings in the target tenant to a less restrictive setting. For more information, see [Configure external collaboration settings](https://learn.microsoft.com/en-us/entra/external-id/external-collaboration-settings-configure).

### Symptom - UserPrincipalName does not update for existing B2B users in pending acceptance state

When a user is first invited through manual B2B invitation, the invitation is sent to the source user mail address. As a result the guest user in the target tenant is created with a UserPrincipalName \(UPN\) prefix using the source mail value property. There are environments where the source user object properties, UPN and Mail, have different values, for example Mail == user.mail@domain.com and UPN == user.upn@otherdomain.com. In this case, the guest user in the target tenant will be created with the UPN as *user.mail\_domain.com#EXT#@contoso.onmicrosoft.com.*

The issue raises when then the source object is put in scope for cross-tenant sync and the expectation is that besides other properties, the UPN prefix of the target guest user **would be updated to match the UPN of the source user** \(using the example above the value would be: *user.upn\_otherdomain.com#EXT#@contoso.onmicrosoft.com*\). However, that's not happening during incremental sync cycles, and the change is ignored.

**Cause**

This issue happens when the **B2B user which was manually invited into the target tenant didn't accept or redeem the invitation**, so its state is in pending acceptance. When a user is invited through an email, an object is created with a set of attributes that are populated from the mail, one of them is the UPN, which is pointing to the mail value of the source user. If later you decide to add the user to the scope for cross-tenant sync, the system will try to join the source user with a B2B user in target tenant based on the alternativeSecurityIdentifier attribute, but the previously created user doesn't have an alternativeSecurityIdentifier property populated because the invitation was not redeemed. So, the system won't consider this to be a new user object and won't update the UPN value. The UserPrincipalName isn't updated in the following scenarios:

1. The UPN and mail are different for a user when was manually invited.
2. The user was invited prior to enabling cross-tenant sync.
3. The user never accepted the invitation, so they are in "pending acceptance state".
4. The user is brought into scope for cross-tenant sync.

**Solution**

To resolve the issue, run on-demand provisioning for the affected users to update the UPN. You can also restart provisioning to update the UPN for all affected users. Note that this triggers an initial cycle, which can take a long time for large tenants. To get a list of manual invited users in pending acceptance state, you can use a script, see the following sample.

```powershell
Connect-MgGraph -Scopes "User.Read.All"
$users = Get-MgUser -Filter "userType eq 'Guest' and externalUserState eq 'PendingAcceptance'" 
$users | Select-Object DisplayName, UserPrincipalName | Export-Csv "C:\Temp\GuestUsersPending.csv"
```

Then you can use [provisionOnDemand with PowerShell](https://learn.microsoft.com/en-us/graph/api/synchronization-synchronizationjob-provisionondemand?tabs=powershell#request) for each user. The rate limit for this API is 5 requests per 10 seconds. For more information, see [Known limitations for on-demand provisioning](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/provision-on-demand?pivots=cross-tenant-synchronization#known-limitations).

## Next steps

- [Tutorial: Reporting on automatic user account provisioning](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/check-status-user-account-provisioning)
- [Managing user account provisioning for enterprise apps in the Azure portal](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/configure-automatic-user-provisioning-portal)
- [What is single sign-on in Microsoft Entra ID?](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/what-is-single-sign-on)
