<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/keeper-password-manager-digitalvault-provisioning-tutorial -->
<!-- Sitemap-Last-Modified: 2026-04-14 -->

# Configure Keeper Password Manager & Digital Vault for automatic user provisioning with Microsoft Entra ID

The objective of this article is to demonstrate the steps to be performed in Keeper Password Manager & Digital Vault and Microsoft Entra ID to configure Microsoft Entra ID to automatically provision and de-provision users and/or groups to Keeper Password Manager & Digital Vault.

Note

This article describes a connector built on top of the Microsoft Entra user Provisioning Service. For important details on what this service does, how it works, and frequently asked questions, see [Automate user provisioning and deprovisioning to SaaS applications with Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/user-provisioning).

## Prerequisites

The scenario outlined in this article assumes that you already have the following prerequisites:

- 

  - A Microsoft Entra user account with an active subscription. If you don't already have one, you can [Create an account for free](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
  - One of the following roles:

    - [Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#application-administrator)
    - [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator)
    - [Application Owner](https://learn.microsoft.com/en-us/entra/fundamentals/users-default-permissions#owned-enterprise-applications).

- [A Keeper Password Manager & Digital Vault tenant](https://keepersecurity.com/pricing.html?t=e)
- A user account in Keeper Password Manager & Digital Vault with Admin permissions.

## Add Keeper Password Manager & Digital Vault from the gallery

Before configuring Keeper Password Manager & Digital Vault for automatic user provisioning with Microsoft Entra ID, you need to add Keeper Password Manager & Digital Vault from the Microsoft Entra application gallery to your list of managed SaaS applications.

**To add Keeper Password Manager & Digital Vault from the Microsoft Entra application gallery, perform the following steps:**

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **New application**.
3. In the **Add from the gallery** section, type **Keeper Password Manager & Digital Vault**, select **Keeper Password Manager & Digital Vault** in the search box.
4. Select **Keeper Password Manager & Digital Vault** from results panel and then add the app. Wait a few seconds while the app is added to your tenant. ![Keeper Password Manager & Digital Vault in the results list](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/search-new-app.png)

## Assigning users to Keeper Password Manager & Digital Vault

Microsoft Entra ID uses a concept called *assignments* to determine which users should receive access to selected apps. In the context of automatic user provisioning, only the users and/or groups that have been assigned to an application in Microsoft Entra ID are synchronized.

Before configuring and enabling automatic user provisioning, you should decide which users and/or groups in Microsoft Entra ID need access to Keeper Password Manager & Digital Vault. Once decided, you can assign these users and/or groups to Keeper Password Manager & Digital Vault by following the instructions here:

- [Assign a user or group to an enterprise app](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/assign-user-or-group-access-portal)

### Important tips for assigning users to Keeper Password Manager & Digital Vault

- It's recommended that a single Microsoft Entra user is assigned to Keeper Password Manager & Digital Vault to test the automatic user provisioning configuration. Additional users and/or groups may be assigned later.
- When assigning a user to Keeper Password Manager & Digital Vault, you must select any valid application-specific role \(if available\) in the assignment dialog. Users with the **Default Access** role are excluded from provisioning.

## Configuring automatic user provisioning to Keeper Password Manager & Digital Vault

This section guides you through the steps to configure the Microsoft Entra provisioning service to create, update, and disable users and/or groups in Keeper Password Manager & Digital Vault based on user and/or group assignments in Microsoft Entra ID.

Tip

You may also choose to enable SAML-based single sign-on for Keeper Password Manager & Digital Vault, following the instructions provided in the [Keeper Password Manager & Digital Vault single sign-on article](https://learn.microsoft.com/en-us/entra/identity/saas-apps/keeperpasswordmanager-tutorial). Single sign-on can be configured independently of automatic user provisioning, though these two features complement each other.

### To configure automatic user provisioning for Keeper Password Manager & Digital Vault in Microsoft Entra ID:

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps**

   ![Enterprise applications blade](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/enterprise-applications.png)

3. In the applications list, select **Keeper Password Manager & Digital Vault**.

   ![The Keeper Password Manager & Digital Vault link in the Applications list](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/all-applications.png)

4. Select the **Provisioning** tab.

   ![Screenshot of the Manage options with the Provisioning option called out.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/provisioning.png)

5. Select **+ New configuration**.

   ![Screenshot of Provisioning tab automatic.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/application-provisioning.png)

6. In the **Tenant URL** field, enter your Keeper Password Manager & Digital Vault Tenant URL and Secret Token. Select **Test Connection** to ensure Microsoft Entra ID can connect to Keeper Password Manager & Digital Vault. If the connection fails, ensure your Keeper Password Manager & Digital Vault account has the required admin permissions and try again.
7. Sign in to your [Keeper Admin Console](https://keepersecurity.com/console/#login). Select **Admin** and select an existing node or create a new one. Navigate to the **Provisioning** tab and select **Add Method**.

   ![Keeper Admin Console](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/keeper-password-manager-digitalvault-provisioning-tutorial/keeper-admin-console.png)


   Select **SCIM \(System for Cross-Domain Identity Management**.


   ![Keeper Add SCIM](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/keeper-password-manager-digitalvault-provisioning-tutorial/keeper-add-scim.png)


   Select **Create Provisioning Token**.


   ![Keeper Create Endpoint](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/keeper-password-manager-digitalvault-provisioning-tutorial/keeper-create-endpoint.png)


   Copy the values for **URL** and **Token** and paste them into **Tenant URL** and **Secret Token** in Microsoft Entra ID. Select **Save** to complete the provisioning setup on Keeper.


   ![Keeper Create Token](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/keeper-password-manager-digitalvault-provisioning-tutorial/keeper-create-token.png)

8. Select **Create** to create your configuration.
9. Select **Properties** on the **Overview** page.
10. In the **Notification Email** field, enter the email address of a person who should receive the provisioning error notifications and select the **Send an email notification when a failure occurs** check box.

    ![Screenshot of Provisioning properties.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/provisioning-properties.png)

11. Select **Attribute Mapping** in the left panel and select **users**.
12. Review the user attributes that are synchronized from Microsoft Entra ID to Keeper Password Manager & Digital Vault in the **Attribute-Mapping** section. The attributes selected as **Matching** properties are used to match the user accounts in Keeper Password Manager & Digital Vault for update operations. If you choose to change the [matching target attribute](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/customize-application-attributes), you need to ensure that the Keeper Password Manager & Digital Vault API supports filtering users based on that attribute. Select the **Save** button to commit any changes.

    ![Keeper User Attributes](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/keeper-password-manager-digitalvault-provisioning-tutorial/keeper-user-attributes.png)

13. Review the group attributes that are synchronized from Microsoft Entra ID to Keeper Password Manager & Digital Vault in the **Attribute Mapping** section. The attributes selected as **Matching** properties are used to match the groups in Keeper Password Manager & Digital Vault for update operations. Select the **Save** button to commit any changes.

    ![Keeper Group Attributes](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/keeper-password-manager-digitalvault-provisioning-tutorial/keeper-group-attributes.png)

14. To configure scoping filters, refer to the instructions provided in the [Scoping filter article](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts).
15. Use [on-demand provisioning](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/provision-on-demand) to validate sync with a small number of users before deploying more broadly in your organization.
16. When you're ready to provision, select **Start Provisioning** from the **Overview** page.

## Connector Limitations

- Keeper Password Manager & Digital Vault requires **emails** and **userName** to have the same source value, as any updates to either attributes will modify the other value.
- Keeper Password Manager & Digital Vault doesn't support user deletes, only disable. Disabled users appear as locked in the Keeper Admin Console UI.

## Additional resources

- [Managing user account provisioning for Enterprise Apps](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/configure-automatic-user-provisioning-portal)
- [What is application access and single sign-on with Microsoft Entra ID?](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/what-is-single-sign-on)

## Related content

- [Learn how to review logs and get reports on provisioning activity](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/check-status-user-account-provisioning)
