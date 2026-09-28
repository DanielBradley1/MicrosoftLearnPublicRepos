<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/cerby-provisioning-tutorial -->
<!-- Sitemap-Last-Modified: 2026-03-05 -->

# Configure Cerby for automatic user provisioning with Microsoft Entra ID

This article describes the steps you need to do in both Cerby and Microsoft Entra ID to configure automatic user provisioning. When configured, Microsoft Entra ID automatically provisions and de-provisions users and groups to [Cerby](https://app.cerby.com/) using the Microsoft Entra provisioning service. For important details on what this service does, how it works, and frequently asked questions, see [Automate user provisioning and deprovisioning to SaaS applications with Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/user-provisioning).

## Capabilities supported

- Create users in Cerby
- Remove users in Cerby when they don't require access anymore
- Keep user attributes synchronized between Microsoft Entra ID and Cerby
- Provision groups and group memberships in Cerby.
- [Single sign-on](https://learn.microsoft.com/en-us/entra/identity/saas-apps/cerby-tutorial) to Cerby \(recommended\).

## Prerequisites

The scenario outlined in this article assumes that you already have the following prerequisites:

- [A Microsoft Entra tenant](https://learn.microsoft.com/en-us/entra/identity-platform/quickstart-create-new-tenant)
- One of the following roles: [Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#application-administrator), [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator), or [Application Owner](https://learn.microsoft.com/en-us/entra/fundamentals/users-default-permissions#owned-enterprise-applications).
- A user account in Cerby with the Workspace Owner role.
- The Cerby SAML2-based integration must be set up. Follow the instructions in the [How to Configure the Cerby App Gallery SAML App with Your Microsoft Entra tenant](https://help.cerby.com/en/articles/5457563-how-to-configure-the-cerby-app-gallery-saml-app-with-your-azure-ad-tenant) article to set up the integration.

## Step 1: Plan your provisioning deployment

1. Learn about [how the provisioning service works](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/user-provisioning).
2. Determine who's in [scope for provisioning](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts).
3. Determine what data to [map between Microsoft Entra ID and Cerby](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/customize-application-attributes).

## Step 2: Configure Cerby to support provisioning with Microsoft Entra ID

Cerby has enabled by default the provisioning support for Microsoft Entra ID. You must only retrieve the SCIM API authentication token by completing the following steps:

1. Log in to your corresponding [Cerby workspace](https://app.cerby.com/).
2. Select the **Hi there < user >!** button located at the bottom of the left side navigation menu. A drop-down menu is displayed.
3. Select the **Workspace Configuration** option related to your account from the drop-down menu. The **Workspace Configuration** page is displayed.
4. Activate the **IDP Settings** tab.
5. Select the **View Token** button located in the **Directory Sync** section of the **IDP Settings** tab. A pop-up window is displayed waiting to confirm your identity, and a push notification is sent to your Cerby mobile application. **IMPORTANT:** To confirm your identity, you must have installed and logged in to the Cerby mobile application to receive push notifications.
6. Select the **It's me!** button in the **Confirmation Request** screen of your Cerby mobile application to confirm your identity. The pop-up window in your Cerby workspace is closed, and the **Show Token** pop-up window is displayed.
7. Select the **Copy** button to copy the SCIM token to the clipboard.

   Tip

   Keep the **Show Token** pop-up window open to copy the token at any time. You need the token to configure provisioning with Microsoft Entra ID.

## Step 3: Add Cerby from the Microsoft Entra application gallery

Add Cerby from the Microsoft Entra application gallery to start managing provisioning to Cerby. If you have previously setup Cerby for SSO, you can use the same application. However it's recommended you create a separate app when testing out the integration initially. Learn more about adding an application from the gallery [here](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/add-application-portal).

## Step 4: Define who is in scope for provisioning

The Microsoft Entra provisioning service allows you to scope who is provisioned based on assignment to the application, or based on attributes of the user or group. If you choose to scope who is provisioned to your app based on assignment, you can use the [steps to assign users and groups to the application](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/assign-user-or-group-access-portal). If you choose to scope who is provisioned based solely on attributes of the user or group, you can [use a scoping filter](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts).

- Start small. Test with a small set of users and groups before rolling out to everyone. When scope for provisioning is set to assigned users and groups, you can control this by assigning one or two users or groups to the app. When scope is set to all users and groups, you can specify an [attribute based scoping filter](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts).
- If you need extra roles, you can [update the application manifest](https://learn.microsoft.com/en-us/entra/identity-platform/howto-add-app-roles-in-apps) to add new roles.

## Step 5: Configure automatic user provisioning to Cerby

This section guides you through the steps to configure the Microsoft Entra provisioning service to create, update, and disable users and groups in Cerby based on user and group assignments in Microsoft Entra ID.

### To configure automatic user provisioning for Cerby in Microsoft Entra ID:

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps**

   ![Enterprise applications blade](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/enterprise-applications.png)

3. In the applications list, select **Cerby**.

   ![The Cerby link in the Applications list](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/all-applications.png)

4. Select the **Provisioning** tab.

   ![Provisioning tab](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/provisioning.png)

5. Set **+ New configuration**.

   ![Screenshot of Provisioning tab automatic.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/application-provisioning.png)

6. In the **Tenant URL** field, input your Cerby Tenant URL and Secret Token. Select **Test Connection** to ensure Microsoft Entra ID can connect to Cerby. If the connection fails, ensure your Cerby account has the required admin permissions and try again.

   ![Screenshot of Provisioning test connection.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/provisioning-test-connection.png)

7. Select **Create** to create your configuration.
8. Select **Properties** in the **Overview** page.
9. Select the pencil to edit the properties. Enable notification emails and provide an email to receive quarantine emails. Enable accidental deletions prevention. Select **Apply** to save the changes.

   ![Screenshot of Provisioning properties.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/provisioning-properties.png)

10. Select **Attribute Mapping** in the left panel and select **users**.
11. Review the user attributes that are synchronized from Microsoft Entra ID to Cerby in the **Attribute Mappings** section. The attributes selected as **Matching** properties are used to match the user accounts in Cerby for update operations. If you choose to change the [matching target attribute](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/customize-application-attributes), you need to ensure that the Cerby API supports filtering users based on that attribute. Select the **Save** button to commit any changes.
    | Attribute | Type | Supported for filtering | Required by Cerby |
    | --- | --- | --- | --- |
    | userName | String | ✓ | ✓ |
    | emails\[type eq "work"\].value | String | ✓ | ✓ |
    | active | Boolean |  | ✓ |
    | name.givenName | String |  | ✓ |
    | name.familyName | String |  | ✓ |
    | externalId | String |  |  |
12. Select **Groups**.
13. Review the group attributes that are synchronized from Microsoft Entra ID to Cerby in the **Attribute-Mapping** section. The attributes selected as **Matching** properties are used to match the groups in Cerby for update operations. Select the **Save** button to commit any changes.
    | Attribute | Type | Supported for filtering | Required by Cerby |
    | --- | --- | --- | --- |
    | displayName | String | ✓ | ✓ |
    | externalId | String |  |  |
    | members | Reference |  |  |
14. To configure scoping filters, refer to the following instructions provided in the [Scoping filter article](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts).
15. Use [on-demand provisioning](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/provision-on-demand) to validate sync with a small number of users before deploying more broadly in your organization.
16. When you're ready to provision, select **Start Provisioning** from the **Overview** page.

## Step 6: Monitor your deployment

Once you configure provisioning, use the following resources to monitor your deployment:

1. Use the [provisioning logs](https://learn.microsoft.com/en-us/entra/identity/monitoring-health/concept-provisioning-logs) to determine which users are provisioned successfully or unsuccessfully
2. Check the [progress bar](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/application-provisioning-when-will-provisioning-finish-specific-user) to see the status of the provisioning cycle and how close it's to completion
3. If the provisioning configuration seems to be in an unhealthy state, the application goes into quarantine. Learn more about quarantine states the [application provisioning quarantine status](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/application-provisioning-quarantine-status) article.

## Troubleshooting Tips

If you need to regenerate the SCIM API authentication token, complete the following steps:

1. Send an email with your request to [Cerby Support Team](mailto:support@cerby.com). The Cerby team regenerates the SCIM API authentication token.
2. Receive the response email from Cerby to confirm that the token was successfully regenerated.
3. Complete the instructions from the [How to Retrieve the SCIM API Authentication Token from Cerby](https://help.cerby.com/en/articles/5638472-how-to-configure-automatic-user-provisioning-for-azure-ad) article to retrieve the new token.

   Note

   The Cerby team is currently developing a self-service solution for regenerating the SCIM API authentication token. To regenerate the token, the Cerby team members must validate their identity.

## Change log

- 01/02/2024 - Added support for **Group Provisioning**.

## More resources

- [Managing user account provisioning for Enterprise Apps](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/configure-automatic-user-provisioning-portal)
- [What is application access and single sign-on with Microsoft Entra ID?](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/what-is-single-sign-on)

## Related content

- [Learn how to review logs and get reports on provisioning activity](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/check-status-user-account-provisioning)
