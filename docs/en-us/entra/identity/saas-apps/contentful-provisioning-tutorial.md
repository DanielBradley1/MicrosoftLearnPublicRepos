<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/contentful-provisioning-tutorial -->
<!-- Sitemap-Last-Modified: 2026-04-27 -->

# Configure Contentful for automatic user provisioning with Microsoft Entra ID

This article describes the steps you need to complete in Contentful and in Microsoft Entra ID to configure automatic user provisioning. When configured, Microsoft Entra ID automatically provisions and deprovisions users and groups to [Contentful](https://www.contentful.com/) by using the Microsoft Entra provisioning service. For important details about what this service does and how it works, and for frequently asked questions, see [Automate user provisioning and deprovisioning to SaaS applications with Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/user-provisioning).

## Capabilities supported

- Create users in Contentful
- Remove users in Contentful when they don't require access anymore
- Keep user attributes synchronized between Microsoft Entra ID and Contentful
- Provision groups and group memberships in Contentful
- [Single sign-on](https://learn.microsoft.com/en-us/entra/identity/saas-apps/contentful-tutorial) to Contentful \(recommended\)

## Prerequisites

The scenario outlined in this article assumes that you already have the following prerequisites:

- [A Microsoft Entra tenant](https://learn.microsoft.com/en-us/entra/identity-platform/quickstart-create-new-tenant).
- One of the following roles: [Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#application-administrator), [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator), or [Application Owner](https://learn.microsoft.com/en-us/entra/fundamentals/users-default-permissions#owned-enterprise-applications).
- A Contentful organization account that has a subscription that supports System for Cross-domain Identity Management \(SCIM\) provisioning. If you have questions about your organization's subscription, contact [Contentful Support](mailto:support@contentful.com).

## Plan your provisioning deployment

1. Learn about [how the provisioning service works](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/user-provisioning).
2. Determine who's in [scope for provisioning](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts).
3. Determine what data to [map between Microsoft Entra ID and Contentful](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/customize-application-attributes).

## Configure Contentful to support provisioning with Microsoft Entra ID

1. In Contentful, create a **Service User** account. All provisioning permissions for Azure are provided through this account. We recommend that you choose **Owner** as the organization role for this account.
2. Sign in to Contentful as the **Service User**.
3. In the left menu, select **Organization settings** > **Access Tools** > **User provisioning**.

   ![Screenshot of the Organization settings menu in Contentful, with User provisioning highlighted under Access Tools.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/contentful-provisioning-tutorial/access.png)

4. Copy and save the **SCIM URL**. You'll enter this value in the Azure portal, on the **Provisioning** tab of your Contentful application.
5. Select **Generate personal access token**.

   ![Screenshot showing the SCIM URL to generate a personal access token.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/contentful-provisioning-tutorial/generate.png)

6. In the modal window, enter a name for your personal access token, and then select **Generate**.
7. The SCIM URL and the secret token are generated. Copy and save these values. You'll enter these values on the **Provisioning** tab of your Contentful application.

   ![Screenshot of the Personal access token pane, with C F P A T and the token placeholder name highlighted.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/contentful-provisioning-tutorial/token.png)

If you have questions while you configure provisioning in the Contentful admin console, contact [Contentful Support](mailto:support@contentful.com).

## Add Contentful from the Microsoft Entra application gallery

To manage provisioning to Contentful, add Contentful from the Microsoft Entra application gallery. If you have previously set up Contentful for single sign-on, you can use the same application. However, we recommend that you create a separate app to initially test the integration. Learn how to [add an application in the gallery](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/add-application-portal).

## Define who is in scope for provisioning

The Microsoft Entra provisioning service allows you to scope who is provisioned based on assignment to the application, or based on attributes of the user or group. If you choose to scope who is provisioned to your app based on assignment, you can use the [steps to assign users and groups to the application](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/assign-user-or-group-access-portal). If you choose to scope who is provisioned based solely on attributes of the user or group, you can [use a scoping filter](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts).

- Start small. Test with a small set of users and groups before rolling out to everyone. When scope for provisioning is set to assigned users and groups, you can control this by assigning one or two users or groups to the app. When scope is set to all users and groups, you can specify an [attribute based scoping filter](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts).
- If you need extra roles, you can [update the application manifest](https://learn.microsoft.com/en-us/entra/identity-platform/howto-add-app-roles-in-apps) to add new roles.

## Configure automatic user provisioning to Contentful

This section guides you through the steps to set up the Microsoft Entra provisioning service to create, update, and disable users and groups in a test app based on user or group assignments in Microsoft Entra ID.

### Configure automatic user provisioning for Contentful in Microsoft Entra ID

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps**.

   ![Screenshot that shows the Enterprise applications menu in the Azure portal, with All applications highlighted.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/enterprise-applications.png)

3. In the applications list, select **Contentful**.

   ![Screenshot that shows the first 20 results returned in the Applications list.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/all-applications.png)

4. Select the **Provisioning** tab.

   ![Screenshot of the Provisioning tab highlighted in the Manage section of the left menu.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/provisioning.png)

5. Select **+ New configuration**.

   ![Screenshot of Provisioning tab automatic.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/application-provisioning.png)

6. In the **Tenant URL** field, enter your Contentful Tenant URL and Secret Token. Select **Test Connection** to ensure Microsoft Entra ID can connect to Contentful. If the connection fails, ensure your Contentful account has the required admin permissions and try again.

   ![Screenshot of Provisioning test connection.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/provisioning-test-connection.png)

7. Select **Create** to create your configuration.
8. Select **Properties** on the **Overview** page.
9. In the **Notification Email** field, enter the email address of a person who should receive the provisioning error notifications and select the **Send an email notification when a failure occurs** check box.

   ![Screenshot of Provisioning properties.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/provisioning-properties.png)

10. Select **Attribute Mapping** in the left panel and select **users**.
11. Review the user attributes that are synchronized from Microsoft Entra ID to Contentful in the **Attribute-Mapping** section. The attributes selected as **Matching** properties are used to match the user accounts in Contentful for update operations. If you choose to change the [matching target attribute](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/customize-application-attributes), you need to ensure that the Contentful API supports filtering users based on that attribute. Select the **Save** button to commit any changes.
    | Attribute | Type | Supported for filtering |
    | --- | --- | --- |
    | userName | String | ✓ |
    | name.givenName | String |  |
    | name.familyName | String |  |
12. In the **Attribute-Mapping** section, review the group attributes that are synced from Microsoft Entra ID to Contentful. The attributes selected as **Matching** properties are used to match the groups in Contentful for update operations. Select the **Save** button to commit any changes.
    | Attribute | Type | Supported for filtering |
    | --- | --- | --- |
    | displayName | String | ✓ |
    | members | Reference |  |
13. To configure scoping filters, refer to the instructions provided in the [Scoping filter article](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts).
14. Use [on-demand provisioning](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/provision-on-demand) to validate sync with a small number of users before deploying more broadly in your organization.
15. When you're ready to provision, select **Start Provisioning** from the **Overview** page.

## Monitor your deployment

Once you configure provisioning, use the following resources to monitor your deployment:

1. Use the [provisioning logs](https://learn.microsoft.com/en-us/entra/identity/monitoring-health/concept-provisioning-logs) to determine which users are provisioned successfully or unsuccessfully
2. Check the [progress bar](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/application-provisioning-when-will-provisioning-finish-specific-user) to see the status of the provisioning cycle and how close it's to completion
3. If the provisioning configuration seems to be in an unhealthy state, the application goes into quarantine. Learn more about quarantine states the [application provisioning quarantine status](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/application-provisioning-quarantine-status) article.

## Related content

- [Learn how to review logs and get reports on provisioning activity](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/check-status-user-account-provisioning)
- [Manage user account provisioning for Enterprise Apps](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/configure-automatic-user-provisioning-portal)
- [What is application access and single sign-on with Microsoft Entra ID?](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/what-is-single-sign-on)
