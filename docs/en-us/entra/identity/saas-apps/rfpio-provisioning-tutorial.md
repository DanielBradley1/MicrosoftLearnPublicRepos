<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/rfpio-provisioning-tutorial -->
<!-- Sitemap-Last-Modified: 2026-04-28 -->

# Configure RFPIO for automatic user provisioning with Microsoft Entra ID

The objective of this article is to demonstrate the steps to be performed in RFPIO and Microsoft Entra ID to configure Microsoft Entra ID to automatically provision and de-provision users and/or groups to RFPIO.

Note

This article describes a connector built on top of the Microsoft Entra user provisioning service. For important details on what this service does, how it works, and frequently asked questions, see [Automate user provisioning and deprovisioning to SaaS applications with Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/user-provisioning).

## Prerequisites

The scenario outlined in this article assumes that you already have the following prerequisites:

- A Microsoft Entra user account with an active subscription. If you don't already have one, you can [Create an account for free](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn). - One of the following roles: - [Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#application-administrator) - [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator) - [Application Owner](https://learn.microsoft.com/en-us/entra/fundamentals/users-default-permissions#owned-enterprise-applications)..

- [A RFPIO tenant](https://www.rfpio.com/product/).
- A user account in RFPIO with Admin permissions.

## Assigning users to RFPIO

Microsoft Entra ID uses a concept called *assignments* to determine which users should receive access to selected apps. In the context of automatic user provisioning, only the users and/or groups that have been assigned to an application in Microsoft Entra ID are synchronized.

Before configuring and enabling automatic user provisioning, you should decide which users and/or groups in Microsoft Entra ID need access to RFPIO. Once decided, you can assign these users and/or groups to RFPIO by following the instructions here:

- [Assign a user or group to an enterprise app](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/assign-user-or-group-access-portal)

## Important tips for assigning users to RFPIO

- It's recommended that a single Microsoft Entra user is assigned to RFPIO to test the automatic user provisioning configuration. Additional users and/or groups may be assigned later.
- When assigning a user to RFPIO, you must select any valid application-specific role \(if available\) in the assignment dialog. Users with the **Default Access** role are excluded from provisioning.

## Set up RFPIO for provisioning

Before configuring RFPIO for automatic user provisioning with Microsoft Entra ID, you need to enable SCIM provisioning on RFPIO.

1. Sign in to your RFPIO Admin Console. On the bottom left of the admin console, select **Tenant**.

   ![Screenshot of RFPIO Admin Console](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/rfpio-provisioning-tutorial/aadtest0.png)

2. Select **Organization Settings**.

   ![Screenshot of RFPIO Admin](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/rfpio-provisioning-tutorial/aadtest.png)

3. Navigate to **USER MANAGEMENT** > **SECURITY** > **SCIM**.

   ![Screenshot of RFPIO Add SCIM](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/rfpio-provisioning-tutorial/scim.png)

4. Ensure that **Auto User Provisioning** is enabled. Select **GENERATE SCIM API TOKEN**.

   ![Screenshot of the S C I M section with the GENERATE S C I M A P I TOKEN option called out.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/rfpio-provisioning-tutorial/generate.png)

5. Save the **SCIM API Token** as this token isn't displayed again for security purpose. This value is entered in the **Secret Token** field in the Provisioning tab of your RFPIO application.

   ![Screenshot of the S C I M section with the Warning dialog box that appears after you select SUBMIT.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/rfpio-provisioning-tutorial/auth.png)

## Add RFPIO from the gallery

To configure RFPIO for automatic user provisioning with Microsoft Entra ID, you need to add RFPIO from the Microsoft Entra application gallery to your list of managed SaaS applications.

**To add RFPIO from the Microsoft Entra application gallery, perform the following steps:**

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **New application**.
3. In the **Add from the gallery** section, type **RFPIO**, select **RFPIO** in the results panel, and then select the **Add** button to add the application.

   ![Screenshot of RFPIO in the results list](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/search-new-app.png)

## Configuring automatic user provisioning to RFPIO

This section guides you through the steps to configure the Microsoft Entra provisioning service to create, update, and disable users and/or groups in RFPIO based on user and/or group assignments in Microsoft Entra ID.

Tip

You may also choose to enable SAML-based single sign-on for RFPIO, following the instructions provided in the [RFPIO Single sign-on article](https://learn.microsoft.com/en-us/entra/identity/saas-apps/rfpio-tutorial). Single sign-on can be configured independently of automatic user provisioning, though these two features complement each other.

### To configure automatic user provisioning for RFPIO in Microsoft Entra ID:

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps**

   ![Screenshot of Enterprise applications blade.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/enterprise-applications.png)

3. In the applications list, select **RFPIO**.

   ![Screenshot of the RFPIO link in the Applications list.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/all-applications.png)

4. Select the **Provisioning** tab.

   ![Screenshot of Provisioning tab automatic.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/application-provisioning.png)

5. Set **+ New configuration**.

   ![Screenshot of the Provisioning Mode dropdown list with the Automatic option called out.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/provisioning-automatic.png)

6. In the **Tenant URL** field, input your RFPIO Tenant URL and Secret Token. Select **Test Connection** to ensure Microsoft Entra ID can connect to RFPIO. If the connection fails, ensure your RFPIO account has the required admin permissions and try again.

   ![Screenshot of Provisioning test connection.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/provisioning-test-connection.png)

7. Select **Create** to create your configuration.
8. Select **Properties** in the **Overview** page.
9. Select the pencil to edit the properties. Enable notification emails and provide an email to receive quarantine emails. Enable accidental deletions prevention. Select **Apply** to save the changes.

   ![Screenshot of the Provisioning properties page showing notification and deletion settings.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/provisioning-properties.png)

10. Select **Attribute Mapping** in the left panel and select users.
11. Review the user attributes that are synchronized from Microsoft Entra ID to RFPIO in the **Attribute Mapping** section. The attributes selected as **Matching** properties are used to match the user accounts in RFPIO for update operations. Select the **Save** button to commit any changes.

    ![Screenshot of RFPIO User Attributes](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/rfpio-provisioning-tutorial/userattributes.png)

12. To configure scoping filters, refer to the following instructions provided in the [Scoping filter article](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts) article.
13. Use [on-demand provisioning](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/provision-on-demand) to validate sync with a small number of users before deploying more broadly in your organization.
14. When you're ready to provision, select **Start Provisioning** from the **Overview** page.

For more information on how to read the Microsoft Entra provisioning logs, see [Reporting on automatic user account provisioning](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/check-status-user-account-provisioning).

## Connector Limitations

- RFPIO doesn't support groups provisioning currently.

## Additional resources

- [Managing user account provisioning for Enterprise Apps](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/configure-automatic-user-provisioning-portal)
- [What is application access and single sign-on with Microsoft Entra ID?](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/what-is-single-sign-on)

## Related content

- [Learn how to review logs and get reports on provisioning activity](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/check-status-user-account-provisioning)
