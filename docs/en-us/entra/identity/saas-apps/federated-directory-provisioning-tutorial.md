<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/federated-directory-provisioning-tutorial -->
<!-- Sitemap-Last-Modified: 2026-04-13 -->

# Configure Federated Directory for automatic user provisioning with Microsoft Entra ID

The objective of this article is to demonstrate the steps to be performed in Federated Directory and Microsoft Entra ID to configure Microsoft Entra ID to automatically provision and de-provision users and/or groups to Federated Directory.

Note

This article describes a connector built on top of the Microsoft Entra user provisioning service. For important details on what this service does, how it works, and frequently asked questions, see [Automate user provisioning and deprovisioning to SaaS applications with Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/user-provisioning).

## Capabilities supported

- Create users in Federated Directory.
- Remove users in Federated Directory when they don't require access anymore.
- Long lived bearer token authentication supported.

## Prerequisites

The scenario outlined in this article assumes that you already have the following prerequisites:

- A Microsoft Entra user account with an active subscription. If you don't already have one, you can [Create an account for free](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn). - One of the following roles: - [Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#application-administrator) - [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator) - [Application Owner](https://learn.microsoft.com/en-us/entra/fundamentals/users-default-permissions#owned-enterprise-applications)..

- [A Federated Directory](https://www.federated.directory/pricing).
- A user account in Federated Directory with Admin permissions.

## Assign Users to Federated Directory

Microsoft Entra ID uses a concept called assignments to determine which users should receive access to selected apps. In the context of automatic user provisioning, only the users and/or groups that have been assigned to an application in Microsoft Entra ID are synchronized.

Before configuring and enabling automatic user provisioning, you should decide which users and/or groups in Microsoft Entra ID need access to Federated Directory. Once decided, you can assign these users and/or groups to Federated Directory by following the instructions here:

- [Assign a user or group to an enterprise app](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/assign-user-or-group-access-portal)

## Important tips for assigning users to Federated Directory

- It's recommended that a single Microsoft Entra user is assigned to Federated Directory to test the automatic user provisioning configuration. Additional users and/or groups may be assigned later.
- When assigning a user to Federated Directory, you must select any valid application-specific role \(if available\) in the assignment dialog. Users with the Default Access role are excluded from provisioning.

## Set up Federated Directory for provisioning

Before configuring Federated Directory for automatic user provisioning with Microsoft Entra ID, you need to enable SCIM provisioning on Federated Directory.

1. Sign in to your [Federated Directory Admin Console](https://federated.directory/of)

   ![Screenshot of the Federated Directory admin console showing a field for entering a company name. Sign-in buttons are also visible.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/federated-directory-provisioning-tutorial/companyname.png)

2. Navigate to **Directories > User directories** and select your tenant.

   ![Screenshot of the Federated Directory admin console, with Directories and Federated Directory Microsoft Entra ID Test highlighted.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/federated-directory-provisioning-tutorial/ad-user-directories.png)

3. To generate a permanent bearer token, navigate to **Directory Keys > Create New Key.**

   ![Screenshot of the Directory keys page of the Federated Directory admin console. The Create new key button is highlighted.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/federated-directory-provisioning-tutorial/federated01.png)

4. Create a directory key.

   ![Screenshot of the Create directory key page of the Federated Directory admin console, with Name and Description fields and a Create key button.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/federated-directory-provisioning-tutorial/federated02.png)

5. Copy the **Access Token** value. This value is entered in the **Secret Token** field in the Provisioning tab of your Federated Directory application.

   ![Screenshot of a page in the Federated Directory admin console. An access token placeholder and a key name, description, and issuer are visible.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/federated-directory-provisioning-tutorial/federated03.png)

## Add Federated Directory from the gallery

To configure Federated Directory for automatic user provisioning with Microsoft Entra ID, you need to add Federated Directory from the Microsoft Entra application gallery to your list of managed SaaS applications.

**To add Federated Directory from the Microsoft Entra application gallery, perform the following steps:**

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **New application**.
3. In the **Add from the gallery** section, type **Federated Directory**, select **Federated Directory** in the results panel.

   ![Screenshot of Federated Directory in the results list.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/search-new-app.png)

4. Navigate to the **URL** highlighted below in a separate browser.

   ![Screenshot of a page in the Azure portal that displays information on Federated Directory. The U R L value is highlighted.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/federated-directory-provisioning-tutorial/loginpage1.png)

5. Select **LOG IN**.

   ![Screenshot of the main menu on the Federated Directory site. The Login button is highlighted.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/federated-directory-provisioning-tutorial/federated04.png)

6. As Federated Directory is an OpenIDConnect app, choose to log in to Federated Directory using your Microsoft work account.

   ![Screenshot of the S C I M A D test page on the Federated Directory site. Log in with your Microsoft account is highlighted.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/federated-directory-provisioning-tutorial/loginpage3.png)

7. After a successful authentication, accept the consent prompt for the consent page. The application will then be automatically added to your tenant and you'll be redirected to your Federated Directory account.

## Configuring automatic user provisioning to Federated Directory

This section guides you through the steps to configure the Microsoft Entra provisioning service to create, update, and disable users and/or groups in Federated Directory based on user and/or group assignments in Microsoft Entra ID.

### To configure automatic user provisioning for Federated Directory in Microsoft Entra ID:

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps**

   ![Screenshot of Enterprise applications blade.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/enterprise-applications.png)

3. In the applications list, select **Federated Directory**.

   ![Screenshot of the Federated Directory link in the Applications list.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/all-applications.png)

4. Select the **Provisioning** tab.

   ![Screenshot of the Manage options with the Provisioning option called out.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/provisioning.png)

5. Select **+ New configuration**.

   ![Screenshot of the Provisioning Mode dropdown list with the Automatic option called out.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/application-provisioning.png)

6. In the **Tenant URL** field, enter your Federated Directory Tenant URL and Secret Token. Select **Test Connection** to ensure Microsoft Entra ID can connect to Federated Directory. If the connection fails, ensure your Federated Directory account has the required admin permissions and try again.

   ![Screenshot of Provisioning test connection.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/provisioning-test-connection.png)

7. Select **Create** to create your configuration.
8. Select **Properties** on the **Overview** page.
9. Select the **Edit** icon to edit the properties. Enable notification emails and provide an email to receive quarantine notifications. Enable **Accidental deletions prevention**. Select **Apply** to save the changes.
10. In the **Notification Email** field, enter the email address of a person who should receive the provisioning error notifications and select the **Send an email notification when a failure occurs** check box.

    ![Screenshot of Provisioning properties.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/provisioning-properties.png)

11. Select **Attribute Mapping** in the left panel and select **users**.
12. Review the user attributes that are synchronized from Microsoft Entra ID to Federated Directory in the **Attribute Mapping** section. The attributes selected as **Matching** properties are used to match the user accounts in Federated Directory for update operations. Select the **Save** button to commit any changes.

    ![Screenshot of the Attribute Mappings page. A table lists Microsoft Entra ID and Federated Directory attributes and the matching status.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/federated-directory-provisioning-tutorial/user-attributes.png)

13. To configure scoping filters, refer to the instructions provided in the [Scoping filter article](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts).
14. Use [on-demand provisioning](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/provision-on-demand) to validate sync with a small number of users before deploying more broadly in your organization.
15. When you're ready to provision, select **Start Provisioning** from the **Overview** page.

For more information on how to read the Microsoft Entra provisioning logs, see [Reporting on automatic user account provisioning](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/check-status-user-account-provisioning)

## Additional resources

- [Managing user account provisioning for Enterprise Apps](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/configure-automatic-user-provisioning-portal)
- [What is application access and single sign-on with Microsoft Entra ID?](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/what-is-single-sign-on)

## Related content

- [Learn how to review logs and get reports on provisioning activity](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/check-status-user-account-provisioning)
