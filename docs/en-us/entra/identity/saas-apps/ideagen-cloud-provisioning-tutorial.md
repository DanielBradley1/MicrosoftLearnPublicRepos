<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/ideagen-cloud-provisioning-tutorial -->
<!-- Sitemap-Last-Modified: 2026-04-27 -->

# Configure Ideagen Cloud for automatic user provisioning with Microsoft Entra ID

This article describes the steps you need to perform in both Ideagen Cloud and Microsoft Entra ID to configure automatic user provisioning. When configured, Microsoft Entra ID automatically provisions and de-provisions users and groups to [Ideagen Cloud](https://www.ideagen.com/) using the Microsoft Entra provisioning service. For important details on what this service does, how it works, and frequently asked questions, see [Automate user provisioning and deprovisioning to SaaS applications with Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/user-provisioning).

## Capabilities supported

- Create users in Ideagen Cloud.
- Remove users in Ideagen Cloud when they don't require access anymore.
- Keep user attributes synchronized between Microsoft Entra ID and Ideagen Cloud.
- Long lived bearer token authentication supported.

## Prerequisites

The scenario outlined in this article assumes that you already have the following prerequisites:

- [A Microsoft Entra tenant](https://learn.microsoft.com/en-us/entra/identity-platform/quickstart-create-new-tenant).
- One of the following roles: [Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#application-administrator), [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator), or [Application Owner](https://learn.microsoft.com/en-us/entra/fundamentals/users-default-permissions#owned-enterprise-applications).
- The Tenant URL and Secret Token.

## Step 1: Plan your provisioning deployment

1. Learn about [how the provisioning service works](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/user-provisioning).
2. Determine who's in [scope for provisioning](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts).
3. Determine what data to [map between Microsoft Entra ID and Ideagen Cloud](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/customize-application-attributes).

## Step 2: Configure Ideagen Cloud to support provisioning with Microsoft Entra ID

1. Log in to Ideagen. Select the **Administration** icon to show the left hand side menu.

   ![Screenshot of administration menu.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/ideagen-cloud-provisioning-tutorial/admin.png)

2. Navigate to **Authentication** page under the **Manage tenant** sub menu.

   ![Screenshot of authentication page.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/ideagen-cloud-provisioning-tutorial/authentication.png)

3. Select Edit button and select **Enabled** checkbox under automatic provisioning.

   ![Screenshot of allow provisioning.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/ideagen-cloud-provisioning-tutorial/allow-provisioning.png)

4. Select **Save** button to save the changes.
5. Scroll down in the Authentication Page to **Client Token** section and select **Regenerate** .

   ![Screenshot of token generation.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/ideagen-cloud-provisioning-tutorial/generate-token.png)

6. **Copy** and save the Bearer Token. This value is entered in the Secret Token \* field in the Provisioning tab of your Ideagen Cloud application.

   ![Screenshot of copying token.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/ideagen-cloud-provisioning-tutorial/copy-token.png)

7. Locate the **SCIM URL** and keep the value for later use. This value is used as Tenant URL when configuring automatic user provisioning in Azure portal.

## Step 3: Add Ideagen Cloud from the Microsoft Entra application gallery

Add Ideagen Cloud from the Microsoft Entra application gallery to start managing provisioning to Ideagen Cloud. If you have previously setup Ideagen Cloud for SSO, you can use the same application. However, we recommend that you create a separate app when testing out the integration initially. Learn more about adding an application from the gallery [here](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/add-application-portal).

## Step 4: Define who is in scope for provisioning

The Microsoft Entra provisioning service allows you to scope who is provisioned based on assignment to the application, or based on attributes of the user or group. If you choose to scope who is provisioned to your app based on assignment, you can use the [steps to assign users and groups to the application](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/assign-user-or-group-access-portal). If you choose to scope who is provisioned based solely on attributes of the user or group, you can [use a scoping filter](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts).

- Start small. Test with a small set of users and groups before rolling out to everyone. When scope for provisioning is set to assigned users and groups, you can control this by assigning one or two users or groups to the app. When scope is set to all users and groups, you can specify an [attribute based scoping filter](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts).
- If you need extra roles, you can [update the application manifest](https://learn.microsoft.com/en-us/entra/identity-platform/howto-add-app-roles-in-apps) to add new roles.

## Step 5: Configure automatic user provisioning to Ideagen Cloud

This section guides you through the steps to configure the Microsoft Entra provisioning service to create, update, and disable users and/or groups in Ideagen Cloud based on user and/or group assignments in Microsoft Entra ID.

### To configure automatic user provisioning for Ideagen Cloud in Microsoft Entra ID:

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps**

   ![Screenshot of Enterprise applications blade.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/enterprise-applications.png)

3. In the applications list, select **Ideagen Cloud**.

   ![Screenshot of the Ideagen Cloud link in the Applications list.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/all-applications.png)

4. Select the **Provisioning** tab.

   ![Screenshot of Provisioning tab,](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/provisioning.png)

5. Select **+ New configuration**.

   ![Screenshot of the New configuration option on the Provisioning page.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/application-provisioning.png)

6. In the **Tenant URL** field, enter your Ideagen Cloud Tenant URL and Secret Token. Select **Test Connection** to ensure Microsoft Entra ID can connect to Ideagen Cloud. If the connection fails, ensure your Ideagen Cloud account has the required admin permissions and try again.

   ![Screenshot of Provisioning test connection.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/provisioning-test-connection.png)

7. Select **Create** to create your configuration.
8. Select **Properties** on the **Overview** page.
9. Select the **Edit** icon to edit the properties. Enable notification emails and provide an email to receive quarantine notifications. Enable **Accidental deletions prevention**. Select **Apply** to save the changes.
10. In the **Notification Email** field, enter the email address of a person who should receive the provisioning error notifications and select the **Send an email notification when a failure occurs** check box.

    ![Screenshot of the Provisioning properties configuration page.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/provisioning-properties.png)

11. Select **Attribute Mapping** in the left panel and select **users**.
12. Review the user attributes that are synchronized from Microsoft Entra ID to Ideagen Cloud in the **Attribute-Mapping** section. The attributes selected as **Matching** properties are used to match the user accounts in Ideagen Cloud for update operations. If you choose to change the [matching target attribute](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/customize-application-attributes), you need to ensure that the Ideagen Cloud API supports filtering users based on that attribute. Select the **Save** button to commit any changes.
    | Attribute | Type | Supported for filtering | Required by Ideagen Cloud |
    | --- | --- | --- | --- |
    | userName | String | ✓ | ✓ |
    | active | Boolean |  | ✓ |
    | displayName | String |  | ✓ |
    | title | String |  |  |
    | emails\[type eq "work"\].value | String |  | ✓ |
    | preferredLanguage | String |  |  |
    | name.givenName | String |  | ✓ |
    | name.familyName | String |  | ✓ |
    | externalId | String |  | ✓ |


    Note


    All the required fields \(for example, first name, last name and email\) are required to be filled in Microsoft Entra ID in order to get the auto provision work without any issue.

13. To configure scoping filters, refer to the instructions provided in the [Scoping filter article](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts).
14. Use [on-demand provisioning](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/provision-on-demand) to validate sync with a small number of users before deploying more broadly in your organization.
15. When you're ready to provision, select **Start Provisioning** from the **Overview** page.

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
