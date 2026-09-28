<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/linkedinsalesnavigator-provisioning-tutorial -->
<!-- Sitemap-Last-Modified: 2026-03-18 -->

# Configure LinkedIn Sales Navigator for automatic user provisioning

The objective of this article is to show you the steps you need to perform in LinkedIn Sales Navigator and Microsoft Entra ID to automatically provision and deprovision user accounts from Microsoft Entra ID to LinkedIn Sales Navigator.

## Prerequisites

The scenario outlined in this article assumes that you already have the following items:

- A Microsoft Entra user account with an active subscription. If you don't already have one, you can [Create an account for free](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
- One of the following roles:

  - [Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#application-administrator)
  - [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator)
  - [Application Owner](https://learn.microsoft.com/en-us/entra/fundamentals/users-default-permissions#owned-enterprise-applications).

- A LinkedIn Sales Navigator tenant
- An administrator account in LinkedIn Sales Navigator with access to the LinkedIn Account Center

Note

Microsoft Entra ID integrates with LinkedIn Sales Navigator using the SCIM protocol.

## Assigning users to LinkedIn Sales Navigator

Microsoft Entra ID uses a concept called "assignments" to determine which users should receive access to selected apps. In the context of automatic user account provisioning, only the users and groups that have been "assigned" to an application in Microsoft Entra ID is synchronized.

Before configuring and enabling the provisioning service, you need to decide what users and/or groups in Microsoft Entra ID represent the users who need access to LinkedIn Sales Navigator. Once decided, you can assign these users to LinkedIn Sales Navigator by following the instructions here:

[Assign a user or group to an enterprise app](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/assign-user-or-group-access-portal)

### Important tips for assigning users to LinkedIn Sales Navigator

- It's recommended that a single Microsoft Entra user be assigned to LinkedIn Sales Navigator to test the provisioning configuration. Additional users and/or groups might be assigned later.
- When assigning a user to LinkedIn Sales Navigator, you must select the **User** role in the assignment dialog. The "Default Access" role doesn't work for provisioning.

## Configuring user provisioning to LinkedIn Sales Navigator

This section guides you through connecting your Microsoft Entra ID to LinkedIn Sales Navigator's SCIM user account provisioning API, and configuring the provisioning service to create, update, and disable assigned user accounts in LinkedIn Sales Navigator based on user and group assignment in Microsoft Entra ID.

Tip

You might also choose to enable SAML-based single sign-on for LinkedIn Sales Navigator, following the instructions provided in the [Azure portal](https://portal.azure.com). Single sign-on can be configured independently of automatic provisioning, though these two features complement each other.

### To configure automatic user account provisioning to LinkedIn Sales Navigator in Microsoft Entra ID:

The first step is to retrieve your LinkedIn access token. If you're an Enterprise administrator, you can self-provision an access token. In your account center, go to **Settings > Global Settings** and open the **SCIM Setup** panel.

Note

If you're accessing the account center directly rather than through a link, you can reach it using the following steps.

1. Sign in to Account Center.
2. Select **Admin** > **Admin Settings** .
3. Select **Advanced Integrations** on the left sidebar. You're directed to the account center.
4. Select **+ Add new SCIM configuration** and follow the procedure by filling in each field.

   Note

   When auto-assign licenses option isn't enabled, it means that only user data is synced.

   ![Screenshot shows the LinkedIn Account Center Global Settings.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/linkedinsalesnavigator-provisioning-tutorial/linkedin_1.png)


   Note


   When auto-license assignment is enabled, you need to note the application instance and license type. Licenses are assigned on a first come, first serve basis until all the licenses are taken.


   ![Screenshot shows the S C I M Setup page.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/linkedinsalesnavigator-provisioning-tutorial/linkedin_2.png)

5. Select **Generate token**. You should see your access token display under the **Access token** field.
6. Save your access token to your clipboard or computer before leaving the page.
7. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
8. Browse to **Entra ID** > **Enterprise apps**
9. If you have already configured LinkedIn Sales Navigator for single sign-on, search for your instance of LinkedIn Sales Navigator using the search field. Otherwise, select **Add** and search for **LinkedIn Sales Navigator** in the application gallery. Select LinkedIn Sales Navigator from the search results, and add it to your list of applications.
10. Select your instance of LinkedIn Sales Navigator, select the **Provisioning** tab.

    ![Provisioning tab](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/provisioning.png)

11. Select **+ New configuration**.

    ![Screenshot of Provisioning tab automatic.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/application-provisioning.png)

12. Fill in the following fields under **Admin Credentials** :

    - In the **Tenant URL** field, enter [https://developer.linkedin.com](https://developer.linkedin.com).
    - In the **Secret Token** field, enter the access token you generated in step 1 and select **Test Connection** .
    - You should see a success notification on the upper-right side of your portal.


    ![Screenshot of Provisioning test connection.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/provisioning-test-connection.png)

13. Select **Create** to create your configuration.
14. Select **Properties** on the **Overview** page.
15. Select the **Edit** icon to edit the properties. Enable notification emails and provide an email to receive quarantine emails. Enable accidental deletions prevention. Select **Apply** to save the changes.

    ![Screenshot of Provisioning properties.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/provisioning-properties.png)

16. Select **Attribute Mapping** in the left panel and select **users**.
17. Review the user and group attributes that's synchronized from Microsoft Entra ID to LinkedIn Sales Navigator. The attributes selected as **Matching** properties are used to match the user accounts and groups in LinkedIn Sales Navigator for update operations. Select the Save button to commit any changes.

    ![Screenshot shows Mappings, including Attribute Mappings.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/linkedinsalesnavigator-provisioning-tutorial/linkedin_4.png)

18. To configure scoping filters, refer to the following instructions provided in the [Scoping filter article](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts).
19. Use [on-demand provisioning](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/provision-on-demand) to validate sync with a small number of users before deploying more broadly in your organization.
20. When you're ready to provision, select **Start Provisioning** from the **Overview** page.

## Monitor your deployment

Once you configure provisioning, use the following resources to monitor your deployment:

1. Use the [provisioning logs](https://learn.microsoft.com/en-us/entra/identity/monitoring-health/concept-provisioning-logs) to determine which users are provisioned successfully or unsuccessfully
2. Check the [progress bar](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/application-provisioning-when-will-provisioning-finish-specific-user) to see the status of the provisioning cycle and how close it's to completion
3. If the provisioning configuration seems to be in an unhealthy state, the application goes into quarantine. Learn more about quarantine states the [application provisioning quarantine status](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/application-provisioning-quarantine-status) article.

## Additional Resources

- [Managing user account provisioning for Enterprise Apps](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/configure-automatic-user-provisioning-portal)
- [What is application access and single sign-on with Microsoft Entra ID?](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/what-is-single-sign-on)
