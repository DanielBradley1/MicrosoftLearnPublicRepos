<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/linkedinelevate-provisioning-tutorial -->
<!-- Sitemap-Last-Modified: 2026-04-30 -->

# Configure LinkedIn Elevate for automatic user provisioning in Microsoft Entra ID

The objective of this article is to show you the steps you need to perform in LinkedIn Elevate and Microsoft Entra ID to automatically provision and de-provision user accounts from Microsoft Entra ID to LinkedIn Elevate.

## Prerequisites

The scenario outlined in this article assumes that you already have the following items:

- A Microsoft Entra user account with an active subscription. If you don't already have one, you can [Create an account for free](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
- One of the following roles:

  - [Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#application-administrator)
  - [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator)
  - [Application Owner](https://learn.microsoft.com/en-us/entra/fundamentals/users-default-permissions#owned-enterprise-applications).

- A LinkedIn Elevate tenant
- An administrator account in LinkedIn Elevates with access to the LinkedIn Account Center

Note

Microsoft Entra ID integrates with LinkedIn Elevate using the SCIM protocol.

## Step 1: Assign users to LinkedIn Elevate

Microsoft Entra ID uses a concept called "assignments" to determine which users should receive access to selected apps. In the context of automatic user account provisioning, only the users and groups that have been "assigned" to an application in Microsoft Entra ID is synchronized.

Before configuring and enabling the provisioning service, you need to decide what users and/or groups in Microsoft Entra ID represent the users who need access to LinkedIn Elevate. Once decided, you can assign these users to LinkedIn Elevate by following the instructions here:

[Assign a user or group to an enterprise app](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/assign-user-or-group-access-portal)

### Important tips for assigning users to LinkedIn Elevate

- It's recommended that a single Microsoft Entra user be assigned to LinkedIn Elevate to test the provisioning configuration. More users and/or groups may be assigned later.
- When assigning a user to LinkedIn Elevate, you must select the **User** role in the assignment dialog. The "Default Access" role doesn't work for provisioning.

## Step 2: Configure user provisioning to LinkedIn Elevate

This section guides you through connecting your Microsoft Entra ID to LinkedIn Elevate's SCIM user account provisioning API, and configuring the provisioning service to create, update disable assigned user accounts in LinkedIn Elevate based on user and group assignment in Microsoft Entra ID.

**Tip:** You may also choose to enable SAML-based single sign-on for LinkedIn Elevate, following the instructions provided in the [Azure portal](https://portal.azure.com). single sign-on can be configured independently of automatic provisioning, though these two features complement each other.

### Configure automatic user account provisioning to LinkedIn Elevate in Microsoft Entra ID

The first step is to retrieve your LinkedIn access token. If you're an Enterprise administrator, you can self-provision an access token. In your account center, go to **Settings > Global Settings** and open the **SCIM Setup** panel.

Note

If you're accessing the account center directly rather than through a link, you can reach it using the following steps.

1. Sign in to Account Center.
2. Select **Admin > Admin Settings** .
3. Select **Advanced Integrations** on the left sidebar. You're directed to the account center.
4. Select **+ Add new SCIM configuration** and follow the procedure by filling in each field.

   Note

   When auto-assign licenses isn't enabled, it means that only user data is synced.

   ![Screenshot shows the LinkedIn Account Center Global Settings.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/linkedinelevate-provisioning-tutorial/linkedin_elevate1.png)


   Note


   When auto-license assignment is enabled, you need to note the application instance and license type. Licenses are assigned on a first come, first serve basis until all the licenses are taken.


   ![Screenshot shows the S C I M Setup page.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/linkedinelevate-provisioning-tutorial/linkedin_elevate2.png)

5. Select **Generate token**. You should see your access token display under the **Access token** field.
6. Save your access token to your clipboard or computer before leaving the page.
7. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
8. Browse to **Entra ID** > **Enterprise apps**.
9. If you have already configured LinkedIn Elevate for single sign-on, search for your instance of LinkedIn Elevate using the search field. Otherwise, select **Add** and search for **LinkedIn Elevate** in the application gallery. Select LinkedIn Elevate from the search results, and add it to your list of applications.
10. Select your instance of LinkedIn Elevate, then select the **Provisioning** tab.
11. Select **+ New configuration**.
12. Fill in the following fields under **Admin Credentials** :

    - In the **Tenant URL** field, enter `https://api.linkedin.com`.
    - In the **Secret Token** field, enter the access token you generated in step 1 and select **Test Connection** .
    - You should see a success notification on the upper-right side of your portal.

13. Select **Create** to create your configuration.
14. Select **Properties** on the **Overview** page.
15. Select the **Edit** icon to edit the properties. Enable notification emails and provide an email to receive quarantine notifications. Enable **Accidental deletions prevention**. Select **Apply** to save the changes.
16. In the **Attribute Mappings** section, review the user and group attributes that are synchronized from Microsoft Entra ID to LinkedIn Elevate. The attributes selected as **Matching** properties are used to match the user accounts and groups in LinkedIn Elevate for update operations. Select the Save button to commit any changes.

    ![Screenshot shows Mappings, including Attribute Mappings.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/linkedinelevate-provisioning-tutorial/linkedin_elevate4.png)

17. To configure scoping filters, refer to the instructions provided in the [Scoping filter article](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts).
18. Use [on-demand provisioning](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/provision-on-demand) to validate sync with a small number of users before deploying more broadly in your organization.
19. When you're ready to provision, select **Start Provisioning** from the **Overview** page.

## Step 3: Monitor your deployment

Once you configure provisioning, use the following resources to monitor your deployment:

1. Use the [provisioning logs](https://learn.microsoft.com/en-us/entra/identity/monitoring-health/concept-provisioning-logs) to determine which users are provisioned successfully or unsuccessfully
2. Check the [progress bar](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/application-provisioning-when-will-provisioning-finish-specific-user) to see the status of the provisioning cycle and how close it's to completion
3. If the provisioning configuration seems to be in an unhealthy state, the application goes into quarantine. Learn more about quarantine states the [application provisioning quarantine status](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/application-provisioning-quarantine-status) article.

## More Resources

- [Managing user account provisioning for Enterprise Apps](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/configure-automatic-user-provisioning-portal)
- [What is application access and single sign-on with Microsoft Entra ID?](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/what-is-single-sign-on)
