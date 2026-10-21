<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/copilot-restrict-brand-kit-creation -->
<!-- Sitemap-Last-Modified: 2026-06-12 -->

# Configure brand kit governance and organizational assets

Brand kits can include logos, color palettes, fonts, images, and templates. Users can use these assets to create branded content or add approved brand assets to existing designs, presentations, and images.

Brand kit policies control who can create personal brand kits and who can publish or manage official brand kits. Configure each policy according to your organization's asset management and governance requirements.

Microsoft Copilot provides two independent policies for brand kit governance:

| Policy | Controls | Who receives access |
| --- | --- | --- |
| [Enterprise Brand Manager policy](#configure-the-enterprise-brand-manager-policy) | Who can publish, edit, and manage official brand kits. | Members of the brand manager mail-enabled security group specified in the policy. |
| [Restrict brand kit creation policy](#configure-the-restrict-brand-kit-creation-policy) | Who can create and edit personal brand kits. | Members of the mail-enabled security group specified in the policy. |

Important

The policies are independent. To publish a personal brand kit as an official brand kit, a user must satisfy both policy checks. For more information, see [Verify policy behavior](#verify-policy-behavior).

## Prerequisites

Before users can create and publish brand kits, complete the following prerequisites:

- [Create an organization assets library](https://learn.microsoft.com/en-us/sharepoint/organization-assets-library) to connect to Copilot.
- Make sure that you're an administrator with the privileges required to manage groups and policy configurations. For more information, see [About admin roles in the Microsoft 365 admin center](https://learn.microsoft.com/en-us/microsoft-365/admin/add-users/about-admin-roles).
- Create a separate [mail-enabled security group for brand managers](https://learn.microsoft.com/en-us/exchange/recipients-in-exchange-online/manage-mail-enabled-security-groups#use-the-eac-to-create-a-mail-enabled-security-group) who can publish and manage official brand kits.
- Create a [mail-enabled security group](https://learn.microsoft.com/en-us/exchange/recipients-in-exchange-online/manage-mail-enabled-security-groups#use-the-eac-to-create-a-mail-enabled-security-group) for users who can create and edit personal brand kits.

Note

The same users can be members of both the brand manager security group and the user security group if that configuration matches your governance model.

Group membership grants policy access. Group owners can manage the group, but ownership alone doesn't grant permission to publish or edit official brand kits.

## Create a mail-enabled security group for brand managers

Create a mail-enabled security group for the brand managers who can publish and manage official brand kits.

1. Sign in to the [Microsoft 365 admin center](https://go.microsoft.com/fwlink/p/?linkid=2024339) with an administrator account.
2. Go to **Teams and groups** > **Active teams and groups**, and then select **Security groups**.
3. Select **Add a mail-enabled security group**, and enter a name and optional description.
4. Select the group owners, and then select **Add**.
5. Select the group members, and then select **Add**. These members receive permission to edit and publish official brand kits.
6. Enter an email address for the group. You use this address when you configure the [Enterprise Brand Manager policy](#configure-the-enterprise-brand-manager-policy).
7. Review the information, and then select **Create group**.

## Configure the Enterprise Brand Manager policy

After you create the mail-enabled security group for brand managers, configure the Enterprise Brand Manager policy.

1. Go to the [Microsoft 365 Apps admin center](https://config.office.com/) and sign in with an administrator account.
2. In the left navigation, select **Customization** > **Policy Management**.
3. Select an existing tenant-level policy with the scope **Apply to all users**. If this policy doesn't exist, [create a tenant-level policy](#create-a-tenant-level-policy).
4. Select the **Policies** tab.
5. Search for **Brand Manager**, and then select **Elevated role for Brand Managers**.
6. Set the policy to **Enabled**. By default, the policy is set to **Not configured**.
7. In **Security group email address**, enter the email address of the brand manager security group.
8. Select **Apply**.
9. Go to the **Review and Publish** tab, verify the details, and update the policy.
10. Select **Done**.
11. On the **Policy Management** page, verify that the policy scope is **Tenant**.
12. Select the policy, and then select **Reorder priority**.
13. Set the priority to **0**, and then select **Save**.

Important

Verify that the policy has the following configuration:

- The policy scope is set to **Tenant**.
- The policy priority is set to **0**.
- The policy specifies the correct security group for brand managers.

After the policy is configured, brand managers see a publish button in their brand kits that they can use to share brand kits with the organization. For information about creating a brand kit, see [Create and manage official brand kits in Microsoft 365 Copilot](https://support.microsoft.com/topic/create-and-manage-official-brand-kits-in-microsoft-365-copilot-app-6bc8a5a7-5697-466b-9e1f-302a38d44afc).

Note

Policy changes can take up to 24 hours to take effect.

## Create a tenant-level policy

If a tenant-level policy that applies to all users doesn't exist, create one.

1. Select **Create** or **+ Create**.
2. On the **Start with the basics** page, enter a name and description for the policy, and then select **Next**. For example:

   - **Name**: Apply to all users
   - **Description**: Policy that applies to all users

3. On the **Choose the scope** page, under **Select the scope**, select **This policy configuration applies to all users**, and then select **Next**.
4. On the **Configure Settings** page, select **Next**.
5. On the **Review configuration and create** page, review the settings, and then select **Create**.
6. On the **Policy configuration created** page, select **Done**.
7. On the **Policy configurations** page, select the policy to edit it. Select the policy itself instead of selecting its checkbox.

## Configure the Restrict brand kit creation policy

Important

Before you configure this policy, create a [mail-enabled security group](https://learn.microsoft.com/en-us/exchange/recipients-in-exchange-online/manage-mail-enabled-security-groups#use-the-eac-to-create-a-mail-enabled-security-group) that includes the users who can create and edit personal brand kits.

Configure the policy to specify who can create and edit personal brand kits. For the expected results of each group-membership configuration, see [Verify policy behavior](#verify-policy-behavior).

1. Sign in to the [Microsoft 365 Apps admin center](https://config.office.com/).
2. In the left navigation, select **Customization** > **Policy Management**.
3. Select an existing tenant-level policy with the scope **This policy configuration applies to all users**. Select the policy itself instead of selecting its checkbox. If this policy doesn't exist, [create a tenant-level policy](#create-a-tenant-level-policy).
4. On the **Start with the basics** page, select **Next**.
5. On the **Choose the scope** page, verify that the scope is **This policy configuration applies to all users**, and then select **Next**.
6. On the **Configure Settings** page:

   1. Search for **brand kit**.
   2. Select **Restrict brand kit creation**.
   3. In the **Restrict brand kit creation** pane, set **Configuration setting** to **Enabled**.
   4. Under **Additional setting**, enter the email address of the security group whose members can create brand kits in **Security group email address**. Users outside this group don't see the option to create a brand kit.
   5. Select **Apply**.

7. On the **Configure Settings** page, select **Next**.
8. On the **Review configuration and update** page, review the settings, and then select **Update**.
9. On the **Policy configuration updated** page, select **Done**.

For information about creating and managing brand kits, see [Create and manage official brand kits in Microsoft 365 Copilot](https://support.microsoft.com/topic/create-and-manage-official-brand-kits-in-microsoft-365-copilot-app-6bc8a5a7-5697-466b-9e1f-302a38d44afc).

## Verify policy behavior

The following table shows the expected experience for each combination of group membership.

| User | Creation group | Brand manager group | Expected experience |
| --- | --- | --- | --- |
| A | No | No | Can use published official brand kits but can't create or edit brand kits. |
| B | Yes | No | Can create personal brand kits but can't publish them as official brand kits. |
| C | No | Yes | Can't create or edit brand kits because the creation policy requirement isn't satisfied. |
| D | Yes | Yes | Can create personal brand kits and publish or manage official brand kits. |

If a user who isn't in the permitted group receives a shared brand kit with edit rights, the user can only view the kit. When the user opens it, the following message appears:

> Your admin has restricted the rights for brand kit creation and editing. Please contact your admin for permission.

## Connect an organizational asset library to Copilot

Note

You must [create an organization assets library](https://learn.microsoft.com/en-us/sharepoint/organization-assets-library) before you [connect an organizational asset library to Copilot](https://learn.microsoft.com/en-us/sharepoint/connect-organizational-asset-libraries-to-copilot).

An organizational asset library is a central collection of approved brand assets such as logos, illustrations, and other visuals. After an administrator [connects the library to Copilot](https://learn.microsoft.com/en-us/sharepoint/connect-organizational-asset-libraries-to-copilot) and configures it as searchable, users in the organization can discover and use the assets in Microsoft Copilot.

The assets are available to the organization in the following experiences:

- **Create experience**: Users can access organizational assets while creating content in the Microsoft Copilot app. In the **Create** experience, users can open the **Visuals** pane and find approved assets under a label based on the tenant name. For more information, see [Create and manage official brand kits in Microsoft 365 Copilot](https://support.microsoft.com/topic/create-and-manage-official-brand-kits-in-microsoft-365-copilot-app-6bc8a5a7-5697-466b-9e1f-302a38d44afc).
- **Copilot Chat in PowerPoint and Word**: Users can access approved brand assets through Copilot Chat.
