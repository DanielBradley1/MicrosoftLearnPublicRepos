<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/uniflow-online-provisioning-tutorial -->
<!-- Sitemap-Last-Modified: 2026-04-10 -->

# Configure uniFLOW Online for automatic user provisioning with Microsoft Entra ID

This article describes the steps you need to perform in both uniFLOW Online and Microsoft Entra ID to configure automatic user provisioning. When configured, Microsoft Entra ID automatically provisions and de-provisions users to [uniFLOW Online](https://www.uniflowonline.com/) using the Microsoft Entra provisioning service. For important details on what this service does, how it works, and frequently asked questions, see [Automate user provisioning and deprovisioning to SaaS applications with Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/user-provisioning).

## Supported capabilities

- Create users in uniFLOW Online.
- Disable users in uniFLOW Online.
- Remove users in uniFLOW Online when they don't require access anymore.
- Keep user attributes synchronized between Microsoft Entra ID and uniFLOW Online.
- [Single sign-on](https://learn.microsoft.com/en-us/entra/identity/saas-apps/uniflow-online-tutorial) to uniFLOW Online \(recommended\).
- Long lived bearer token authentication supported.

## Prerequisites

The scenario outlined in this article assumes that you already have the following prerequisites:

- [A Microsoft Entra tenant](https://learn.microsoft.com/en-us/entra/identity-platform/quickstart-create-new-tenant)
- One of the following roles: [Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#application-administrator), [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator), or [Application Owner](https://learn.microsoft.com/en-us/entra/fundamentals/users-default-permissions#owned-enterprise-applications).
- An administrator account with uniFLOW Online.

## Step 1: Plan your provisioning deployment

1. Learn about [how the provisioning service works](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/user-provisioning).
2. Determine who's in [scope for provisioning](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts).
3. Determine what data to [map between Microsoft Entra ID and uniFLOW Online](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/customize-application-attributes).

## Step 2: Configure uniFLOW Online to support provisioning with Microsoft Entra ID

- In a different web browser window, sign in to uniFLOW Online website as an administrator.
- Select **Extensions** tab **> Identity Providers > Configure identity providers**.
- Select **Add identity provider**. On the **ADD IDENTITY PROVIDER** section, perform the following steps:

  - Enter the **Display name** .
  - For **Provider type**, select **WS-Federation** option from the dropdown.
  - For **WS-Federation type**, select **Microsoft Entra ID** option from the dropdown.
  - Select **Save**.

- Enable the Advanced Administrative View within your user Profile settings by navigating to **Profile settings > Administrator view** and setting it to **Advanced**.
- The provisioning tab will now be available within the Identity Provider configuration.
- Select **Enable Provisioning** when you're ready to set up user provisioning in your company's Microsoft Entra ID.

  - **Provisioning tenant URL** \(only displayed once after **Provisioning** is enabled\): You need this URL when setting up provisioning in your Microsoft Entra application.
  - **Provisioning secret token** \(only displayed once after **Provisioning** is enabled\): You need this token when setting up provisioning in your Microsoft Entra application.

## Step 3: Add uniFLOW Online from the Microsoft Entra application gallery

Add uniFLOW Online from the Microsoft Entra application gallery to start managing provisioning to uniFLOW Online. If you have previously setup uniFLOW Online for SSO you can use the same application. However it's recommended that you create a separate app when testing out the integration initially. Learn more about adding an application from the gallery [here](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/add-application-portal).

## Step 4: Define who is in scope for provisioning

The Microsoft Entra provisioning service allows you to scope who is provisioned based on assignment to the application, or based on attributes of the user or group. If you choose to scope who is provisioned to your app based on assignment, you can use the [steps to assign users and groups to the application](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/assign-user-or-group-access-portal). If you choose to scope who is provisioned based solely on attributes of the user or group, you can [use a scoping filter](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts).

- Start small. Test with a small set of users and groups before rolling out to everyone. When scope for provisioning is set to assigned users and groups, you can control this by assigning one or two users or groups to the app. When scope is set to all users and groups, you can specify an [attribute based scoping filter](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts).
- If you need extra roles, you can [update the application manifest](https://learn.microsoft.com/en-us/entra/identity-platform/howto-add-app-roles-in-apps) to add new roles.

## Step 5: Configure automatic user provisioning to uniFLOW Online

This section guides you through the steps to configure the Microsoft Entra provisioning service to create, update, and disable users and/or groups in TestApp based on user and/or group assignments in Microsoft Entra ID.

### Configure automatic user provisioning for uniFLOW Online in Microsoft Entra ID

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps**

   ![Screenshot of Enterprise applications blade.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/enterprise-applications.png)

3. In the applications list, select **uniFLOW Online**.

   ![Screenshot of the uniFlow Online link in the Applications list.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/all-applications.png)

4. Select the **Provisioning** tab.

   ![Screenshot of Provisioning tab.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/provisioning.png)

5. Select **+ New configuration**.

   ![Screenshot of New configuration.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/application-provisioning.png)

6. In the **Tenant URL** field, enter your uniFLOW Online Tenant URL and Secret Token. Select **Test Connection** to ensure Microsoft Entra ID can connect to uniFLOW Online. If the connection fails, ensure your uniFLOW Online account has the required admin permissions and try again.

   ![Screenshot of Provisioning test connection.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/provisioning-test-connection.png)

7. Select **Create** to create your configuration.
8. Select **Properties** on the **Overview** page.
9. Select the **Edit** icon to edit the properties. Enable notification emails and provide an email to receive quarantine notifications. Enable **Accidental deletions prevention**. Select **Apply** to save the changes.

   ![Screenshot of Provisioning properties.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/provisioning-properties.png)

10. Select **Attribute Mapping** in the left panel and select **users**.
11. Review the user attributes that are synchronized from Microsoft Entra ID to uniFLOW Online in the **Attribute-Mapping** section. The attributes selected as **Matching** properties are used to match the user accounts in uniFLOW Online for update operations. If you choose to change the [matching target attribute](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/customize-application-attributes), you need to ensure that the uniFLOW Online API supports filtering users based on that attribute. Select the **Save** button to commit any changes.
    | Attribute | Type | Supported for filtering | Required by uniFLOW Online |
    | --- | --- | --- | --- |
    | userName | String | ✓ | ✓ |
    | externalId | String | ✓ | ✓ |
    | emails\[type eq "work"\].value | String | ✓ |  |
    | active | Boolean |  | ✓ |
    | urn:ietf:params:scim:schemas:extension:enterprise:2.0:User:department | String |  |  |
    | displayName | String |  |  |
    | title | String |  |  |
    | addresses\[type eq "work"\].streetAddress | String |  |  |
    | title | String |  |  |
    | phoneNumbers\[type eq "work"\].value | String |  |  |
    | urn:ietf:params:scim:schemas:extension:uniFLOWOnline:2.0:User:cardNumber | String |  |  |
    | urn:ietf:params:scim:schemas:extension:uniFLOWOnline:2.0:User:cardRegistrationCode | String |  |  |
    | urn:ietf:params:scim:schemas:extension:uniFLOWOnline:2.0:User:localUsername | String |  |  |
    | urn:ietf:params:scim:schemas:extension:uniFLOWOnline:2.0:User:pin | String |  |  |
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
