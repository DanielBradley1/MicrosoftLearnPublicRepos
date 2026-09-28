<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/m-files-provisioning-tutorial -->
<!-- Sitemap-Last-Modified: 2026-04-30 -->

# Configure M-Files for automatic user provisioning with Microsoft Entra ID

This article describes the steps you need to perform in both M-Files and Microsoft Entra ID to configure automatic user provisioning. When configured, Microsoft Entra ID automatically provisions and deprovisions users and groups to [M-Files](https://www.m-files.com/) using the Microsoft Entra provisioning service. For important details on what this service does, how it works, and frequently asked questions, see [Automate user provisioning and deprovisioning to SaaS applications with Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/user-provisioning).

## Supported capabilities

- Create users in M-Files.
- Remove users in M-Files when they don't require access anymore.
- Keep user attributes synchronized between Microsoft Entra ID and M-Files.
- Provision groups and group memberships in M-Files.
- [Single sign-on](https://learn.microsoft.com/en-us/entra/identity/saas-apps/m-files-tutorial) to M-Files \(recommended\).

## Prerequisites

The scenario outlined in this article assumes that you already have the following prerequisites:

- [A Microsoft Entra tenant](https://learn.microsoft.com/en-us/entra/identity-platform/quickstart-create-new-tenant)
- One of the following roles: [Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#application-administrator), [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator), or [Application Owner](https://learn.microsoft.com/en-us/entra/fundamentals/users-default-permissions#owned-enterprise-applications).
- M-Files Cloud Subscription \(Classic Cloud isn't supported\).
- A user account in M-Files with the Subscription admin or Access admin access to [M-Files Manage](https://manage.m-files.com/).

## Step 1: Plan your provisioning deployment

1. Learn about [how the provisioning service works](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/user-provisioning).
2. Determine who's in [scope for provisioning](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts).
3. Determine what data to [map between Microsoft Entra ID and M-Files](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/customize-application-attributes).
4. The necessary mappings are predefined but you can map two additional data fields to M-Files.

## Step 2: Configure M-Files to support provisioning with Microsoft Entra ID

Before you set up user provisioning in M-Files, make sure that all vaults in your subscription have user synchronization disabled in M-Files Admin.

If you have previously configured user provisioning in M-Files Manage with your own Entra ID application, you can't change the configuration to use the M-Files application from the Microsoft Entra application gallery. If you want to use the M-Files application instead, delete the existing configuration from M-Files Manage and disable or delete the related Entra ID application. Then, follow these instructions to create the new configuration.

1. Log in to M-Files Manage at [https://manage.m-files.com](https://manage.m-files.com).
2. In the left-side page navigation, select **Provisioning**.
3. Go to the **Configuration** tab.
4. In **Create configuration for user provisioning**, select **Azure AD gallery app**.
5. Enter the necessary information.

   - In **Configuration name**, enter a unique name for the configuration.
   - Select **Default license type** for the provisioned users. All the provisioned users first get this license. You can change a user group's license type to a higher one after user groups have been provisioned. If there aren't enough available licenses of the default license type in the subscription, all the users don't get the license.

6. Select the copy icon \(![Screenshot of the Copy icon.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/m-files-provisioning-tutorial/icon.png) \) for each piece of data, that M-Files Manage created, and note down the values.

Note

The client secret isn't shown anywhere else when you close the dialog.

## Step 3: Add M-Files from the Microsoft Entra application gallery

Add M-Files from the Microsoft Entra application gallery to start managing provisioning to M-Files. If you have previously set up M-Files for SSO you can use the same application. However, we recommend that you create a separate app when testing out the integration initially. Learn more about adding an application from the gallery [here](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/add-application-portal).

## Step 4: Define who is in scope for provisioning

The Microsoft Entra provisioning service allows you to scope who is provisioned based on assignment to the application, or based on attributes of the user or group. If you choose to scope who is provisioned to your app based on assignment, you can use the [steps to assign users and groups to the application](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/assign-user-or-group-access-portal). If you choose to scope who is provisioned based solely on attributes of the user or group, you can [use a scoping filter](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts).

- Start small. Test with a small set of users and groups before rolling out to everyone. When scope for provisioning is set to assigned users and groups, you can control this by assigning one or two users or groups to the app. When scope is set to all users and groups, you can specify an [attribute based scoping filter](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts).
- If you need extra roles, you can [update the application manifest](https://learn.microsoft.com/en-us/entra/identity-platform/howto-add-app-roles-in-apps) to add new roles.

## Step 5: Configure automatic user provisioning to M-Files

This section guides you through the steps to configure the Microsoft Entra provisioning service to create, update, and disable users and/or groups in TestApp based on user and/or group assignments in Microsoft Entra ID.

### Configure automatic user provisioning for M-Files in Microsoft Entra ID

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps**.

   ![Screenshot of Enterprise applications blade.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/enterprise-applications.png)

3. In the applications list, select **M-Files**.

   ![Screenshot of the M-Files link in the Applications list.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/all-applications.png)

4. Select the **Provisioning** tab.

   ![Screenshot of the Manage options with the Provisioning option called out.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/provisioning.png)

5. Select **+ New configuration**.

   ![Screenshot of the New configuration option on the Provisioning page.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/application-provisioning.png)

6. Under the **Admin Credentials** section, enter your M-Files Tenant URL, Token Endpoint, Client Identifier and Client Secret. Select **Test Connection** to ensure Microsoft Entra ID can connect to M-Files. If the connection fails, make sure that the values you entered are correct and try again.

   ![Screenshot of Provisioning test connection.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/m-files-provisioning-tutorial/test-connection.png)

7. Select **Create** to create your configuration.
8. Select **Properties** on the **Overview** page.
9. Select the **Edit** icon to edit the properties. Enable notification emails and provide an email to receive quarantine notifications. Enable **Accidental deletions prevention**. Select **Apply** to save the changes.

   ![Screenshot of the Provisioning properties page.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/provisioning-properties.png)

10. **Optional**: If you want to synchronize additional user information, you can define two additional fields to be synchronized to M-Files Manage. The information is shown in **Additional information 1** and **Additional information 2** on the **User information** page.

    1. Under the **Mappings** section, select **Synchronize Microsoft Entra users to M-Files**.
    2. In the **Attribute-Mapping** section, select **Add new mapping**.
    3. Use these values:

       - **Mapping type**: **Direct**
       - **Source attribute**: Enter the Entra ID attribute
       - **Target attribute**: Select **urn:ietf:params:scim:schemas:extension:info:2.0:User:info1** or **urn:ietf:params:scim:schemas:extension:info:2.0:User:info2**
       - **Match objects using this attribute**: **No**
       - **Apply this mapping**: **Always**

    4. Select **Ok**.
    5. **Optional**: To synchronize two additional data fields to M-Files Manage, add a second mapping with the other available target attribute.


    Note


    It isn't recommended to make changes to the default attribute mappings.

11. To configure scoping filters, refer to the instructions provided in the [Scoping filter article](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts).
12. Use [on-demand provisioning](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/provision-on-demand) to validate sync with a small number of users before deploying more broadly in your organization.
13. When you're ready to provision, select **Start Provisioning** from the **Overview** page.

## Step 6: Monitor your deployment

Once you configure provisioning, use the following resources to monitor your deployment:

1. Use the [provisioning logs](https://learn.microsoft.com/en-us/entra/identity/monitoring-health/concept-provisioning-logs) to determine which users are provisioned successfully or unsuccessfully
2. Check the [progress bar](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/application-provisioning-when-will-provisioning-finish-specific-user) to see the status of the provisioning cycle and how close it's to completion
3. If the provisioning configuration seems to be in an unhealthy state, the application goes into quarantine. Learn more about quarantine states the [application provisioning quarantine status](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/application-provisioning-quarantine-status) article.

## More resources

- [Managing user account provisioning for Enterprise Apps](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/configure-automatic-user-provisioning-portal).
- [What is application access and single sign-on with Microsoft Entra ID?](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/what-is-single-sign-on).

## Related content

- When the user provisioning is complete, create links between the provisioned user groups and M-Files user groups in M-Files Manage. For instructions, refer to [M-Files Manage - User guide](https://m-files.my.site.com/s/article/mfiles-ka-385842).
- [Learn how to review logs and get reports on provisioning activity](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/check-status-user-account-provisioning).
