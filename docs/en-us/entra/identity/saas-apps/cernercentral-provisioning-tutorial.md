<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/cernercentral-provisioning-tutorial -->
<!-- Sitemap-Last-Modified: 2026-03-05 -->

# Configure Cerner Central for automatic user provisioning

The objective of this article is to show you the steps you need to perform in Cerner Central and Microsoft Entra ID to automatically provision and de-provision user accounts from Microsoft Entra ID to a user roster in Cerner Central.

## Prerequisites

The scenario outlined in this article assumes that you already have the following items:

- A Microsoft Entra user account with an active subscription. If you don't already have one, you can [Create an account for free](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
- One of the following roles:

  - [Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#application-administrator)
  - [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator)
  - [Application Owner](https://learn.microsoft.com/en-us/entra/fundamentals/users-default-permissions#owned-enterprise-applications).

- A Cerner Central tenant

Note

Microsoft Entra ID integrates with Cerner Central using the SCIM protocol.

## Assigning users to Cerner Central

Microsoft Entra ID uses a concept called "assignments" to determine which users should receive access to selected apps. In the context of automatic user account provisioning, only the users and groups that have been "assigned" to an application in Microsoft Entra ID are synchronized.

Before configuring and enabling the provisioning service, you should decide what users and/or groups in Microsoft Entra ID represent the users who need access to Cerner Central. Once decided, you can assign these users to Cerner Central by following the instructions here:

[Assign a user or group to an enterprise app](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/assign-user-or-group-access-portal)

### Important tips for assigning users to Cerner Central

- It's recommended that a single Microsoft Entra user be assigned to Cerner Central to test the provisioning configuration. Additional users and/or groups may be assigned later.
- Once initial testing is complete for a single user, Cerner Central recommends assigning the entire list of users intended to access any Cerner solution \(not just Cerner Central\) to be provisioned to Cerner’s user roster. Other Cerner solutions leverage this list of users in the user roster.
- When assigning a user to Cerner Central, you must select the **User** role in the assignment dialog. Users with the "Default Access" role are excluded from provisioning.

## Configuring user provisioning to Cerner Central

This section guides you through connecting your Microsoft Entra ID to Cerner Central’s User Roster using Cerner's SCIM user account provisioning API, and configuring the provisioning service to create, update, and disable assigned user accounts in Cerner Central based on user and group assignment in Microsoft Entra ID.

Tip

You may also choose to enable SAML-based single sign-on for Cerner Central, following the instructions provided in the [Azure portal](https://portal.azure.com). Single sign-on can be configured independently of automatic provisioning, though these two features complement each other. For more information, see the [Cerner Central single sign-on article](https://learn.microsoft.com/en-us/entra/identity/saas-apps/cernercentral-tutorial).

### To configure automatic user account provisioning to Cerner Central in Microsoft Entra ID:

In order to provision user accounts to Cerner Central, you’ll need to request a Cerner Central system account from Cerner, and generate an OAuth bearer token that Microsoft Entra ID can use to connect to Cerner's SCIM endpoint. It's also recommended that the integration be performed in a Cerner sandbox environment before deploying to production.

1. The first step is to ensure the people managing the Cerner and Microsoft Entra integration have a CernerCare account, which is required to access the documentation necessary to complete the instructions. If necessary, use the URLs below to create CernerCare accounts in each applicable environment.

   - Sandbox: [https://sandboxcernercare.com/accounts/create](https://sandboxcernercare.com/accounts/create)
   - Production: [https://cernercare.com/accounts/create](https://cernercare.com/accounts/create)

2. Next, a system account must be created for Microsoft Entra ID. Use the instructions below to request a System Account for your sandbox and production environments.

   - Instructions: [https://wiki.cerner.com/display/public/CernerCentral/Requesting+a+System+Account+in+System+Account+Management](https://wiki.cerner.com/display/public/CernerCentral/Requesting+a+System+Account+in+System+Account+Management)
   - Sandbox: [https://sandboxcernercentral.com/system-accounts/](https://sandboxcernercentral.com/system-accounts/)
   - Production: [https://cernercentral.com/system-accounts/](https://cernercentral.com/system-accounts/)

3. Next, generate an OAuth bearer token for each of your system accounts. To do this, follow the instructions below.

   - Instructions: [https://wiki.ucern.com/display/public/reference/Accessing+Cerner%27s+Web+Services+Using+A+System+Account+Bearer+Token](https://wiki.ucern.com/display/public/reference/Accessing+Cerner%27s+Web+Services+Using+A+System+Account+Bearer+Token)
   - Sandbox: [https://sandboxcernercentral.com/system-accounts/](https://sandboxcernercentral.com/system-accounts/)
   - Production: [https://cernercentral.com/system-accounts/](https://cernercentral.com/system-accounts/)

4. Finally, you need to acquire User Roster Realm IDs for both the sandbox and production environments in Cerner to complete the configuration. For information on how to acquire this, see: [https://wiki.ucern.com/display/public/reference/Publishing+Identity+Data+Using+SCIM](https://wiki.ucern.com/display/public/reference/Publishing+Identity+Data+Using+SCIM).
5. Now you can configure Microsoft Entra ID to provision user accounts to Cerner. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
6. Browse to **Entra ID** > **Enterprise apps** > **All applications**.
7. If you have already configured Cerner Central for single sign-on, search for your instance of Cerner Central using the search field. Otherwise, select **Add** and search for **Cerner Central** in the application gallery. Select Cerner Central from the search results, and add it to your list of applications.
8. Select your instance of Cerner Central, then select the **Provisioning** tab.
9. Set **+ New configuration**.

   ![Screenshot of Provisioning tab automatic.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/application-provisioning.png)


   ![Screenshot of the Provisioning Mode dropdown list with the Automatic option called out.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/provisioning-automatic.png)

10. Fill in the following fields under **Admin Credentials**:

    - In the **Tenant URL** field, enter a URL in the format below, replacing "User-Roster-Realm-ID" with the realm ID you acquired in step #4.

    > Sandbox: `https://user-roster-api.sandboxcernercentral.com/scim/v1/Realms/User-Roster-Realm-ID/`
    > 
    > Production: `https://user-roster-api.cernercentral.com/scim/v1/Realms/User-Roster-Realm-ID/`


    - In the **Secret Token** field, enter the OAuth bearer token you generated in step #3 and select **Test Connection**.
    - You should see a success notification on the upper-right side of your portal.

11. Select **Create** to create your configuration.
12. Select **Properties** in the **Overview** page.
13. Select the pencil to edit the properties. Enable notification emails and provide an email to receive quarantine emails. Enable accidental deletions prevention. Select **Apply** to save the changes.

    ![Screenshot of Provisioning properties.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/provisioning-properties.png)

14. Select **Attribute Mapping** in the left panel and select **users**.
15. Review the user and group attributes to be synchronized from Microsoft Entra ID to Cerner Central. The attributes selected as **Matching** properties are used to match the user accounts and groups in Cerner Central for update operations. Select the Save button to commit any changes.
16. To configure scoping filters, refer to the following instructions provided in the [Scoping filter article](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts).
17. Use [on-demand provisioning](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/provision-on-demand) to validate sync with a small number of users before deploying more broadly in your organization.
18. When you're ready to provision, select **Start Provisioning** from the **Overview** page.

## Step 6: Monitor your deployment

Once you configure provisioning, use the following resources to monitor your deployment:

1. Use the [provisioning logs](https://learn.microsoft.com/en-us/entra/identity/monitoring-health/concept-provisioning-logs) to determine which users are provisioned successfully or unsuccessfully
2. Check the [progress bar](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/application-provisioning-when-will-provisioning-finish-specific-user) to see the status of the provisioning cycle and how close it's to completion
3. If the provisioning configuration seems to be in an unhealthy state, the application goes into quarantine. Learn more about quarantine states the [application provisioning quarantine status](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/application-provisioning-quarantine-status) article.

## Additional resources

- [Cerner Central: Publishing identity data using Microsoft Entra ID](https://wiki.ucern.com/display/public/reference/Publishing+Identity+Data+Using+Azure+AD)
- [Tutorial: Configuring Cerner Central for single sign-on with Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/identity/saas-apps/cernercentral-tutorial)
- [Managing user account provisioning for Enterprise Apps](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/configure-automatic-user-provisioning-portal)
- [What is application access and single sign-on with Microsoft Entra ID?](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/what-is-single-sign-on)

## Related content

- [Learn how to review logs and get reports on provisioning activity](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/check-status-user-account-provisioning).
