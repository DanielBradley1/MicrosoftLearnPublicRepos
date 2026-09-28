<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/mural-identity-provisioning-tutorial -->
<!-- Sitemap-Last-Modified: 2026-04-28 -->

# Configure MURAL Identity for automatic user provisioning with Microsoft Entra ID

This article describes the steps you need to perform in both MURAL Identity and Microsoft Entra ID to configure automatic user provisioning. When configured, Microsoft Entra ID automatically provisions and de-provisions users and groups to [MURAL Identity](https://www.mural.co/) using the Microsoft Entra provisioning service. For important details on what this service does, how it works, and frequently asked questions, see [Automate user provisioning and deprovisioning to SaaS applications with Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/user-provisioning).

## Capabilities Supported

- Create users in MURAL Identity
- Remove users in MURAL Identity when they don't require access anymore.
- Keep user attributes synchronized between Microsoft Entra ID and MURAL Identity
- Provision groups and group memberships in MURAL Identity.
- [Single sign-on](https://learn.microsoft.com/en-us/entra/identity/saas-apps/mural-identity-tutorial) to MURAL Identity \(recommended\).

## Prerequisites

The scenario outlined in this article assumes that you already have the following prerequisites:

- [A Microsoft Entra tenant](https://learn.microsoft.com/en-us/entra/identity-platform/quickstart-create-new-tenant).
- One of the following roles: [Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#application-administrator), [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator), or [Application Owner](https://learn.microsoft.com/en-us/entra/fundamentals/users-default-permissions#owned-enterprise-applications).
- SCIM provisioning is only available for MURAL’s Enterprise plan. Before you configure SCIM provisioning, please reach out to a member of the MURAL Customer Success Team to enable the feature.
- SAML based SSO must be properly set up before configuring automated provisioning. The instructions on how to set up SSO through Microsoft Entra ID for MURAL can be found [here](https://learn.microsoft.com/en-us/entra/identity/saas-apps/mural-identity-tutorial).

## Step 1: Plan your provisioning deployment

1. Learn about [how the provisioning service works](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/user-provisioning).
2. Determine who's in [scope for provisioning](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts).
3. Determine what data to [map between Microsoft Entra ID and MURAL Identity](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/customize-application-attributes).

## Step 2: Configure MURAL Identity to support provisioning with Microsoft Entra ID

Follow the [steps](https://developers.mural.co/enterprise/docs/set-up-the-scim-api) to get your SCIM URL and unique API Token from the API keys page in your MURAL Company dashboard. Use this key in the Secret Token field in **Step 5**.

## Step 3: Add MURAL Identity from the Microsoft Entra application gallery

Add MURAL Identity from the Microsoft Entra application gallery to start managing provisioning to MURAL Identity. If you have previously setup MURAL Identity for SSO you can use the same application. However, we recommend that you create a separate app when testing out the integration initially. Learn more about adding an application from the gallery [here](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/add-application-portal).

## Step 4: Define who is in scope for provisioning

The Microsoft Entra provisioning service allows you to scope who is provisioned based on assignment to the application, or based on attributes of the user or group. If you choose to scope who is provisioned to your app based on assignment, you can use the [steps to assign users and groups to the application](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/assign-user-or-group-access-portal). If you choose to scope who is provisioned based solely on attributes of the user or group, you can [use a scoping filter](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts).

- Start small. Test with a small set of users and groups before rolling out to everyone. When scope for provisioning is set to assigned users and groups, you can control this by assigning one or two users or groups to the app. When scope is set to all users and groups, you can specify an [attribute based scoping filter](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts).
- If you need extra roles, you can [update the application manifest](https://learn.microsoft.com/en-us/entra/identity-platform/howto-add-app-roles-in-apps) to add new roles.

## Step 5: Configure automatic user provisioning to MURAL Identity

This section guides you through the steps to configure the Microsoft Entra provisioning service to create, update, and disable users and/or groups in MURAL Identity based on user and/or group assignments in Microsoft Entra ID.

### To configure automatic user provisioning for MURAL Identity in Microsoft Entra ID:

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps**

   ![Enterprise applications blade](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/enterprise-applications.png)

3. In the applications list, select **MURAL Identity**.

   ![The MURAL Identity link in the Applications list](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/all-applications.png)

4. Select the **Provisioning** tab.

   ![Provisioning tab](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/provisioning.png)

5. Select **+ New configuration**.

   ![Screenshot of Provisioning tab automatic.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/application-provisioning.png)

6. In the **Tenant URL** field, enter your MURAL Identity Tenant URL and Secret Token. Select **Test Connection** to ensure Microsoft Entra ID can connect to MURAL Identity. If the connection fails, ensure your MURAL Identity account has the required admin permissions and try again.

   ![Screenshot of Provisioning test connection.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/provisioning-test-connection.png)

7. Select **Create** to create your configuration.
8. Select **Properties** on the **Overview** page.
9. In the **Notification Email** field, enter the email address of a person who should receive the provisioning error notifications and select the **Send an email notification when a failure occurs** check box.

   ![Screenshot of Provisioning properties.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/provisioning-properties.png)

10. Select **Attribute Mapping** in the left panel and select **users**.
11. Review the user attributes that are synchronized from Microsoft Entra ID to MURAL Identity in the **Attribute-Mapping** section. The attributes selected as **Matching** properties are used to match the user accounts in MURAL Identity for update operations. If you choose to change the [matching target attribute](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/customize-application-attributes), you need to ensure that the MURAL Identity API supports filtering users based on that attribute. Select the **Save** button to commit any changes.
    | Attribute | Type | Supported for filtering | Required by MURAL Identity |
    | --- | --- | --- | --- |
    | userName | String | ✓ | ✓ |
    | emails\[type eq "work"\].value | String |  | ✓ |
    | active | Boolean |  |  |
    | name.givenName | String |  |  |
    | name.familyName | String |  |  |
    | externalId | String |  |  |
12. Review the group attributes that are synchronized from Microsoft Entra ID to MURAL Identity in the **Attribute-Mapping** section. The attributes selected as **Matching** properties are used to match the groups in MURAL Identity for update operations. Select the **Save** button to commit any changes.
    | Attribute | Type | Supported for filtering | Required by MURAL Identity |
    | --- | --- | --- | --- |
    | displayName | String | ✓ | ✓ |
    | members | Reference |  |  |
    | externalId | String |  |  |
13. To configure scoping filters, refer to the instructions provided in the [Scoping filter article](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts).
14. Use [on-demand provisioning](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/provision-on-demand) to validate sync with a small number of users before deploying more broadly in your organization.
15. When you're ready to provision, select **Start Provisioning** from the **Overview** page.

## Step 6: Monitor your deployment

Once you configure provisioning, use the following resources to monitor your deployment:

1. Use the [provisioning logs](https://learn.microsoft.com/en-us/entra/identity/monitoring-health/concept-provisioning-logs) to determine which users are provisioned successfully or unsuccessfully
2. Check the [progress bar](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/application-provisioning-when-will-provisioning-finish-specific-user) to see the status of the provisioning cycle and how close it's to completion
3. If the provisioning configuration seems to be in an unhealthy state, the application goes into quarantine. Learn more about quarantine states the [application provisioning quarantine status](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/application-provisioning-quarantine-status) article.

## Troubleshooting Tips

- When provisioning a user keep in mind that at MURAL we don't support numbers in the name fields \(that is, givenName or familyName\).
- When filtering on **userName** in the GET endpoint make sure that the email address is all lowercase otherwise you get an empty result. This is because we convert email addresses to lowercase while provisioning accounts.
- When de-provisioning an end-user \(setting the active attribute to false\), user is soft-deleted and lose access to all their workspaces. When that same de-provisioned end-user is later activated again \(setting the active attribute to true\), user doesn't have access to the workspaces user previously belonged to. The end-user will see an error message "You’ve been deactivated from this workspace", with an option to request reactivation which the workspace admin must approve.
- If you have any other issues, please reach out to [MURAL Identity support team](mailto:support@mural.co).

## Change log

06/22/2023 - Added support for **Group Provisioning**.

## More resources

- [Managing user account provisioning for Enterprise Apps](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/configure-automatic-user-provisioning-portal)
- [What is application access and single sign-on with Microsoft Entra ID?](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/what-is-single-sign-on)

## Related content

- [Learn how to review logs and get reports on provisioning activity](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/check-status-user-account-provisioning)
