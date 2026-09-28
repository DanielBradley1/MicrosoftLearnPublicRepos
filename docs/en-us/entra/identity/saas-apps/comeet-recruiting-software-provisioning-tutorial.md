<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/comeet-recruiting-software-provisioning-tutorial -->
<!-- Sitemap-Last-Modified: 2026-05-26 -->

# Configure Comeet Recruiting Software for automatic user provisioning with Microsoft Entra ID

The objective of this article is to demonstrate the steps to be performed in Comeet Recruiting Software and Microsoft Entra ID to configure Microsoft Entra ID to automatically provision and de-provision users and/or groups to Comeet Recruiting Software.

Note

This article describes a connector built on top of the Microsoft Entra user provisioning service. For important details on what this service does, how it works, and frequently asked questions, see [Automate user provisioning and deprovisioning to SaaS applications with Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/user-provisioning).

Comeet Recruiting Software is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government | China operated by 21Vianet |
| :---: | :---: | :---: |
| ✅ | ✅ |  |

## Prerequisites

The scenario outlined in this article assumes that you already have the following prerequisites:

- 

  - A Microsoft Entra user account with an active subscription. If you don't already have one, you can [Create an account for free](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
  - One of the following roles:

    - [Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#application-administrator)
    - [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator)
    - [Application Owner](https://learn.microsoft.com/en-us/entra/fundamentals/users-default-permissions#owned-enterprise-applications).

- [A Comeet Recruiting Software tenant](https://www.comeet.co/)
- A user account in Comeet Recruiting Software with Admin permissions.

## Add Comeet Recruiting Software from the gallery

Before configuring Comeet Recruiting Software for automatic user provisioning with Microsoft Entra ID, you need to add Comeet Recruiting Software from the Microsoft Entra application gallery to your list of managed SaaS applications.

**To add Comeet Recruiting Software from the Microsoft Entra application gallery, perform the following steps:**

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **New application**.
3. In the **Add from the gallery** section, type **Comeet Recruiting Software**, select **Comeet Recruiting Software** in the search box.
4. Select **Comeet Recruiting Software** from results panel and then add the app. Wait a few seconds while the app is added to your tenant. ![Comeet Recruiting Software in the results list](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/search-new-app.png)

## Assigning users to Comeet Recruiting Software

Microsoft Entra ID uses a concept called *assignments* to determine which users should receive access to selected apps. In the context of automatic user provisioning, only the users and/or groups that have been assigned to an application in Microsoft Entra ID are synchronized.

Before configuring and enabling automatic user provisioning, you should decide which users and/or groups in Microsoft Entra ID need access to Comeet Recruiting Software. Once decided, you can assign these users and/or groups to Comeet Recruiting Software by following the instructions here:

- [Assign a user or group to an enterprise app](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/assign-user-or-group-access-portal)

### Important tips for assigning users to Comeet Recruiting Software

- It's recommended that a single Microsoft Entra user is assigned to Comeet Recruiting Software to test the automatic user provisioning configuration. More users and/or groups may be assigned later.
- When assigning a user to Comeet Recruiting Software, you must select any valid application-specific role \(if available\) in the assignment dialog. Users with the **Default Access** role are excluded from provisioning.

## Configuring automatic user provisioning to Comeet Recruiting Software

This section guides you through the steps to configure the Microsoft Entra provisioning service to create, update, and disable users and/or groups in Comeet Recruiting Software based on user and/or group assignments in Microsoft Entra ID.

Tip

You may also choose to enable SAML-based single sign-on for Comeet Recruiting Software, following the instructions provided in the [Comeet Recruiting Software single sign-on article](https://learn.microsoft.com/en-us/entra/identity/saas-apps/comeetrecruitingsoftware-tutorial). Single sign-on can be configured independently of automatic user provisioning, though these two features complement each other.

### To configure automatic user provisioning for Comeet Recruiting Software in Microsoft Entra ID:

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps**

   ![Screenshot of the Enterprise applications blade.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/enterprise-applications.png)

3. In the applications list, select **Comeet Recruiting Software**.

   ![Screenshot of the Comeet Recruiting Software link in the Applications list.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/all-applications.png)

4. Select the **Provisioning** tab.

   ![Screenshot of the Provisioning tab](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/provisioning.png)

5. Select **+ New configuration**.

   ![Screenshot of Provisioning tab automatic.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/application-provisioning.png)

6. In the **Tenant URL** field, enter your Comeet Recruiting Software Tenant URL and Secret Token. Select **Test Connection** to ensure Microsoft Entra ID can connect to Comeet Recruiting Software. If the connection fails, ensure your Comeet Recruiting Software account has the required admin permissions and try again.

   ![Screenshot of Provisioning test connection.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/provisioning-test-connection.png)

7. Select **Create** to create your configuration.
8. Select **Properties** on the **Overview** page.
9. In the **Notification Email** field, enter the email address of a person who should receive the provisioning error notifications and select the **Send an email notification when a failure occurs** check box.

   ![Screenshot of the Provisioning properties configuration page.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/provisioning-properties.png)

10. Select **Attribute Mapping** in the left panel and select **users**.
11. Review the user attributes that are synchronized from Microsoft Entra ID to Comeet Recruiting Software in the **Attribute-Mapping** section. The attributes selected as **Matching** properties are used to match the user accounts in Comeet Recruiting Software for update operations. If you choose to change the [matching target attribute](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/customize-application-attributes), you need to ensure that the Comeet Recruiting Software API supports filtering users based on that attribute. Select the **Save** button to commit any changes.

    ![Screenshot of the Comeet Recruiting Software Group Attributes page.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/comeet-recruiting-software-provisioning-tutorial/user-mapping-attributes.png)

12. To configure scoping filters, refer to the instructions provided in the [Scoping filter article](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts).
13. Use [on-demand provisioning](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/provision-on-demand) to validate sync with a small number of users before deploying more broadly in your organization.
14. When you're ready to provision, select **Start Provisioning** from the **Overview** page.

## Connector Limitations

- Comeet Recruiting Software doesn't not currently support groups.

## More resources

- [Managing user account provisioning for Enterprise Apps](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/configure-automatic-user-provisioning-portal)
- [What is application access and single sign-on with Microsoft Entra ID?](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/what-is-single-sign-on)

## Related content

- [Learn how to review logs and get reports on provisioning activity](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/check-status-user-account-provisioning)
