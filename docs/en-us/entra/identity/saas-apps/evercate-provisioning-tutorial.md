<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/evercate-provisioning-tutorial -->
<!-- Sitemap-Last-Modified: 2026-03-12 -->

# Configure Evercate for automatic user provisioning with Microsoft Entra ID

This article describes the steps you need to do in both Evercate and Microsoft Entra ID to configure automatic user provisioning. When configured, Microsoft Entra ID automatically provisions and de-provisions users and groups to [Evercate](https://evercate.com) using the Microsoft Entra provisioning service. For important details on what this service does, how it works, and frequently asked questions, see [Automate user provisioning and deprovisioning to SaaS applications with Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/user-provisioning).

## Capabilities Supported

- Create users in Evercate.
- Remove users in Evercate when they don't require access anymore.
- Keep user attributes synchronized between Microsoft Entra ID and Evercate.
- Provision groups and group memberships in Evercate.
- [Single sign-on](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/add-application-portal-setup-oidc-sso) to Evercate \(recommended\).

## Prerequisites

The scenario outlined in this article assumes that you already have the following prerequisites:

- [A Microsoft Entra tenant](https://learn.microsoft.com/en-us/entra/identity-platform/quickstart-create-new-tenant).
- One of the following roles: [Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#application-administrator), [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator), or [Application Owner](https://learn.microsoft.com/en-us/entra/fundamentals/users-default-permissions#owned-enterprise-applications).
- A user account in Evercate with Admin permissions.

## Step 1: Plan your provisioning deployment

1. Learn about [how the provisioning service works](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/user-provisioning).
2. Determine who's in [scope for provisioning](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts).
3. Determine what data to [map between Microsoft Entra ID and Evercate](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/customize-application-attributes).

## Step 2: Configure Evercate to support provisioning with Microsoft Entra ID

1. Log in to Evercate as an administrator and select **Settings** in the top menu.
2. Under Settings, navigate to **Advanced -> Connect Microsoft Entra ID**.
3. Select the button "**I understand, connect Microsoft Entra ID**" to start the process. [![connect Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/evercate-provisioning-tutorial/connect-azure-ad-page.png)](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/evercate-provisioning-tutorial/connect-azure-ad-page.png#lightbox)
4. Now you're taken to Microsoft’s Sign in page where you need to sign in as an administrator for your AD.

   The Microsoft user you sign in with must:

   - Be an administrator with permissions to “Enterprise Applications”.
   - Be an AD user and not a personal account.


   [![Sign in](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/evercate-provisioning-tutorial/sign-in-page.png)](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/evercate-provisioning-tutorial/sign-in-page.png#lightbox)

5. Tick the "**Consent on behalf of your organization**" before selecting accept. [![Provide consent](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/evercate-provisioning-tutorial/consent-page.png)](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/evercate-provisioning-tutorial/consent-page.png#lightbox)

   Note

   If you missed ticking the consent checkbox, every user gets a similar dialog upon their first sign in. See below under the section “Configuring the application in Azure” on how to give consent for your organization after the connection is made.
6. Once you have successfully set up the connection to Microsoft Entra ID you can configure which AD features you want to enable in Evercate.
7. Navigate to **Settings -> Advanced -> Connect Microsoft Entra ID** you see the token you need to enable provisioning \(enabled from Microsoft Entra ID\) and can tick the box for allowing single sign on for your Evercate account.
8. Copy and save the token. This value is entered in the **Secret Token** \* field in the Provisioning tab of your Evercate application.

## Step 3: Add Evercate from the Microsoft Entra application gallery

Add Evercate from the Microsoft Entra application gallery to start managing provisioning to Evercate. If you have previously setup Evercate for SSO, you can use the same application. Learn more about adding an application from the gallery [here](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/add-application-portal).

## Step 4: Define who is in scope for provisioning

The Microsoft Entra provisioning service allows you to scope who is provisioned based on assignment to the application, or based on attributes of the user or group. If you choose to scope who is provisioned to your app based on assignment, you can use the [steps to assign users and groups to the application](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/assign-user-or-group-access-portal). If you choose to scope who is provisioned based solely on attributes of the user or group, you can [use a scoping filter](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts).

- Start small. Test with a small set of users and groups before rolling out to everyone. When scope for provisioning is set to assigned users and groups, you can control this by assigning one or two users or groups to the app. When scope is set to all users and groups, you can specify an [attribute based scoping filter](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts).
- If you need extra roles, you can [update the application manifest](https://learn.microsoft.com/en-us/entra/identity-platform/howto-add-app-roles-in-apps) to add new roles.

## Step 5: Configure automatic user provisioning to Evercate

This section guides you through the steps to configure the Microsoft Entra provisioning service to create, update, and disable users and groups in Evercate based on user and/or group assignments in Microsoft Entra ID.

### To configure automatic user provisioning for Evercate in Microsoft Entra ID:

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps**

   ![Enterprise applications blade](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/enterprise-applications.png)

3. In the applications list, select **Evercate**.

   ![The Evercate link in the Applications list](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/all-applications.png)

4. Select the **Provisioning** tab.

   ![Provisioning tab](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/provisioning.png)

5. Set **+ New configuration**.

   ![Screenshot of Provisioning tab automatic.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/application-provisioning.png)

6. In the **Tenant URL** field, input your Evercate Tenant URL and Secret Token. Select **Test Connection** to ensure Microsoft Entra ID can connect to Evercate. If the connection fails, ensure your Evercate account has the required admin permissions and try again.

   ![Screenshot of Provisioning test connection.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/provisioning-test-connection.png)

7. Select **Create** to create your configuration.
8. Select **Properties** in the **Overview** page.
9. Select the pencil to edit the properties. Enable notification emails and provide an email to receive quarantine emails. Enable accidental deletions prevention. Select **Apply** to save the changes.

   ![Screenshot of Provisioning properties.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/provisioning-properties.png)

10. Select **Attribute Mapping** in the left panel and select **users**.
11. Review the user attributes that are synchronized from Microsoft Entra ID to Evercate in the **Attribute-Mapping** section. The attributes selected as **Matching** properties are used to match the user accounts in Evercate for update operations. If you choose to change the [matching target attribute](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/customize-application-attributes), you need to ensure that the Evercate API supports filtering users based on that attribute. Select the **Save** button to commit any changes.
    | Attribute | Type | Supported for filtering | Required by Evercate |
    | --- | --- | --- | --- |
    | userName | String | ✓ | ✓ |
    | urn:ietf:params:scim:schemas:extension:enterprise:2.0:User:manager | String |  |  |
    | active | Boolean |  |  |
    | displayName | String |  | ✓ |
    | emails\[type eq "work"\].value | String |  |  |
    | name.givenName | String |  |  |
    | name.familyName | String |  |  |
    | urn:ietf:params:scim:schemas:extension:enterprise:2.0:User:department | String |  |  |
12. Select **Groups**.
13. Review the group attributes that are synchronized from Microsoft Entra ID to Evercate in the **Attribute-Mapping** section. The attributes selected as **Matching** properties are used to match the groups in Evercate for update operations. Select the **Save** button to commit any changes.
    | Attribute | Type | Supported for filtering | Required by Evercate |
    | --- | --- | --- | --- |
    | displayName | String | ✓ | ✓ |
    | members | Reference |  |  |
14. To configure scoping filters, refer to the following instructions provided in the [Scoping filter article](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts).
15. Use [on-demand provisioning](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/provision-on-demand) to validate sync with a small number of users before deploying more broadly in your organization.
16. When you're ready to provision, select **Start Provisioning** from the **Overview** page.

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
