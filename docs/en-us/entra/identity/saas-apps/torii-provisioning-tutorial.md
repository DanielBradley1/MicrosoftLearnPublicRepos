<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/torii-provisioning-tutorial -->
<!-- Sitemap-Last-Modified: 2026-04-28 -->

# Configure Torii for automatic user provisioning with Microsoft Entra ID

This article describes the steps you need to perform in both Torii and Microsoft Entra ID to configure automatic user provisioning. When configured, Microsoft Entra ID automatically provisions and de-provisions users to [Torii](https://toriihq.com) using the Microsoft Entra provisioning service. For important details on what this service does, how it works, and frequently asked questions, see [Automate user provisioning and deprovisioning to SaaS applications with Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/user-provisioning).

## Supported capabilities

- Create users in Torii.
- Remove users in Torii when they don't require access anymore.
- Keep user attributes synchronized between Microsoft Entra ID and Torii.
- [Single sign-on](https://learn.microsoft.com/en-us/entra/identity/saas-apps/torii-tutorial) to Torii \(recommended\).

## Prerequisites

The scenario outlined in this article assumes that you already have the following prerequisites:

- [A Microsoft Entra tenant](https://learn.microsoft.com/en-us/entra/identity-platform/quickstart-create-new-tenant)
- One of the following roles: [Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#application-administrator), [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator), or [Application Owner](https://learn.microsoft.com/en-us/entra/fundamentals/users-default-permissions#owned-enterprise-applications).
- An administrator account with Torii.

## Step 1: Plan your provisioning deployment

1. Learn about [how the provisioning service works](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/user-provisioning).
2. Determine who's in [scope for provisioning](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts).
3. Determine what data to [map between Microsoft Entra ID and Torii](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/customize-application-attributes).

## Step 2: Configure Torii to support provisioning with Microsoft Entra ID

1. Log in to [Torii admin console](https://app.toriihq.com).
2. Navigate to [Settings](https://app.toriihq.com/team/settings/apiAccess) page > **Security**, enable the SCIM toggle.

   ![Screenshot of SCIM Toggle.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/torii-provisioning-tutorial/scim-enabled.png)

3. Navigate to the **API Access** tab. From here, you can view and manage the Torii API keys and SCIM.
4. Select **Generate API Key** to generate a new SCIM.

   ![Screenshot of Generate API Key.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/torii-provisioning-tutorial/generate-key.png)

5. Choose type: **SCIM**.
6. Add **Description** and set **Expiration date**. For security purposes, we recommend setting an expiration date when generating a new key.
7. Select **Generate key**.
8. Copy and save the API Key as it won't be available next. This value is entered in the **Secret Token** field in the Provisioning tab of your Torii application.
9. Select **Got it**.

   ![Screenshot of Create API Key.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/torii-provisioning-tutorial/create-key.png)


   ![Screenshot of Copy API Key.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/torii-provisioning-tutorial/copy-key.png)

10. **Torii Tenant Url:** `https://api.toriihq.com/v1.0/scim/v2` is entered in the **Tenant URL** field in the Provisioning tab of your Torii application.

## Step 3: Add Torii from the Microsoft Entra application gallery

Add Torii from the Microsoft Entra application gallery to start managing provisioning to Torii. If you have previously setup Torii for SSO you can use the same application. However it's recommended that you create a separate app when testing out the integration initially. Learn more about adding an application from the gallery [here](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/add-application-portal).

## Step 4: Define who is in scope for provisioning

The Microsoft Entra provisioning service allows you to scope who is provisioned based on assignment to the application, or based on attributes of the user or group. If you choose to scope who is provisioned to your app based on assignment, you can use the [steps to assign users and groups to the application](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/assign-user-or-group-access-portal). If you choose to scope who is provisioned based solely on attributes of the user or group, you can [use a scoping filter](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts).

- Start small. Test with a small set of users and groups before rolling out to everyone. When scope for provisioning is set to assigned users and groups, you can control this by assigning one or two users or groups to the app. When scope is set to all users and groups, you can specify an [attribute based scoping filter](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts).
- If you need extra roles, you can [update the application manifest](https://learn.microsoft.com/en-us/entra/identity-platform/howto-add-app-roles-in-apps) to add new roles.

## Step 5: Configure automatic user provisioning to Torii

This section guides you through the steps to configure the Microsoft Entra provisioning service to create, update, and disable users in TestApp based on user and/or group assignments in Microsoft Entra ID.

### Configure automatic user provisioning for Torii in Microsoft Entra ID

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps**

   ![Screenshot of Enterprise applications blade.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/enterprise-applications.png)

3. In the applications list, select **Torii**.

   ![Screenshot of the Torii link in the Applications list.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/all-applications.png)

4. Select the **Provisioning** tab.

   ![Screenshot of Provisioning tab.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/provisioning.png)

5. Select **+ New configuration**.

   ![Screenshot of New configuration.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/application-provisioning.png)

6. In the **Tenant URL** field, enter your Torii Tenant URL and Secret Token. Select **Test Connection** to ensure Microsoft Entra ID can connect to Torii. If the connection fails, ensure your Torii account has the required admin permissions and try again.

   ![Screenshot of Provisioning test connection.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/provisioning-test-connection.png)

7. Select **Create** to create your configuration.
8. Select **Properties** on the **Overview** page.
9. Select the **Edit** icon to edit the properties. Enable notification emails and provide an email to receive quarantine notifications. Enable **Accidental deletions prevention**. Select **Apply** to save the changes.

   ![Screenshot of Provisioning properties.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/provisioning-properties.png)

10. Select **Attribute Mapping** in the left panel and select **users**.
11. Review the user attributes that are synchronized from Microsoft Entra ID to Torii in the **Attribute-Mapping** section. The attributes selected as **Matching** properties are used to match the user accounts in Torii for update operations. If you choose to change the [matching target attribute](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/customize-application-attributes), you need to ensure that the Torii API supports filtering users based on that attribute. Select the **Save** button to commit any changes.
    | Attribute | Type | Supported for filtering | Required by Torii |
    | --- | --- | --- | --- |
    | userName | String | ✓ | ✓ |
    | active | Boolean |  |  |
    | name.givenName | String |  |  |
    | name.familyName | String |  |  |
    | userType | String |  |  |


    Note


    - **userName** must be a valid email address with a valid domain.
    - **userType**\(role in Torii\):
    - It must be exactly as appear at Torii
    - If **userType** is empty, the user gets the **Employee** role as the default.
    - The user types\(roles\) appear [here](https://support.toriihq.com/hc/en-us/articles/6174005637787#h_01G6FRWNXDJG89HCBD93PNYW4H).
    - Only admin users \(not from type "Employee"\) is displayed in Torii's UI
    - Read more about Torii's attributes [here](https://support.toriihq.com/hc/en-us/articles/9183460072347-Torii-s-SCIM-User-Provisioning#heading-3).

12. To configure scoping filters, refer to the instructions provided in the [Scoping filter article](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts).
13. Use [on-demand provisioning](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/provision-on-demand) to validate sync with a small number of users before deploying more broadly in your organization.
14. When you're ready to provision, select **Start Provisioning** from the **Overview** page.

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
