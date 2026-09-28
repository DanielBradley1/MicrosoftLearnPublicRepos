<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/soloinsight-cloudgate-sso-provisioning-tutorial -->
<!-- Sitemap-Last-Modified: 2026-03-26 -->

# Configure Soloinsight-CloudGate SSO for automatic user provisioning with Microsoft Entra ID

The objective of this article is to demonstrate the steps to be performed in Soloinsight-CloudGate SSO and Microsoft Entra ID to configure Microsoft Entra ID to automatically provision and de-provision users and/or groups to Soloinsight-CloudGate SSO.

Note

This article describes a connector built on top of the Microsoft Entra user provisioning service. For important details on what this service does, how it works, and frequently asked questions, see [Automate user provisioning and deprovisioning to SaaS applications with Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/user-provisioning).

## Prerequisites

The scenario outlined in this article assumes that you already have the following prerequisites:

- A Microsoft Entra user account with an active subscription. If you don't already have one, you can [Create an account for free](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
- One of the following roles:

  - [Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#application-administrator)
  - [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator)
  - [Application Owner](https://learn.microsoft.com/en-us/entra/fundamentals/users-default-permissions#owned-enterprise-applications).

- [A Soloinsight-CloudGate SSO tenant](https://www.soloinsight.com/)
- A user account in Soloinsight-CloudGate SSO with Admin permissions.

## Step 1: Assign users to Soloinsight-CloudGate SSO

Microsoft Entra ID uses a concept called *assignments* to determine which users should receive access to selected apps. In the context of automatic user provisioning, only the users and/or groups that have been assigned to an application in Microsoft Entra ID are synchronized.

Before configuring and enabling automatic user provisioning, you should decide which users and/or groups in Microsoft Entra ID need access to Soloinsight-CloudGate SSO. Once decided, you can assign these users and/or groups to Soloinsight-CloudGate SSO by following the instructions here:

- [Assign a user or group to an enterprise app](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/assign-user-or-group-access-portal)

## Step 2: Important tips for user assignment to Soloinsight-CloudGate SSO

- It's recommended that a single Microsoft Entra user is assigned to Soloinsight-CloudGate SSO to test the automatic user provisioning configuration. More users and/or groups may be assigned later.
- When assigning a user to Soloinsight-CloudGate SSO, you must select any valid application-specific role \(if available\) in the assignment dialog. Users with the **Default Access** role are excluded from provisioning.

## Step 3: Set up Soloinsight-CloudGate SSO for provisioning

1. Sign in to your [Soloinsight-CloudGate SSO Admin Console](https://soloinsight.sigateway.com/login). Navigate to **Administration > System Settings**.

   ![Soloinsight-CloudGate SSO Admin Console](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/soloinsight-cloudgate-sso-provisioning-tutorial/admin.png)

2. Navigate to **General**.

   ![Soloinsight-CloudGate SSO Add SCIM](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/soloinsight-cloudgate-sso-provisioning-tutorial/config.png)

3. Scroll down to the end of the page to get the **Tenant URL** and **Secret Token**. Copy the **Secret Token**. This value is entered in the Secret Token field in the Provisioning tab of your Soloinsight-CloudGate SSO application.

   ![Soloinsight-CloudGate SSO Create Token](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/soloinsight-cloudgate-sso-provisioning-tutorial/token.png)

## Step 4: Add Soloinsight-CloudGate SSO from the gallery

Before configuring Soloinsight-CloudGate SSO for automatic user provisioning with Microsoft Entra ID, you need to add Soloinsight-CloudGate SSO from the Microsoft Entra application gallery to your list of managed SaaS applications.

**To add Soloinsight-CloudGate SSO from the Microsoft Entra application gallery, perform the following steps:**

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **New application**.
3. In the **Add from the gallery** section, type **Soloinsight-CloudGate SSO**, select **Soloinsight-CloudGate SSO** in the search box.
4. Select **Soloinsight-CloudGate SSO** from results panel and then add the app. Wait a few seconds while the app is added to your tenant. ![Soloinsight-CloudGate SSO in the results list](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/search-new-app.png)

## Step 5: Configure automatic user provisioning to Soloinsight-CloudGate SSO

This section guides you through the steps to configure the Microsoft Entra provisioning service to create, update, and disable users and/or groups in Soloinsight-CloudGate SSO based on user and/or group assignments in Microsoft Entra ID.

Tip

You may also choose to enable SAML-based single sign-on for Soloinsight-CloudGate SSO, following the instructions provided in the [Soloinsight-CloudGate SSO Single sign-on article](https://learn.microsoft.com/en-us/entra/identity/saas-apps/soloinsight-cloudgate-sso-tutorial). Single sign-on can be configured independently of automatic user provisioning, though these two features complement each other

### To configure automatic user provisioning for Soloinsight-CloudGate SSO in Microsoft Entra ID:

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps**

   ![Enterprise applications blade](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/enterprise-applications.png)

3. In the applications list, select **Soloinsight-CloudGate SSO**.

   ![The Soloinsight-CloudGate SSO link in the Applications list](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/all-applications.png)

4. Select the **Provisioning** tab.

   ![Screenshot of the Manage options with the Provisioning option called out.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/provisioning.png)

5. Select **+ New configuration**.

   ![Screenshot of Provisioning tab automatic.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/application-provisioning.png)

6. In the **Tenant URL** field, input `https://sigateway.com/scim/v2/sync/serviceproviderconfig`. Input the **SCIM Authentication Token** value retrieved earlier in **Secret Token**. Select **Test Connection** to ensure Microsoft Entra ID can connect to Soloinsight-CloudGate SSO. If the connection fails, ensure your Soloinsight-CloudGate SSO account has the required admin permissions and try again.

   ![Screenshot of Provisioning test connection.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/provisioning-test-connection.png)

7. Select **Create** to create your configuration.
8. Select **Properties** on the **Overview** page.
9. Select the **Edit** icon to edit the properties. Enable notification emails and provide an email to receive quarantine emails. Enable accidental deletions prevention. Select **Apply** to save the changes.

   ![Screenshot of Provisioning properties.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/provisioning-properties.png)

10. Select **Attribute Mapping** in the left panel and select **users**.
11. Review the user attributes that are synchronized from Microsoft Entra ID to Soloinsight-CloudGate SSO in the **Attribute Mapping** section. The attributes selected as **Matching** properties are used to match the user accounts in Soloinsight-CloudGate SSO for update operations. Select the **Save** button to commit any changes.

    ![Soloinsight-CloudGate SSO User Attributes](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/soloinsight-cloudgate-sso-provisioning-tutorial/userattributes.png)

12. Select **Groups**.
13. Review the group attributes that are synchronized from Microsoft Entra ID to Soloinsight-CloudGate SSO in the **Attribute Mapping** section. The attributes selected as **Matching** properties are used to match the groups in Soloinsight-CloudGate SSO for update operations. Select the **Save** button to commit any changes.

    ![Soloinsight-CloudGate SSO Group Attributes](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/soloinsight-cloudgate-sso-provisioning-tutorial/groupattributes.png)

14. To configure scoping filters, refer to the following instructions provided in the [Scoping filter article](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts).
15. Use [on-demand provisioning](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/provision-on-demand) to validate sync with a small number of users before deploying more broadly in your organization.
16. When you're ready to provision, select **Start Provisioning** from the **Overview** page.

## Step 6: Monitor your deployment

Once you configure provisioning, use the following resources to monitor your deployment:

1. Use the [provisioning logs](https://learn.microsoft.com/en-us/entra/identity/monitoring-health/concept-provisioning-logs) to determine which users are provisioned successfully or unsuccessfully
2. Check the [progress bar](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/application-provisioning-when-will-provisioning-finish-specific-user) to see the status of the provisioning cycle and how close it's to completion
3. If the provisioning configuration seems to be in an unhealthy state, the application goes into quarantine. Learn more about quarantine states the [application provisioning quarantine status](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/application-provisioning-quarantine-status) article.

## More resources

- [Managing user account provisioning for Enterprise Apps](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/configure-automatic-user-provisioning-portal)
- [What is application access and single sign-on with Microsoft Entra ID?](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/what-is-single-sign-on)

## Related content

- [Learn how to review logs and get reports on provisioning activity](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/check-status-user-account-provisioning)
