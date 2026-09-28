<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/salesforce-sandbox-provisioning-tutorial -->
<!-- Sitemap-Last-Modified: 2026-03-26 -->

# Configure Salesforce Sandbox for automatic user provisioning with Microsoft Entra ID

The objective of this article is to show you the steps you need to perform in Salesforce Sandbox and Microsoft Entra ID to automatically provision and de-provision user accounts from Microsoft Entra ID to Salesforce Sandbox.

## Prerequisites

The scenario outlined in this article assumes that you already have the following items:

- A Microsoft Entra tenant.
- A valid tenant for Salesforce Sandbox for Work or Salesforce Sandbox for Education. You may use a free trial account for either service.
- A user account in Salesforce Sandbox with Team Admin permissions.

## Assigning users to Salesforce Sandbox

Microsoft Entra ID uses a concept called "assignments" to determine which users should receive access to selected apps. In the context of automatic user account provisioning, only the users and groups that have been "assigned" to an application in Microsoft Entra ID are synchronized.

Before configuring and enabling the provisioning service, you need to decide which users or groups in Microsoft Entra ID need access to your Salesforce Sandbox app. After you've made this decision, you can assign these users to your Salesforce Sandbox app by following the instructions in [Assign a user or group to an enterprise app](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/assign-user-or-group-access-portal)

### Important tips for assigning users to Salesforce Sandbox

- It's recommended that a single Microsoft Entra user is assigned to Salesforce Sandbox to test the provisioning configuration. Additional users and/or groups may be assigned later.
- When assigning a user to Salesforce Sandbox, you must select a valid user role. The "Default Access" role doesn't work for provisioning.

Note

The Salesforce Sandbox app will, by default, append a string to the username and email of the users provisioned. Usernames and Emails have to be unique across all of Salesforce so this is to prevent creating real user data in the sandbox which would prevent these users being provisioned to the production Salesforce environment

Note

This app imports custom roles from Salesforce Sandbox as part of the provisioning process, which the customer may want to select when assigning users.

## Enable automated user provisioning

This section guides you through connecting your Microsoft Entra ID to Salesforce Sandbox's user account provisioning API, and configuring the provisioning service to create, update, and disable assigned user accounts in Salesforce Sandbox based on user and group assignment in Microsoft Entra ID.

Tip

You may also choose to enabled SAML-based Single Sign-On for Salesforce Sandbox, following the instructions provided in the [Azure portal](https://portal.azure.com). Single sign-on can be configured independently of automatic provisioning, though these two features complement each other.

### Configure automatic user account provisioning

The objective of this section is to outline how to enable user provisioning of Active Directory user accounts to Salesforce Sandbox.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps**.
3. If you have already configured Salesforce Sandbox for single sign-on, search for your instance of Salesforce Sandbox using the search field. Otherwise, select **Add** and search for **Salesforce Sandbox** in the application gallery. Select Salesforce Sandbox from the search results, and add it to your list of applications.
4. Select your instance of Salesforce Sandbox, then select the **Provisioning** tab.
5. Select **+ New configuration**.

   ![Screenshot of Provisioning tab automatic.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/application-provisioning.png)

6. Under the **Admin Credentials** section, provide the following configuration settings:

   1. In the **Admin Username** textbox, type a Salesforce Sandbox account name that has the **System Administrator** profile in Salesforce.com assigned.
   2. In the **Admin Password** textbox, type the password for this account.

7. To get your Salesforce Sandbox security token, open a new tab and sign into the same Salesforce Sandbox admin account. On the top right corner of the page, select your name, and then select **Settings**.

   ![Screenshot shows the Settings link selected.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/salesforce-sandbox-provisioning-tutorial/sf-my-settings.png "Enable automatic user provisioning")

8. On the left navigation pane, select **My Personal Information** to expand the related section, and then select **Reset My Security Token**.

   ![Screenshot shows Reset My Security Token selected from My Personal Information.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/salesforce-sandbox-provisioning-tutorial/sf-personal-reset.png "Enable automatic user provisioning")

9. On the **Reset Security Token** page, select the **Reset Security Token** button.

   ![Screenshot shows the Rest Security Token page, with explanatory text and the option to Reset Security Token](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/salesforce-sandbox-provisioning-tutorial/sf-reset-token.png "Enable automatic user provisioning")

10. Check the email inbox associated with this admin account. Look for an email from Salesforce Sandbox.com that contains the new security token.
11. Copy the token, go to your Microsoft Entra window, and paste it into the **Secret Token** field.
12. Select **Test Connection** to ensure Microsoft Entra ID can connect to your Salesforce Sandbox app.
13. Select **Create** to create your configuration.
14. Select **Properties** on the **Overview** page.
15. Select the **Edit** icon to edit the properties. Enable notification emails and provide an email to receive quarantine emails. Enable accidental deletions prevention. Select **Apply** to save the changes.

    ![Screenshot of Provisioning properties.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/provisioning-properties.png)

16. Select **Attribute Mapping** in the left panel and select **users**.
17. Review the user attributes that are synchronized from Microsoft Entra ID to Salesforce Sandbox. The attributes selected as **Matching** properties are used to match the user accounts in Salesforce Sandbox for update operations. Select the Save button to commit any changes.
18. To configure scoping filters, refer to the following instructions provided in the [Scoping filter article](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts).
19. Use [on-demand provisioning](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/provision-on-demand) to validate sync with a small number of users before deploying more broadly in your organization.
20. When you're ready to provision, select **Start Provisioning** from the **Overview** page.

## Monitor your deployment

Once you configure provisioning, use the following resources to monitor your deployment:

1. Use the [provisioning logs](https://learn.microsoft.com/en-us/entra/identity/monitoring-health/concept-provisioning-logs) to determine which users are provisioned successfully or unsuccessfully
2. Check the [progress bar](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/application-provisioning-when-will-provisioning-finish-specific-user) to see the status of the provisioning cycle and how close it's to completion
3. If the provisioning configuration seems to be in an unhealthy state, the application goes into quarantine. Learn more about quarantine states the [application provisioning quarantine status](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/application-provisioning-quarantine-status) article.

## Additional resources

- [Managing user account provisioning for Enterprise Apps](https://learn.microsoft.com/en-us/entra/identity/saas-apps/tutorial-list)
- [What is application access and single sign-on with Microsoft Entra ID?](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/what-is-single-sign-on)
- [Configure Single Sign-on](https://learn.microsoft.com/en-us/entra/identity/saas-apps/salesforce-sandbox-tutorial)
