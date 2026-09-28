<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/browserstack-single-sign-on-provisioning-tutorial -->
<!-- Sitemap-Last-Modified: 2026-03-05 -->

# Configure BrowserStack Single Sign-on for automatic user provisioning with Microsoft Entra ID

This article describes the steps you need to perform in both BrowserStack Single Sign-on and Microsoft Entra ID to configure automatic user provisioning. When configured, Microsoft Entra ID automatically provisions and de-provisions users to [BrowserStack Single Sign-on](https://www.browserstack.com) using the Microsoft Entra provisioning service. For important details on what this service does, how it works, and frequently asked questions, see [Automate user provisioning and deprovisioning to SaaS applications with Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/user-provisioning).

## Capabilities supported

- Create users in BrowserStack Single Sign-on
- Remove users in BrowserStack Single Sign-on when they don't require access anymore
- Keep user attributes synchronized between Microsoft Entra ID and BrowserStack Single Sign-on
- [Single sign-on](https://learn.microsoft.com/en-us/entra/identity/saas-apps/browserstack-single-sign-on-tutorial) to BrowserStack Single Sign-on \(recommended\)
- Long lived bearer token authentication supported.

## Prerequisites

The scenario outlined in this article assumes that you already have the following prerequisites:

- A Microsoft Entra user account with an active subscription. If you don't already have one, you can [Create an account for free](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
- One of the following roles:

  - [Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#application-administrator)
  - [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator)
  - [Application Owner](https://learn.microsoft.com/en-us/entra/fundamentals/users-default-permissions#owned-enterprise-applications).

- A user account in BrowserStack with **Owner** permissions.
- An [Enterprise plan](https://www.browserstack.com/pricing) with BrowserStack.
- [Single Sign-on](https://www.browserstack.com/docs/enterprise/single-sign-on/azure-ad) integration with BrowserStack \(mandatory\).

## Step 1: Plan your provisioning deployment

1. Learn about [how the provisioning service works](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/user-provisioning).
2. Determine who's in [scope for provisioning](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts).
3. Determine what data to [map between Microsoft Entra ID and BrowserStack Single Sign-on](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/customize-application-attributes).

## Step 2: Configure BrowserStack Single Sign-on to support provisioning with Microsoft Entra ID

1. Log in to [BrowserStack](https://www.browserstack.com/users/sign_in) as a user with **Owner** permissions.
2. Navigate to **Account** > **Settings & Permissions**. Select the **Security** tab.
3. Under **Auto User Provisioning**, select **Configure**.

   ![Settings](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/browserstack-single-sign-on-provisioning-tutorial/configure.png)

4. Select the user attributes that you want to control via Microsoft Entra ID and select **Confirm**.

   ![User](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/browserstack-single-sign-on-provisioning-tutorial/attributes.png)

5. Copy the **Tenant URL** and **Secret Token**. These values are entered in the Tenant URL and Secret Token fields in the Provisioning tab of your BrowserStack Single Sign-on application. Select **Done**.

   ![Authorization](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/browserstack-single-sign-on-provisioning-tutorial/credential.png)

6. Your provisioning configuration has been saved on BrowserStack. **Enable** user provisioning in BrowserStack once **the provisioning setup on Microsoft Entra ID** is completed, to prevent blocking of inviting new users from BrowserStack [Account](https://www.browserstack.com/accounts/manage-users).

   ![Account](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/browserstack-single-sign-on-provisioning-tutorial/enable.png)

## Step 3: Add BrowserStack Single Sign-on from the Microsoft Entra application gallery

Add BrowserStack Single Sign-on from the Microsoft Entra application gallery to start managing provisioning to BrowserStack Single Sign-on. If you have previously setup BrowserStack Single Sign-on for SSO, you can use the same application. However, we recommend that you create a separate app when testing out the integration initially. Learn more about adding an application from the gallery [here](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/add-application-portal).

## Step 4: Define who is in scope for provisioning

The Microsoft Entra provisioning service allows you to scope who is provisioned based on assignment to the application, or based on attributes of the user or group. If you choose to scope who is provisioned to your app based on assignment, you can use the [steps to assign users and groups to the application](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/assign-user-or-group-access-portal). If you choose to scope who is provisioned based solely on attributes of the user or group, you can [use a scoping filter](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts).

- Start small. Test with a small set of users and groups before rolling out to everyone. When scope for provisioning is set to assigned users and groups, you can control this by assigning one or two users or groups to the app. When scope is set to all users and groups, you can specify an [attribute based scoping filter](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts).
- If you need extra roles, you can [update the application manifest](https://learn.microsoft.com/en-us/entra/identity-platform/howto-add-app-roles-in-apps) to add new roles.

## Step 5: Configure automatic user provisioning to BrowserStack Single Sign-on

This section guides you through the steps to configure the Microsoft Entra provisioning service to create, update, and disable users in app based on user assignments in Microsoft Entra ID.

### To configure automatic user provisioning for BrowserStack Single Sign-on in Microsoft Entra ID:

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps**

   ![Enterprise applications blade](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/enterprise-applications.png)

3. In the applications list, select **BrowserStack Single Sign-on**.

   ![The BrowserStack Single Sign-on link in the Applications list](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/all-applications.png)

4. Select the **Provisioning** tab.

   ![Provisioning tab](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/provisioning.png)

5. Set **+ New configuration**.

   ![Screenshot of Provisioning tab automatic.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/application-provisioning.png)

6. In the **Tenant URL** field, input your BrowserStack Single Sign-on Tenant URL and Secret Token. Select **Test Connection** to ensure Microsoft Entra ID can connect to BrowserStack Single Sign-on. If the connection fails, ensure your BrowserStack Single Sign-on account has the required admin permissions and try again.

   ![Screenshot of Provisioning test connection.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/provisioning-test-connection.png)

7. Select **Create** to create your configuration.
8. Select **Properties** in the **Overview** page.
9. Select the pencil to edit the properties. Enable notification emails and provide an email to receive quarantine emails. Enable accidental deletions prevention. Select **Apply** to save the changes.

   ![Screenshot of Provisioning properties.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/provisioning-properties.png)

10. Select **Attribute Mapping** in the left panel and select **users**.
11. Review the user attributes that are synchronized from Microsoft Entra ID to BrowserStack Single Sign-on in the **Attribute-Mapping** section. The attributes selected as **Matching** properties are used to match the user accounts in BrowserStack Single Sign-on for update operations. If you choose to change the [matching target attribute](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/customize-application-attributes), you need to ensure that the BrowserStack Single Sign-on API supports filtering users based on that attribute. Select the **Save** button to commit any changes.
    | Attribute | Type | Supported for Filtering |
    | --- | --- | --- |
    | userName | String | ✓ |
    | name.givenName | String |  |
    | name.familyName | String |  |
    | urn:ietf:params:scim:schemas:extension:Bstack:2.0:User:bstack\_role | String |  |
    | urn:ietf:params:scim:schemas:extension:Bstack:2.0:User:bstack\_team | String |  |
    | urn:ietf:params:scim:schemas:extension:Bstack:2.0:User:bstack\_product | String |  |
12. To configure scoping filters, refer to the following instructions provided in the [Scoping filter article](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts).
13. Use [on-demand provisioning](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/provision-on-demand) to validate sync with a small number of users before deploying more broadly in your organization.
14. When you're ready to provision, select **Start Provisioning** from the **Overview** page.

## Step 6: Monitor your deployment

Once you configure provisioning, use the following resources to monitor your deployment:

1. Use the [provisioning logs](https://learn.microsoft.com/en-us/entra/identity/monitoring-health/concept-provisioning-logs) to determine which users are provisioned successfully or unsuccessfully
2. Check the [progress bar](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/application-provisioning-when-will-provisioning-finish-specific-user) to see the status of the provisioning cycle and how close it's to completion
3. If the provisioning configuration seems to be in an unhealthy state, the application goes into quarantine. Learn more about quarantine states the [application provisioning quarantine status](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/application-provisioning-quarantine-status) article.

## Connector limitations

- BrowserStack Single Sign-on doesn't support group provisioning.
- BrowserStack Single Sign-on requires **emails\[type eq "work"\].value** and **userName** to have the same source value.

## Troubleshooting tips

- Refer to troubleshooting tips [here](https://www.browserstack.com/docs/enterprise/auto-user-provisioning/azure-ad#troubleshooting).

## Additional resources

- [Managing user account provisioning for Enterprise Apps](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/configure-automatic-user-provisioning-portal)
- [What is application access and single sign-on with Microsoft Entra ID?](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/what-is-single-sign-on)
- [Configuring attribute-mappings in BrowserStack Single Sign-on](https://www.browserstack.com/docs/enterprise/auto-user-provisioning/azure-ad)
- [Setup and enable auto user provisioning in BrowserStack](https://www.browserstack.com/docs/enterprise/auto-user-provisioning/azure-ad#setup-and-enable-auto-user-provisioning)

## Related content

- [Learn how to review logs and get reports on provisioning activity](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/check-status-user-account-provisioning)
