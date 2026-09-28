<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/bitabiz-provisioning-tutorial -->
<!-- Sitemap-Last-Modified: 2026-03-05 -->

# Configure BitaBIZ for automatic user provisioning with Microsoft Entra ID

The objective of this article is to demonstrate the steps to be performed in BitaBIZ and Microsoft Entra ID to configure Microsoft Entra ID to automatically provision and de-provision users and/or groups to BitaBIZ.

Note

This article describes a connector built on top of the Microsoft Entra user Provisioning Service. For important details on what this service does, how it works, and frequently asked questions, see [Automate user provisioning and deprovisioning to SaaS applications with Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/user-provisioning).

## Prerequisites

The scenario outlined in this article assumes that you already have the following prerequisites:

- A Microsoft Entra user account with an active subscription. If you don't already have one, you can [Create an account for free](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn). - One of the following roles: - [Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#application-administrator) - [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator) - [Application Owner](https://learn.microsoft.com/en-us/entra/fundamentals/users-default-permissions#owned-enterprise-applications)..

- [A BitaBIZ tenant](https://bitabiz.dk/en/price/).
- A user account in BitaBIZ with Admin permissions.

## Assigning users to BitaBIZ

Microsoft Entra ID uses a concept called *assignments* to determine which users should receive access to selected apps. In the context of automatic user provisioning, only the users and/or groups that have been assigned to an application in Microsoft Entra ID are synchronized.

Before configuring and enabling automatic user provisioning, you should decide which users and/or groups in Microsoft Entra ID need access to BitaBIZ. Once decided, you can assign these users and/or groups to BitaBIZ by following the instructions here:

- [Assign a user or group to an enterprise app](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/assign-user-or-group-access-portal)

## Important tips for assigning users to BitaBIZ

- It's recommended that a single Microsoft Entra user is assigned to BitaBIZ to test the automatic user provisioning configuration. Additional users and/or groups may be assigned later.
- When assigning a user to BitaBIZ, you must select any valid application-specific role \(if available\) in the assignment dialog. Users with the **Default Access** role are excluded from provisioning.

## Setup BitaBIZ for provisioning

Before configuring BitaBIZ for automatic user provisioning with Microsoft Entra ID, you need to enable SCIM provisioning on BitaBIZ.

1. Sign in to your [BitaBIZ Admin Console](https://www.bitabiz.com/login?lang=en). Select **SETUP ADMIN**.

   ![Screenshot of the BitaBIZ Admin Console, with Setup admin highlighted.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/bitabiz-provisioning-tutorial/setup-admin.png)

2. Navigate to **INTEGRATION**.

   ![Screenshot of the BitaBIZ Admin Console, with Integration highlighted.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/bitabiz-provisioning-tutorial/integration.png)

3. Navigate to **Microsoft Entra provisioning**. Select **Enabled** in Automatic user provisioning. Copy the values for **SCIM Provisioning endpoint URL** and **Bearer Token**. These values are entered in the Tenant URL and Secret Token fields in the Provisioning tab of your BitaBIZ application.

   ![BitaBIZ Add SCIM](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/bitabiz-provisioning-tutorial/authentication.png)

## Add BitaBIZ from the gallery

To configure BitaBIZ for automatic user provisioning with Microsoft Entra ID, you need to add BitaBIZ from the Microsoft Entra application gallery to your list of managed SaaS applications.

**To add BitaBIZ from the Microsoft Entra application gallery, perform the following steps:**

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **New application**.
3. In the **Add from the gallery** section, type **BitaBIZ**, select **BitaBIZ** in the search box.
4. Select **BitaBIZ** from results panel and then add the app. Wait a few seconds while the app is added to your tenant. ![BitaBIZ in the results list](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/search-new-app.png)

## Configuring automatic user provisioning to BitaBIZ

This section guides you through the steps to configure the Microsoft Entra provisioning service to create, update, and disable users and/or groups in BitaBIZ based on user and/or group assignments in Microsoft Entra ID.

Tip

You may also choose to enable SAML-based single sign-on for BitaBIZ, following the instructions provided in the [BitaBIZ Single sign-on article](https://learn.microsoft.com/en-us/entra/identity/saas-apps/bitabiz-tutorial). Single sign-on can be configured independently of automatic user provisioning, though these two features complement each other

### To configure automatic user provisioning for BitaBIZ in Microsoft Entra ID:

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps**

   ![Enterprise applications blade](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/enterprise-applications.png)

3. In the applications list, select **BitaBIZ**.

   ![The BitaBIZ link in the Applications list](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/all-applications.png)

4. Select the **Provisioning** tab.

   ![Screenshot of the Manage options with the Provisioning option called out.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/provisioning.png)

5. Select the **Provisioning** tab.

   ![Screenshot of Provisioning tab.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/provisioning.png)

6. Set **+ New configuration**.

   ![Screenshot of Provisioning tab automatic.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/application-provisioning.png)

7. In the **Tenant URL** field, input your BitaBIZ Tenant URL and Secret Token. Select **Test Connection** to ensure Microsoft Entra ID can connect to BitaBIZ. If the connection fails, ensure your BitaBIZ account has the required admin permissions and try again.

   ![Screenshot of Provisioning test connection.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/provisioning-test-connection.png)

8. Select **Create** to create your configuration.
9. Select **Properties** in the **Overview** page.
10. Select the pencil to edit the properties. Enable notification emails and provide an email to receive quarantine emails. Enable accidental deletions prevention. Select **Apply** to save the changes.

    ![Screenshot of Provisioning properties.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/provisioning-properties.png)

11. Select **Attribute Mapping** in the left panel and select **users**.
12. Review the user attributes that are synchronized from Microsoft Entra ID to BitaBIZ in the **Attribute Mapping** section. The attributes selected as **Matching** properties are used to match the user accounts in BitaBIZ for update operations. Select the **Save** button to commit any changes.

    ![BitaBIZ User Attributes](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/bitabiz-provisioning-tutorial/user-attribute.png)

13. To configure scoping filters, refer to the following instructions provided in the [Scoping filter article](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts).
14. Use [on-demand provisioning](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/provision-on-demand) to validate sync with a small number of users before deploying more broadly in your organization.
15. When you're ready to provision, select **Start Provisioning** from the **Overview** page.

For more information on how to read the Microsoft Entra provisioning logs, see [Reporting on automatic user account provisioning](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/check-status-user-account-provisioning).

## Connector limitations

- BitaBIZ requires **userName**, **email**, **firstName** and **lastName** as mandatory attributes.
- BitaBIZ doesn't support hard deletes currently.

## Additional resources

- [Managing user account provisioning for Enterprise Apps](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/configure-automatic-user-provisioning-portal).
- [What is application access and single sign-on with Microsoft Entra ID?](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/what-is-single-sign-on)

## Related content

- [Learn how to review logs and get reports on provisioning activity](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/check-status-user-account-provisioning).
