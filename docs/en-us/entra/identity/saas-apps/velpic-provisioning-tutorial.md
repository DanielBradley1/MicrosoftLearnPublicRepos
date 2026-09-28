<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/velpic-provisioning-tutorial -->
<!-- Sitemap-Last-Modified: 2026-04-10 -->

# Configure Configuring Velpic for automatic user provisioning with Microsoft Entra ID

The objective of this article is to show you the steps you need to perform in Velpic and Microsoft Entra ID to automatically provision and de-provision user accounts from Microsoft Entra ID to Velpic.

Note

This article describes a connector built on top of the Microsoft Entra user provisioning service. For important details on what this service does, how it works, and frequently asked questions, see [Automate user provisioning and deprovisioning to SaaS applications with Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/user-provisioning).

## Prerequisites

The scenario outlined in this article assumes that you already have the following items:

- 

  - A Microsoft Entra user account with an active subscription. If you don't already have one, you can [Create an account for free](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
  - One of the following roles:

    - [Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#application-administrator)
    - [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator)
    - [Application Owner](https://learn.microsoft.com/en-us/entra/fundamentals/users-default-permissions#owned-enterprise-applications).

- A Velpic tenant with the Enterprise plan or better enabled
- A user account in Velpic with Admin permissions

## Step 1: Assign users to Velpic

Microsoft Entra ID uses a concept called "assignments" to determine which users should receive access to selected apps. In the context of automatic user account provisioning, only the users and groups that have been "assigned" to an application in Microsoft Entra ID is synchronized.

Before configuring and enabling the provisioning service, you need to decide what users and/or groups in Microsoft Entra ID represent the users who need access to your Velpic app. Once decided, you can assign these users to your Velpic app by following the instructions here:

[Assign a user or group to an enterprise app](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/assign-user-or-group-access-portal)

### Important tips for assigning users to Velpic

- It's recommended that a single Microsoft Entra user be assigned to Velpic to test the provisioning configuration. Additional users and/or groups may be assigned later.
- When assigning a user to Velpic, you must select either the **User** role, or another valid application-specific role \(if available\) in the assignment dialog. The **Default Access** role doesn't work for provisioning, and these users are skipped.

## Step 2: Configure user provisioning to Velpic

This section guides you through connecting your Microsoft Entra ID to Velpic's user account provisioning API, and configuring the provisioning service to create, update, and disable assigned user accounts in Velpic based on user and group assignment in Microsoft Entra ID.

Tip

You may also choose to enable SAML-based single sign-on for Velpic, following the instructions provided in the [Azure portal](https://portal.azure.com). Single sign-on can be configured independently of automatic provisioning, though these two features complement each other.

### Configure automatic user account provisioning to Velpic in Microsoft Entra ID

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps**.
3. If you have already configured Velpic for single sign-on, search for your instance of Velpic using the search field. Otherwise, select **Add** and search for **Velpic** in the application gallery. Select Velpic from the search results, and add it to your list of applications.
4. In the applications list, select **Velpic**.

   ![Screenshot of the Velpic link in the Applications list.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/all-applications.png)

5. Select the **Provisioning** tab.

   ![Screenshot of Provisioning tab.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/provisioning.png)

6. Select **+ New configuration**.

   ![Screenshot of New configuration.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/application-provisioning.png)

7. Under the **Admin Credentials** section, enter the Tenant URL and Secret Token of Velpic.\(You can find these values under your Velpic account: **Manage** > **Integration** > **Plugin** > **SCIM**\)

   ![Screenshot of Authorization Values.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/velpic-provisioning-tutorial/velpic2.png)

8. Select **Test Connection** to ensure Microsoft Entra ID can connect to your Velpic app. If the connection fails, ensure your Velpic account has Admin permissions and try step 5 again.
9. Select **Create** to create your configuration.
10. Select **Properties** on the **Overview** page.
11. Select the **Edit** icon to edit the properties. Enable notification emails and provide an email to receive quarantine notifications. Enable **Accidental deletions prevention**. Select **Apply** to save the changes.

    ![Screenshot of Provisioning properties.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/provisioning-properties.png)

12. Select **Attribute Mapping** in the left panel and select **users**.
13. Review the user attributes that are synchronized from Microsoft Entra ID to Velpic. The attributes selected as **Matching** properties are used to match the user accounts in Velpic for update operations. Select the Save button to commit any changes.
14. To configure scoping filters, refer to the instructions provided in the [Scoping filter article](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts).
15. Use [on-demand provisioning](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/provision-on-demand) to validate sync with a small number of users before deploying more broadly in your organization.
16. When you're ready to provision, select **Start Provisioning** from the **Overview** page.

## Step 3: Monitor your deployment

Once you configure provisioning, use the following resources to monitor your deployment:

1. Use the [provisioning logs](https://learn.microsoft.com/en-us/entra/identity/monitoring-health/concept-provisioning-logs) to determine which users are provisioned successfully or unsuccessfully
2. Check the [progress bar](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/application-provisioning-when-will-provisioning-finish-specific-user) to see the status of the provisioning cycle and how close it's to completion
3. If the provisioning configuration seems to be in an unhealthy state, the application goes into quarantine. Learn more about quarantine states the [application provisioning quarantine status](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/application-provisioning-quarantine-status) article.

## More resources

- [Managing user account provisioning for Enterprise Apps](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/configure-automatic-user-provisioning-portal)
- [What is application access and single sign-on with Microsoft Entra ID?](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/what-is-single-sign-on)

## Related content

- [Learn how to review logs and get reports on provisioning activity](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/check-status-user-account-provisioning)
