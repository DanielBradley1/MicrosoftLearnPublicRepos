<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/citrixgotomeeting-provisioning-tutorial -->
<!-- Sitemap-Last-Modified: 2026-03-05 -->

# Configure GoToMeeting for automatic user provisioning with Microsoft Entra ID

The objective of this article is to show you the steps you need to perform in GoToMeeting and Microsoft Entra ID to automatically provision and de-provision user accounts from Microsoft Entra ID to GoToMeeting.

Warning

This provisioning integration is no longer supported. As a result of this, the provisioning functionality of the GoToMeeting application in the Microsoft Entra Enterprise App Gallery is removed soon. The application's SSO functionality will remain intact. Microsoft is working with GoToMeeting to build a new modernized provisioning integration, but there are no timelines on when it's completed.

## Prerequisites

The scenario outlined in this article assumes that you already have the following items:

- A Microsoft Entra tenant.
- A GoToMeeting single sign-on enabled subscription.
- A user account in GoToMeeting with Team Admin permissions.

## Assigning users to GoToMeeting

Microsoft Entra ID uses a concept called "assignments" to determine which users should receive access to selected apps. In the context of automatic user account provisioning, only the users and groups that have been "assigned" to an application in Microsoft Entra ID is synchronized.

Before configuring and enabling the provisioning service, you need to decide what users and/or groups in Microsoft Entra ID represent the users who need access to your GoToMeeting app. Once decided, you can assign these users to your GoToMeeting app by following the instructions here:

[Assign a user or group to an enterprise app](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/assign-user-or-group-access-portal)

### Important tips for assigning users to GoToMeeting

- It's recommended that a single Microsoft Entra user is assigned to GoToMeeting to test the provisioning configuration. Additional users and/or groups may be assigned later.
- When assigning a user to GoToMeeting, you must select a valid user role. The "Default Access" role doesn't work for provisioning.

## Enable Automated User Provisioning

This section guides you through connecting your Microsoft Entra ID to GoToMeeting's user account provisioning API, and configuring the provisioning service to create, update, and disable assigned user accounts in GoToMeeting based on user and group assignment in Microsoft Entra ID.

Tip

You may also choose to enable SAML-based single sign-on for GoToMeeting, following the instructions provided in the [Azure portal](https://portal.azure.com). Single sign-on can be configured independently of automatic provisioning, though these two features complement each other.

### To configure automatic user account provisioning:

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps**.
3. If you have already configured GoToMeeting for single sign-on, search for your instance of GoToMeeting using the search field. Otherwise, select **Add** and search for **GoToMeeting** in the application gallery. Select GoToMeeting from the search results, and add it to your list of applications.
4. Select your instance of GoToMeeting, then select the **Provisioning** tab.
5. Set **+ New configuration**.

   ![Screenshot of Provisioning tab automatic.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/application-provisioning.png)

6. In the **Tenant URL** field, input your GoToMeeting Tenant URL and Secret Token. Select **Test Connection** to ensure Microsoft Entra ID can connect to GoToMeeting. If the connection fails, ensure your GoToMeeting account has the required admin permissions and try again.

   ![Screenshot of Provisioning test connection.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/provisioning-test-connection.png)

7. Select **Create** to create your configuration.
8. Select **Properties** in the **Overview** page.
9. Select the pencil to edit the properties. Enable notification emails and provide an email to receive quarantine emails. Enable accidental deletions prevention. Select **Apply** to save the changes.

   ![Screenshot of Provisioning properties.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/provisioning-properties.png)

10. Select **Attribute Mapping** in the left panel and select **users**.
11. Review the user attributes that are synchronized from Microsoft Entra ID to GoToMeeting. The attributes selected as **Matching** properties are used to match the user accounts in GoToMeeting for update operations. Select the Save button to commit any changes.
12. To configure scoping filters, refer to the following instructions provided in the [Scoping filter article](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts).
13. Use [on-demand provisioning](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/provision-on-demand) to validate sync with a small number of users before deploying more broadly in your organization.
14. When you're ready to provision, select **Start Provisioning** from the **Overview** page.

## Monitor your deployment

Once you configure provisioning, use the following resources to monitor your deployment:

1. Use the [provisioning logs](https://learn.microsoft.com/en-us/entra/identity/monitoring-health/concept-provisioning-logs) to determine which users are provisioned successfully or unsuccessfully
2. Check the [progress bar](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/application-provisioning-when-will-provisioning-finish-specific-user) to see the status of the provisioning cycle and how close it's to completion
3. If the provisioning configuration seems to be in an unhealthy state, the application goes into quarantine. Learn more about quarantine states the [application provisioning quarantine status](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/application-provisioning-quarantine-status) article.

## Additional resources

- [Managing user account provisioning for Enterprise Apps](https://learn.microsoft.com/en-us/entra/identity/saas-apps/tutorial-list)
- [What is application access and single sign-on with Microsoft Entra ID?](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/what-is-single-sign-on)
- [Configure Single Sign-on](https://learn.microsoft.com/en-us/entra/identity/saas-apps/citrix-gotomeeting-tutorial)
