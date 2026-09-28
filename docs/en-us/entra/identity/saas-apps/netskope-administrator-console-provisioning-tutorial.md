<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/netskope-administrator-console-provisioning-tutorial -->
<!-- Sitemap-Last-Modified: 2026-09-16 -->

# Configure Netskope User Authentication for automatic user provisioning with Microsoft Entra ID

The objective of this article is to demonstrate the steps to be performed in Netskope User Authentication and Microsoft Entra ID to configure Microsoft Entra ID to automatically provision and de-provision users and/or groups to Netskope User Authentication.

Note

This article describes a connector built on top of the Microsoft Entra user provisioning service. For important details on what this service does, how it works, and frequently asked questions, see [Automate user provisioning and deprovisioning to SaaS applications with Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/user-provisioning).

## Prerequisites

The scenario outlined in this article assumes that you already have the following prerequisites:

- 

  - A Microsoft Entra user account with an active subscription. If you don't already have one, you can [Create an account for free](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
  - One of the following roles:

    - [Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#application-administrator)
    - [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator)
    - [Application Owner](https://learn.microsoft.com/en-us/entra/fundamentals/users-default-permissions#owned-enterprise-applications).

- [A Netskope User Authentication tenant](https://www.netskope.com/)
- A user account in Netskope User Authentication with Admin permissions.

## Assigning users to Netskope User Authentication

Microsoft Entra ID uses a concept called *assignments* to determine which users should receive access to selected apps. In the context of automatic user provisioning, only the users and/or groups that have been assigned to an application in Microsoft Entra ID are synchronized.

Before configuring and enabling automatic user provisioning, you should decide which users and/or groups in Microsoft Entra ID need access to Netskope User Authentication. Once decided, you can assign these users and/or groups to Netskope User Authentication by following the instructions here:

- [Assign a user or group to an enterprise app](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/assign-user-or-group-access-portal)

## Important tips for assigning users to Netskope User Authentication

- It's recommended that a single Microsoft Entra user is assigned to Netskope User Authentication to test the automatic user provisioning configuration. Additional users and/or groups may be assigned later.
- When assigning a user to Netskope User Authentication, you must select any valid application-specific role \(if available\) in the assignment dialog. Users with the **Default Access** role are excluded from provisioning.

## Set up Netskope User Authentication for provisioning

1. Sign in to your [Netskope User Authentication Admin Console](https://netskope.goskope.com/).
2. Navigate to **Home -> Settings -> Administration ->Administrators** and **Roles -> Service Account**.
3. Input the required details, select **OAuth2** as the type, and set the validity period \(in days\).
4. Click **Create**, then copy the generated **Client ID** and **Client Secret** you will need them later.

   ![Screenshot showing Oauth configuration.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/netskope-administrator-console-provisioning-tutorial/token.png)

## Add Netskope User Authentication from the gallery

Before configuring Netskope User Authentication for automatic user provisioning with Microsoft Entra ID, you need to add Netskope User Authentication from the Microsoft Entra application gallery to your list of managed SaaS applications.

**To add Netskope User Authentication from the Microsoft Entra application gallery, perform the following steps:**

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **New application**.
3. In the **Add from the gallery** section, type **Netskope User Authentication**, select **Netskope User Authentication** in the search box.
4. Select **Netskope User Authentication** from results panel and then add the app. Wait a few seconds while the app is added to your tenant. ![Screenshot of Netskope User Authentication in the results list.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/netskope-administrator-console-provisioning-tutorial/search-icon.png)

## Configuring automatic user provisioning to Netskope User Authentication

This section guides you through the steps to configure the Microsoft Entra provisioning service to create, update, and disable users and/or groups in Netskope User Authentication based on user and/or group assignments in Microsoft Entra ID.

Tip

You may also choose to enable SAML-based single sign-on for Netskope User Authentication by following the instructions provided in the [Netskope User Authentication Single sign-on article](https://learn.microsoft.com/en-us/entra/identity/saas-apps/netskope-cloud-security-tutorial). Single sign-on can be configured independently of automatic user provisioning, although these two features complement each other.

Note

To learn more about Netskope User Authentication's SCIM endpoint, refer [this](https://docs.google.com/document/d/1n9P_TL98_kd1sx5PAvZL2HS6MQAqkQqd-OSkWAAU6ck/edit#heading=h.prxq74iwdpon).

### To configure automatic user provisioning for Netskope User Authentication in Microsoft Entra ID:

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps**

   ![Enterprise applications blade](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/enterprise-applications.png)

3. In the applications list, select **Netskope User Authentication**.

   ![The Netskope User Authentication link in the Applications list](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/all-applications.png)

4. Select the **Provisioning** tab.

   ![Screenshot of the Manage options with the Provisioning option called out.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/provisioning.png)

5. Select **+ New configuration**.

   ![Screenshot of Provisioning tab automatic.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/application-provisioning.png)

6. Select **OAuth2 Client Credentials Grant** as the Authentication Method.

   a. Enter the **Client ID** and **Client Secret** retrieved from Netskope.

   b. Select **Test Connection** to ensure Microsoft Entra ID can connect to Netskope User Authentication.

   c. If the connection fails, ensure your Netskope User Authentication account has Admin permissions and try again.

   ![Screenshot of Token.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/netskope-administrator-console-provisioning-tutorial/oauth2-entra-configuration.png)

7. Select **Create** to create your configuration.
8. Select **Properties** on the **Overview** page.
9. In the **Notification Email** field, enter the email address of a person who should receive the provisioning error notifications and select the **Send an email notification when a failure occurs** check box.

   ![Screenshot of the Provisioning properties page.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/provisioning-properties.png)

10. Select **Attribute Mapping** in the left panel and select **users**.
11. Review the user attributes that are synchronized from Microsoft Entra ID to Netskope User Authentication in the **Attribute-Mapping** section. The attributes selected as **Matching** properties are used to match the user accounts in Netskope User Authentication for update operations. If you choose to change the [matching target attribute](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/customize-application-attributes), you need to ensure that the Netskope User Authentication API supports filtering users based on that attribute. Select the **Save** button to commit any changes.

    ![Screenshot of the Netskope User Authentication User Attributes.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/netskope-administrator-console-provisioning-tutorial/userattributes.png)

12. Review the group attributes that are synchronized from Microsoft Entra ID to Netskope User Authentication in the **Attribute Mapping** section. The attributes selected as **Matching** properties are used to match the groups in Netskope User Authentication for update operations. Select the **Save** button to commit any changes.

    ![Screenshot of the Netskope User Authentication Group Attributes.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/netskope-administrator-console-provisioning-tutorial/groupattributes.png)

13. To configure scoping filters, refer to the instructions provided in the [Scoping filter article](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts).
14. Use [on-demand provisioning](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/provision-on-demand) to validate sync with a small number of users before deploying more broadly in your organization.
15. When you're ready to provision, select **Start Provisioning** from the **Overview** page.

## Additional resources

- [Managing user account provisioning for Enterprise Apps](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/configure-automatic-user-provisioning-portal)
- [What is application access and single sign-on with Microsoft Entra ID?](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/what-is-single-sign-on)

## Related content

- [Learn how to review logs and get reports on provisioning activity](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/check-status-user-account-provisioning)
