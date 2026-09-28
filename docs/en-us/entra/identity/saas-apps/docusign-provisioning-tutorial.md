<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/docusign-provisioning-tutorial -->
<!-- Sitemap-Last-Modified: 2026-04-27 -->

# Configure DocuSign for automatic user provisioning with Microsoft Entra ID

The objective of this article is to show you the steps you need to perform in DocuSign and Microsoft Entra ID to automatically provision and de-provision user accounts from Microsoft Entra ID to DocuSign.

## Prerequisites

The scenario outlined in this article assumes that you already have the following items:

- A Microsoft Entra tenant.
- A DocuSign single sign-on enabled subscription.
- A user account in DocuSign with Team Admin permissions.

## Assigning users to DocuSign

Microsoft Entra ID uses a concept called "assignments" to determine which users should receive access to selected apps. In the context of automatic user account provisioning, only the users and groups that have been "assigned" to an application in Microsoft Entra ID are synchronized.

Before configuring and enabling the provisioning service, you need to decide what users and/or groups in Microsoft Entra ID represent the users who need access to your DocuSign app. Once decided, you can assign these users to your DocuSign app by following the instructions here:

[Assign a user or group to an enterprise app](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/assign-user-or-group-access-portal)

### Important tips for assigning users to DocuSign

- It's recommended that a single Microsoft Entra user is assigned to DocuSign to test the provisioning configuration. Additional users may be assigned later.
- When assigning a user to DocuSign, you must select a valid user role. The "Default Access" role doesn't work for provisioning.

Note

Microsoft Entra ID doesn't support group provisioning with the Docusign application, only users can be provisioned.

## Enable User Provisioning

This section guides you through connecting your Microsoft Entra ID to DocuSign's user account provisioning API, and configuring the provisioning service to create, update, and disable assigned user accounts in DocuSign based on user and group assignment in Microsoft Entra ID.

Tip

You may also choose to enabled SAML-based Single Sign-On for DocuSign, following the instructions provided in the [Azure portal](https://portal.azure.com). Single sign-on can be configured independently of automatic provisioning, though these two features complement each other.

### To configure user account provisioning:

The objective of this section is to outline how to enable user provisioning of Active Directory user accounts to DocuSign.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps**.
3. If you have already configured DocuSign for single sign-on, search for your instance of DocuSign using the search field. Otherwise, select **Add** and search for **DocuSign** in the application gallery. Select DocuSign from the search results, and add it to your list of applications.
4. Select your instance of DocuSign, then select the **Provisioning** tab.
5. Select **+ New configuration**.

   ![Screenshot of Provisioning tab automatic.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/provisioning-automatic.png)

6. In the **Tenant URL** field, input your DocuSign Tenant URL and Secret Token. Select **Test Connection** to ensure Microsoft Entra ID can connect to DocuSign. If the connection fails, ensure your DocuSign account has the required admin permissions and try again.
7. Select **Properties** on the **Overview** page.
8. Select **Create** to create your configuration.
9. Select the **Edit** icon to edit the properties. Enable notification emails and provide an email to receive quarantine notifications. Enable **Accidental deletions prevention**. Select **Apply** to save the changes.
10. In the **Notification Email** field, enter the email address of a person who should receive the provisioning error notifications and select the **Send an email notification when a failure occurs** check box.

    ![Screenshot of Provisioning properties.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/provisioning-properties.png)

11. Select **Attribute Mapping** in the left panel and select **users**.
12. In the **Attribute Mappings** section, review the user attributes that are synchronized from Microsoft Entra ID to DocuSign. The attributes selected as **Matching** properties are used to match the user accounts in DocuSign for update operations. Select the Save button to commit any changes.
13. To configure scoping filters, refer to the instructions provided in the [Scoping filter article](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts).
14. Use [on-demand provisioning](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/provision-on-demand) to validate sync with a small number of users before deploying more broadly in your organization.
15. When you're ready to provision, select **Start Provisioning** from the **Overview** page.

For more information on how to read the Microsoft Entra provisioning logs, see [Reporting on automatic user account provisioning](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/check-status-user-account-provisioning).

## Troubleshooting Tips

- Provisioning a role or permission profile for a user in Docusign can be accomplished by using an expression in your attribute mappings using the [switch](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/functions-for-customizing-application-data#switch) and [singleAppRoleAssignment](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/functions-for-customizing-application-data#singleapproleassignment) functions. For example, the expression below will provision the ID "8032066" when a user has the "DS Admin" role assigned in Microsoft Entra ID. It doesn't provision any permission profile if the user isn't assigned a role on the Microsoft Entra ID side. The ID can be retrieved from the DocuSign [portal](https://support.docusign.com/).

Switch\(SingleAppRoleAssignment\(\[appRoleAssignments\]\)," ", "DS Admin", "8032066"\)

## Additional resources

- [Managing user account provisioning for Enterprise Apps](https://learn.microsoft.com/en-us/entra/identity/saas-apps/tutorial-list)
- [What is application access and single sign-on with Microsoft Entra ID?](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/what-is-single-sign-on)
- [Configure Single Sign-on](https://learn.microsoft.com/en-us/entra/identity/saas-apps/docusign-tutorial)
