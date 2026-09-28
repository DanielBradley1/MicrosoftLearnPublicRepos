<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/8x8-provisioning-tutorial -->
<!-- Sitemap-Last-Modified: 2026-05-26 -->

# Configure 8x8 for automatic user provisioning with Microsoft Entra ID

This article describes the steps you need to perform in both 8x8 Admin Console and Microsoft Entra ID to configure automatic user provisioning. When configured, Microsoft Entra ID automatically provisions and de-provisions users and groups to [8x8](https://www.8x8.com) using the Microsoft Entra provisioning service. For important details on what this service does, how it works, and frequently asked questions, see [Automate user provisioning and deprovisioning to SaaS applications with Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/user-provisioning).

## Capabilities supported

- Create users in 8x8
- Deactivate users in 8x8 when they don't require access anymore
- Keep user attributes synchronized between Microsoft Entra ID and 8x8
- [Single sign-on](https://learn.microsoft.com/en-us/entra/identity/saas-apps/8x8virtualoffice-tutorial) to 8x8 \(recommended\)
- Long lived bearer token authentication supported.

8x8 is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government | China operated by 21Vianet |
| :---: | :---: | :---: |
| ✅ | ✅ |  |

## Prerequisites

The scenario outlined in this article assumes that you already have the following prerequisites:

- [A Microsoft Entra tenant](https://learn.microsoft.com/en-us/entra/identity-platform/quickstart-create-new-tenant)
- A user account in Microsoft Entra ID with [permission](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference) to configure provisioning \(like [Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#application-administrator), [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator), or [Application Owner](https://learn.microsoft.com/en-us/entra/fundamentals/users-default-permissions#owned-enterprise-applications)\).
- An 8x8 X series subscription of any level.
- An 8x8 user account with administrator permission in [Admin Console](https://vo-cm.8x8.com).
- [Single sign-on with Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/identity/saas-apps/8x8virtualoffice-tutorial) has already been configured.

## Step 1: Plan your provisioning deployment

1. Learn about [how the provisioning service works](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/user-provisioning).
2. Determine who is in [scope for provisioning](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts).
3. Determine what data to [map between Microsoft Entra ID and 8x8](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/customize-application-attributes).

## Step 2: Configure 8x8 to support provisioning with Microsoft Entra ID

This section guides you through the steps to configure 8x8 to support provisioning with Microsoft Entra ID.

### To configure a user provisioning access token in 8x8 Admin Console:

1. Sign in to [Admin Console](https://admin.8x8.com). Select **Identity and Security**.

   [![Screenshot showing the 8x8 Admin Console.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/8x8-provisioning-tutorial/8x8-identity-and-security.png)](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/8x8-provisioning-tutorial/8x8-identity-and-security.png#lightbox)

2. In the **User Provisioning Integration \(SCIM\)** pane, select the toggle to enable and then select **Save**.

   [![Screenshot showing the Identity and Security page of the Admin Console with a callout over the user provisioning integration slider.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/8x8-provisioning-tutorial/8x8-enable-user-provisioning.png)](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/8x8-provisioning-tutorial/8x8-enable-user-provisioning.png#lightbox)

3. Copy the **8x8 URL** and **8x8 API Token** values. These values are entered in the **Tenant URL** and **Secret Token** fields respectively in the Provisioning tab of your 8x8 application.

   [![Screenshot showing the Identity and Security page of the Admin Console with callout over token fields.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/8x8-provisioning-tutorial/8x8-copy-url-token.png)](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/8x8-provisioning-tutorial/8x8-copy-url-token.png#lightbox)

## Step 3: Add 8x8 from the Microsoft Entra application gallery

Add 8x8 from the Microsoft Entra application gallery to start managing provisioning to 8x8. If you have previously setup 8x8 for SSO, you can use the same application. However it's recommended that you create a separate app when testing out the integration initially. Learn more about adding an application from the gallery [here](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/add-application-portal).

## Step 4: Define who is in scope for provisioning

The Microsoft Entra provisioning service allows you to scope who is provisioned based on assignment to the application, or based on attributes of the user or group. If you choose to scope who is provisioned to your app based on assignment, you can use the [steps to assign users and groups to the application](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/assign-user-or-group-access-portal). If you choose to scope who is provisioned based solely on attributes of the user or group, you can [use a scoping filter](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts).

- Start small. Test with a small set of users and groups before rolling out to everyone. When scope for provisioning is set to assigned users and groups, you can control this by assigning one or two users or groups to the app. When scope is set to all users and groups, you can specify an [attribute based scoping filter](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts).
- If you need extra roles, you can [update the application manifest](https://learn.microsoft.com/en-us/entra/identity-platform/howto-add-app-roles-in-apps) to add new roles.

## Step 5: Configure automatic user provisioning to 8x8

This section guides you through the steps to configure the Microsoft Entra provisioning service to create, update, and disable users and/or groups in 8x8 based on user and/or group assignments in Microsoft Entra ID.

### To configure automatic user provisioning for 8x8 in Microsoft Entra ID:

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps**

   ![Screenshot of Enterprise applications blade.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/enterprise-applications.png)

3. In the applications list, select **8x8**.

   ![Screenshot showing the 8x8 link in the Applications list](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/all-applications.png)

4. Select the **Provisioning** tab.

   ![Screenshot of Provisioning tab.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/provisioning.png)

5. Set **+ New configuration**.

   ![Screenshot of Provisioning tab automatic.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/application-provisioning.png)

6. In the **Tenant URL** field, input your 8x8 Tenant URL and Secret Token. Select **Test Connection** to ensure Microsoft Entra ID can connect to 8x8. If the connection fails, ensure your 8x8 account has the required admin permissions and try again.

   ![Screenshot of Provisioning test connection.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/provisioning-test-connection.png)

7. Select **Create** to create your configuration.
8. Select **Properties** in the **Overview** page.
9. Select the pencil to edit the properties. Enable notification emails and provide an email to receive quarantine emails. Enable accidental deletions prevention. Select **Apply** to save the changes.

   ![Screenshot of Provisioning properties.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/provisioning-properties.png)

10. Select **Attribute Mapping** in the left panel and select **users**.
11. Review the user attributes that are synchronized from Microsoft Entra ID to 8x8 in the **Attribute-Mapping** section. The attributes selected as **Matching** properties are used to match the user accounts in 8x8 for update operations. If you choose to change the [matching target attribute](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/customize-application-attributes), you need to ensure that the 8x8 API supports filtering users based on that attribute. Select the **Save** button to commit any changes.
    | Attribute | Type | Notes |
    | --- | --- | --- |
    | userName | String | Sets both Username and Federation ID |
    | externalId | String |  |
    | active | Boolean |  |
    | title | String |  |
    | emails\[type eq "work"\].value | String |  |
    | name.givenName | String |  |
    | name.familyName | String |  |
    | phoneNumbers\[type eq "mobile"\].value | String | Personal Contact Number |
    | phoneNumbers\[type eq "work"\].value | String | Personal Contact Number |
    | urn:ietf:params:scim:schemas:extension:enterprise:2.0:User:department | String |  |
    | urn:ietf:params:scim:schemas:extension:8x8:1.1:User:site | String | Can't be updated after user creation |
    | locale | String | Not mapped by default |
    | timezone | String | Not mapped by default |
12. To configure scoping filters, refer to the following instructions provided in the [Scoping filter article](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts) article.
13. Use [on-demand provisioning](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/provision-on-demand) to validate sync with a small number of users before deploying more broadly in your organization.
14. When you're ready to provision, select **Start Provisioning** from the **Overview** page.

## Step 6: Monitor your deployment

Once you configure provisioning, use the following resources to monitor your deployment:

1. Use the [provisioning logs](https://learn.microsoft.com/en-us/entra/identity/monitoring-health/concept-provisioning-logs) to determine which users are provisioned successfully or unsuccessfully
2. Check the [progress bar](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/application-provisioning-when-will-provisioning-finish-specific-user) to see the status of the provisioning cycle and how close it's to completion
3. If the provisioning configuration seems to be in an unhealthy state, the application goes into quarantine. Learn more about quarantine states the [application provisioning quarantine status](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/application-provisioning-quarantine-status) article.

## Additional resources

- [Managing user account provisioning for Enterprise Apps](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/configure-automatic-user-provisioning-portal)
- [What is application access and Single sign-on with Microsoft Entra ID?](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/what-is-single-sign-on)

## Related content

- [Learn how to review logs and get reports on provisioning activity](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/check-status-user-account-provisioning)
