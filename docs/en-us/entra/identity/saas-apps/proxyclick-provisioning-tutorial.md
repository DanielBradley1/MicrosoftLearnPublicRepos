<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/proxyclick-provisioning-tutorial -->
<!-- Sitemap-Last-Modified: 2026-03-31 -->

# Configure Proxyclick for automatic user provisioning with Microsoft Entra ID

The objective of this article is to demonstrate the steps to be performed in Proxyclick and Microsoft Entra ID to configure Microsoft Entra ID to automatically provision and de-provision users and/or groups to Proxyclick.

Note

This article describes a connector built on top of the Microsoft Entra user provisioning service. For important details on what this service does, how it works, and frequently asked questions, see [Automate user provisioning and deprovisioning to SaaS applications with Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/user-provisioning).

## Prerequisites

The scenario outlined in this article assumes that you already have the following prerequisites:

- A Microsoft Entra user account with an active subscription. If you don't already have one, you can [Create an account for free](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
- One of the following roles:

  - [Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#application-administrator)
  - [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator)
  - [Application Owner](https://learn.microsoft.com/en-us/entra/fundamentals/users-default-permissions#owned-enterprise-applications).

- [A Proxyclick tenant](https://www.proxyclick.com/pricing)
- A user account in Proxyclick with Admin permissions.

## Add Proxyclick from the gallery

Before configuring Proxyclick for automatic user provisioning with Microsoft Entra ID, you need to add Proxyclick from the Microsoft Entra application gallery to your list of managed SaaS applications.

**To add Proxyclick from the Microsoft Entra application gallery, perform the following steps:**

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **New application**.
3. In the **Add from the gallery** section, type **Proxyclick**, select **Proxyclick** in the search box.
4. Select **Proxyclick** from results panel and then add the app. Wait a few seconds while the app is added to your tenant.

   ![Diagram that shows Proxyclick in the results list.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/search-new-app.png)

## Assigning users to Proxyclick

Microsoft Entra ID uses a concept called *assignments* to determine which users should receive access to selected apps. In the context of automatic user provisioning, only the users and/or groups that have been assigned to an application in Microsoft Entra ID are synchronized.

Before configuring and enabling automatic user provisioning, you should decide which users and/or groups in Microsoft Entra ID need access to Proxyclick. Once decided, you can assign these users and/or groups to Proxyclick by following the instructions here:

- [Assign a user or group to an enterprise app](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/assign-user-or-group-access-portal)

### Important tips for assigning users to Proxyclick

- It's recommended that a single Microsoft Entra user is assigned to Proxyclick to test the automatic user provisioning configuration. Additional users and/or groups may be assigned later.
- When assigning a user to Proxyclick, you must select any valid application-specific role \(if available\) in the assignment dialog. Users with the **Default Access** role are excluded from provisioning.

## Configure automatic user provisioning to Proxyclick

This section guides you through the steps to configure the Microsoft Entra provisioning service to create, update, and disable users and/or groups in Proxyclick based on user and/or group assignments in Microsoft Entra ID.

Tip

You may also choose to enable SAML-based single sign-on for Proxyclick, following the instructions provided in the [Proxyclick single sign-on article](https://learn.microsoft.com/en-us/entra/identity/saas-apps/proxyclick-tutorial). Single sign-on can be configured independently of automatic user provisioning, though these two features complement each other.

### To configure automatic user provisioning for Proxyclick in Microsoft Entra ID

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps**

   ![Diagram that shows Enterprise applications blade.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/enterprise-applications.png)

3. In the applications list, select **Proxyclick**.

   ![Diagram that shows the Proxyclick link in the Applications list.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/all-applications.png)

4. Select the **Provisioning** tab.

   ![Screenshot of the Manage options with the Provisioning option called out.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/provisioning.png)

5. Select **+ New configuration**.

   ![Screenshot of Provisioning tab automatic.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/application-provisioning.png)

6. To retrieve the **Tenant URL** and **Secret Token** of your Proxyclick account, follow the steps mentioned later in the document.
7. Sign in to your [Proxyclick Admin Console](https://app.proxyclick.com/login//?destination=%2Fdefault). Navigate to **Settings** > **Integrations** > **Browse Marketplace**.

   ![Diagram that shows Proxyclick Settings.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/proxyclick-provisioning-tutorial/proxyclick09.png)


   ![Diagram that shows Proxyclick Integrations.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/proxyclick-provisioning-tutorial/proxyclick01.png)


   ![Diagram that shows Proxyclick Marketplace.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/proxyclick-provisioning-tutorial/proxyclick02.png)


   Select **Microsoft Entra ID**. Select **Install now**.


   ![Diagram that shows Proxyclick Microsoft Entra ID.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/proxyclick-provisioning-tutorial/proxyclick03.png)


   ![Diagram that shows Proxyclick Install.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/proxyclick-provisioning-tutorial/proxyclick04.png)


   Select **User Provisioning** and select **Start integration**.


   ![Diagram that shows Proxyclick User Provisioning.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/proxyclick-provisioning-tutorial/proxyclick05.png)


   The appropriate settings configuration UI should now show up under **Settings** > **Integrations**. Select **Settings** under **Microsoft Entra ID \(User Provisioning\)**.


   ![Diagram that shows Proxyclick Create.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/proxyclick-provisioning-tutorial/proxyclick06.png)


   You can find the **Tenant URL** and **Secret Token** here.


   ![Diagram that shows Proxyclick Create Token.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/proxyclick-provisioning-tutorial/proxyclick07.png)

8. Upon populating the fields shown in Step 5, select **Test Connection** to ensure Microsoft Entra ID can connect to Proxyclick. If the connection fails, ensure your Proxyclick account has Admin permissions and try again.

   ![Diagram that shows Token.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/provisioning-testconnection-tenanturltoken.png)

9. Select **Create** to create your configuration.
10. Select **Properties** on the **Overview** page.
11. Select the **Edit** icon to edit the properties. Enable notification emails and provide an email to receive quarantine emails. Enable accidental deletions prevention. Select **Apply** to save the changes.

    ![Screenshot of Provisioning properties.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/provisioning-properties.png)

12. Select **Attribute Mapping** in the left panel and select **users**.
13. Review the user attributes that are synchronized from Microsoft Entra ID to Proxyclick in the **Attribute Mapping** section. The attributes selected as **Matching** properties are used to match the user accounts in Proxyclick for update operations. Select the **Save** button to commit any changes.

    ![Diagram that shows Proxyclick User Attributes.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/proxyclick-provisioning-tutorial/proxyclick-user-attribute.png)

14. To configure scoping filters, refer to the instructions provided in the [Scoping filter article](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts).
15. Use [on-demand provisioning](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/provision-on-demand) to validate sync with a small number of users before deploying more broadly in your organization.
16. When you're ready to provision, select **Start Provisioning** from the **Overview** page.

## Monitor your deployment

Once you configure provisioning, use the following resources to monitor your deployment:

1. Use the [provisioning logs](https://learn.microsoft.com/en-us/entra/identity/monitoring-health/concept-provisioning-logs) to determine which users are provisioned successfully or unsuccessfully
2. Check the [progress bar](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/application-provisioning-when-will-provisioning-finish-specific-user) to see the status of the provisioning cycle and how close it's to completion
3. If the provisioning configuration seems to be in an unhealthy state, the application goes into quarantine. Learn more about quarantine states the [application provisioning quarantine status](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/application-provisioning-quarantine-status) article.

## Connector limitations

- Proxyclick requires **emails** and **userName** to have the same source value. Any updates to either attributes will modify the other value.
- Proxyclick doesn't support provisioning for groups.

## Additional resources

- [Managing user account provisioning for Enterprise Apps](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/configure-automatic-user-provisioning-portal)
- [What is application access and single sign-on with Microsoft Entra ID?](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/what-is-single-sign-on)

## Related content

- [Learn how to review logs and get reports on provisioning activity](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/check-status-user-account-provisioning)
