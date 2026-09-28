<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/tap-app-security-provisioning-tutorial -->
<!-- Sitemap-Last-Modified: 2026-03-26 -->

# Configure TAP App Security for automatic user provisioning with Microsoft Entra ID

This article describes the steps you need to perform in both TAP App Security and Microsoft Entra ID to configure automatic user provisioning. When configured, Microsoft Entra ID automatically provisions and de-provisions users and groups to [TAP App Security](https://tapappsecurity.com/) using the Microsoft Entra provisioning service. For important details on what this service does, how it works, and frequently asked questions, see [Automate user provisioning and deprovisioning to SaaS applications with Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/user-provisioning).

## Capabilities supported

- Create users in TAP App Security.
- Remove users in TAP App Security when they don't require access anymore.
- Keep user attributes synchronized between Microsoft Entra ID and TAP App Security.
- [Single sign-on](https://learn.microsoft.com/en-us/entra/identity/saas-apps/tap-app-security-tutorial) to TAP App Security.
- Long lived bearer token authentication supported.

## Prerequisites

The scenario outlined in this article assumes that you already have the following prerequisites:

- [A Microsoft Entra tenant](https://learn.microsoft.com/en-us/entra/identity-platform/quickstart-create-new-tenant).
- One of the following roles: [Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#application-administrator), [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator), or [Application Owner](https://learn.microsoft.com/en-us/entra/fundamentals/users-default-permissions#owned-enterprise-applications).
- A user account in TAP App Security with Admin permissions.

## Step 1: Plan your provisioning deployment

1. Learn about [how the provisioning service works](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/user-provisioning).
2. Determine who's in [scope for provisioning](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts).
3. Determine what data to [map between Microsoft Entra ID and TAP App Security](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/customize-application-attributes).

## Step 2: Configure TAP App Security to support provisioning with Microsoft Entra ID

1. Log in to [TAP App Security back-end control panel](https://app.tapappsecurity.com/).
2. Navigate to **Single Sign On > Active Directory**.
3. Select the **Integrate Active Directory app** button. Then enter the domain of your organization and select **Save** button.

   [![Screenshot on how to add domain.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/tap-app-security-provisioning-tutorial/add-domain.png)](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/tap-app-security-provisioning-tutorial/add-domain.png#lightbox)

4. After entering the domain, a new line in the table appears showing domain name and its status as **initialize**. Select the gear icon to reveal technical data about TAP app Security server and to complete initialization.

   [![Screenshot showing initialize.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/tap-app-security-provisioning-tutorial/initialize.png)](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/tap-app-security-provisioning-tutorial/initialize.png#lightbox)

5. Technical data about TAP App Security servers is revealed. You can now copy the **Tenant Url** and **Authorization Token** from this page to be used later on while setting up provisioning in Microsoft Entra ID.

   [![Screenshot showing domain details.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/tap-app-security-provisioning-tutorial/domain-details.png)](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/tap-app-security-provisioning-tutorial/domain-details.png#lightbox)

## Step 3: Add TAP App Security from the Microsoft Entra application gallery

Add TAP App Security from the Microsoft Entra application gallery to start managing provisioning to TAP App Security. If you have previously setup TAP App Security for SSO, you can use the same application. However, we recommend that you create a separate app when testing out the integration initially. Learn more about adding an application from the gallery [here](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/add-application-portal).

## Step 4: Define who is in scope for provisioning

The Microsoft Entra provisioning service allows you to scope who is provisioned based on assignment to the application, or based on attributes of the user or group. If you choose to scope who is provisioned to your app based on assignment, you can use the [steps to assign users and groups to the application](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/assign-user-or-group-access-portal). If you choose to scope who is provisioned based solely on attributes of the user or group, you can [use a scoping filter](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts).

- Start small. Test with a small set of users and groups before rolling out to everyone. When scope for provisioning is set to assigned users and groups, you can control this by assigning one or two users or groups to the app. When scope is set to all users and groups, you can specify an [attribute based scoping filter](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts).
- If you need extra roles, you can [update the application manifest](https://learn.microsoft.com/en-us/entra/identity-platform/howto-add-app-roles-in-apps) to add new roles.

## Step 5: Configure automatic user provisioning to TAP App Security

This section guides you through the steps to configure the Microsoft Entra provisioning service to create, update, and disable users and/or groups in TAP App Security based on user and/or group assignments in Microsoft Entra ID.

### To configure automatic user provisioning for TAP App Security in Microsoft Entra ID:

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps**

   ![Enterprise applications blade](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/enterprise-applications.png)

3. In the applications list, select **TAP App Security**.

   ![The TAP App Security link in the Applications list](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/all-applications.png)

4. Select the **Provisioning** tab.

   ![Provisioning tab](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/provisioning.png)

5. Select **+ New configuration**.

   ![Screenshot of Provisioning tab automatic.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/application-provisioning.png)

6. In the **Tenant URL** field, input your TAP App Security Tenant URL and Secret Token. Select **Test Connection** to ensure Microsoft Entra ID can connect to TAP App Security. If the connection fails, ensure your TAP App Security account has the required admin permissions and try again.

   ![Screenshot of Provisioning test connection.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/provisioning-test-connection.png)

7. Select **Create** to create your configuration.
8. Select **Properties** on the **Overview** page.
9. Select the **Edit** icon to edit the properties. Enable notification emails and provide an email to receive quarantine emails. Enable accidental deletions prevention. Select **Apply** to save the changes.

   ![Screenshot of Provisioning properties.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/provisioning-properties.png)

10. Select **Attribute Mapping** in the left panel and select **users**.
11. Review the user attributes that are synchronized from Microsoft Entra ID to TAP App Security in the **Attribute-Mapping** section. The attributes selected as **Matching** properties are used to match the user accounts in TAP App Security for update operations. If you choose to change the [matching target attribute](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/customize-application-attributes), you need to ensure that the TAP App Security API supports filtering users based on that attribute. Select the **Save** button to commit any changes.
    | Attribute | Type | Supported for filtering | Required by TAP App Security |
    | --- | --- | --- | --- |
    | userName | String | ✓ | ✓ |
    | active | Boolean |  | ✓ |
    | phoneNumbers\[type eq "mobile"\].value | String |  |  |
    | displayName | String |  | ✓ |
    | title | String |  | ✓ |
12. To configure scoping filters, refer to the following instructions provided in the [Scoping filter article](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts).
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
