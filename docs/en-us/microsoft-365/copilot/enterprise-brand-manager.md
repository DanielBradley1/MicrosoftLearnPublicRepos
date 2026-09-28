<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/enterprise-brand-manager -->
<!-- Sitemap-Last-Modified: 2026-07-14 -->

# Enterprise brand manager policy setup

Your organization can enable their brand managers to set up and publish organization or official brand kits using the **Create** tab on [microsoft365.com](https://microsoft365.com). These brand kits can contain multiple logos, color palettes, fonts, images, and templates pertaining to a certain brand.

Once published, the brand kit is available to all users in the tenant in the **Create** tab on [microsoft365.com](https://microsoft365.com). They can use these brand kits to generate branded artifacts or manually add brand assets to existing designs and images.

To enable this functionality, admins must configure the Enterprise Brand Manager policy, which involves:

- Defining a mail-enabled security group that includes the brand managers.
- Assigning responsibility to these brand managers for creating, managing, and publishing the official or organizational brand kits.

## Pre-requisite: Creating a mail-enabled security group for brand managers

1. Navigate to admin.microsoft.com and sign in using an Administrator account.
2. In the left pane, navigate to the **Active teams and groups** option from **Teams and groups** menu.
3. Then select the **Security groups** option on the page and click on **Add a mail-enabled security group**.

   [![Screenshot showing the Security groups menu on Active teams & groups page.](https://learn.microsoft.com/en-us/microsoft-365/copilot/media/enterprise-brand-manager/image.png)](https://learn.microsoft.com/en-us/microsoft-365/copilot/media/brand-manager/brand-manager-policy.png#lightbox)
4. Give a name for the mail enabled security group you wish to create and a description \(optional\).
5. **Assign owners** and select the names or groups you wish to assign the owner permission to and click ‘Add’.
6. **Add members** and select the names or groups you wish to add as members and click ‘Add’. These users obtain publish and edit access to official kits.

   [![Screenshot showing the names selected who have been assigned members in the mail enabled security group.](https://learn.microsoft.com/en-us/microsoft-365/copilot/media/enterprise-brand-manager/image1.png)](https://learn.microsoft.com/en-us/microsoft-365/copilot/media/brand-manager/brand-manager-policy.png#lightbox)
7. Enter the email address you wish to use for the mail enabled security group. Note the email address as this email is needed for the policy setup later.
8. Review the details and click on Create group.
9. You see a confirmation that your mail enabled security group has successfully been created.

Note

Only the members of the email enabled security group have access to publish and edit official kits. Owners of the group only are able to manage the group but don't get the access to official kit editing and publishing.

## Creating and setting up the Enterprise Brand Manager policy

Follow these steps to set up the policy for your organization:

1. Navigate to [Config.office.com](https://config.office.com/) and sign in using an Administrator account.
2. Under Customization, select **Policy Management**.
3. Select your existing tenant level policy with scope set to **Apply to all users** or create a new tenant policy with scope set to **Apply to all users**.
4. Go to the **Policies** tab.
5. Use the search box to search for **Brand Manager**. Select the **Elevated role for Brand Managers** policy.

   [![Screenshot showing the Policy Management page to configure settings.](https://learn.microsoft.com/en-us/microsoft-365/copilot/media/brand-manager/brand-manager-policy.png)](https://learn.microsoft.com/en-us/microsoft-365/copilot/media/brand-manager/brand-manager-policy.png#lightbox)
6. Set the policy to **Enabled**. By default, it is set as **Not configured**.
7. In the **Security group email address** field, provide the email address for the brand managers security group for your tenant.

   ![Screenshot showing the Security group email text box filled with an email.](https://learn.microsoft.com/en-us/microsoft-365/copilot/media/brand-manager/brand-manager-role.png)
8. Select **Apply**.
9. Go to **Review and Publish** tab, verify the details, and update them.
10. Click on **Done**.
11. On the **Policy Management page**, you see the policy you created listed, **ensure that scope is listed as Tenant**.
12. Select the policy and click on ‘Reorder priority’.

    [![Screenshot showing the policy created recently listed under Policy management page.](https://learn.microsoft.com/en-us/microsoft-365/copilot/media/enterprise-brand-manager/image2.png)](https://learn.microsoft.com/en-us/microsoft-365/copilot/media/brand-manager/brand-manager-policy.png#lightbox)
13. Update the priority to ‘0’ and save.

Once configured, the brand managers start seeing a publish button in their brand kits to share their brand kits at the organization level. To set up the brand kit, see [Create and manage official brand kits in Microsoft Copilot](https://support.microsoft.com/topic/create-and-manage-official-brand-kits-in-microsoft-365-copilot-app-6bc8a5a7-5697-466b-9e1f-302a38d44afc).

Important

Ensure the policy has following configurations for a correct setup

1. The policy scope is set to **Tenant**
2. The policy is set to **priority '0'**
3. The security group provided for brand managers in the policy is correct

It could take up to 24 hours after a policy is created for brand managers to be able to create and edit and official brand kits.
