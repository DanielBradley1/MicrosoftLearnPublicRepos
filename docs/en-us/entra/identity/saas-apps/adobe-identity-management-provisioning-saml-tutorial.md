<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/adobe-identity-management-provisioning-saml-tutorial -->
<!-- Sitemap-Last-Modified: 2026-05-26 -->

# Configure Adobe Identity Management \(SAML\) for automatic user provisioning with Microsoft Entra ID

This article describes the steps you need to perform in both Adobe Identity Management \(SAML\) and Microsoft Entra ID to configure automatic user provisioning. When configured, Microsoft Entra ID automatically provisions and de-provisions users and groups to Adobe Identity Management \(SAML\) using the Microsoft Entra provisioning service. For important details on what this service does, how it works, and frequently asked questions, see [Automate user provisioning and deprovisioning to SaaS applications with Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/user-provisioning).

## Capabilities supported

- Create users in Adobe Identity Management \(SAML\).
- Remove users in Adobe Identity Management \(SAML\) when they don't require access anymore.
- Keep user attributes synchronized between Microsoft Entra ID and Adobe Identity Management \(SAML\).
- Provision groups and group memberships in Adobe Identity Management \(SAML\).
- [Single sign-on](https://learn.microsoft.com/en-us/entra/identity/saas-apps/adobe-identity-management-tutorial) to Adobe Identity Management \(SAML\) \(recommended\).

Adobe Identity Management \(SAML\) is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government | China operated by 21Vianet |
| :---: | :---: | :---: |
| ✅ | ✅ |  |

## Prerequisites

The scenario outlined in this article assumes that you already have the following prerequisites:

- [A Microsoft Entra tenant](https://learn.microsoft.com/en-us/entra/identity-platform/quickstart-create-new-tenant).
- One of the following roles: [Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#application-administrator), [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator), or [Application Owner](https://learn.microsoft.com/en-us/entra/fundamentals/users-default-permissions#owned-enterprise-applications).
- A federated directory in the [Adobe Admin Console](https://adminconsole.adobe.com/) with verified domains.
- Review the [Adobe documentation](https://helpx.adobe.com/enterprise/using/add-azure-sync.html#add-sync) on user provisioning

Note

If your organization uses the User Sync Tool or a UMAPI integration, you must first pause the integration. Then, add Microsoft Entra automatic provisioning to automate user management. Once Microsoft Entra automatic provisioning is configured and running, you can completely remove the User Sync Tool or UMAPI integration.

## Step 1: Plan your provisioning deployment

1. Learn about [how the provisioning service works](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/user-provisioning).
2. Determine who is in [scope for provisioning](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts).
3. Determine what data to [map between Microsoft Entra ID and Adobe Identity Management \(SAML\)](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/customize-application-attributes).

## Step 2: Configure Adobe Identity Management \(SAML\) to support provisioning with Microsoft Entra ID

1. Log in to [Adobe Admin Console](https://adminconsole.adobe.com/). Navigate to **Settings > Directory Details > Sync**.
2. Select **Add Sync**.

   ![Screenshot shows to add.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/adobe-identity-management-provisioning-saml-tutorial/add-sync.png "Add")

3. Select **Sync users from Microsoft Azure** and select **Next**.

   ![Screenshot that shows 'Sync users from Microsoft Entra ID' selected.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/adobe-identity-management-provisioning-saml-tutorial/sync-users.png)

4. Copy and save the **Tenant URL** and the **Secret token**. These values are entered in the **Tenant URL** and **Secret Token** fields in the Provisioning tab of your Adobe Identity Management \(SAML\) application.

   ![Screenshot shows to sync.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/adobe-identity-management-provisioning-saml-tutorial/token.png "Sync")

## Step 3: Add Adobe Identity Management \(SAML\) from the Microsoft Entra application gallery

Add Adobe Identity Management \(SAML\) from the Microsoft Entra application gallery to start managing provisioning to Adobe Identity Management \(SAML\). If you have previously setup Adobe Identity Management \(SAML\) for SSO, you can use the same application. However it's recommended that you create a separate app when testing out the integration initially. Learn more about adding an application from the gallery [here](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/add-application-portal).

## Step 4: Define who is in scope for provisioning

The Microsoft Entra provisioning service allows you to scope who is provisioned based on assignment to the application, or based on attributes of the user or group. If you choose to scope who is provisioned to your app based on assignment, you can use the [steps to assign users and groups to the application](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/assign-user-or-group-access-portal). If you choose to scope who is provisioned based solely on attributes of the user or group, you can [use a scoping filter](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts).

- Start small. Test with a small set of users and groups before rolling out to everyone. When scope for provisioning is set to assigned users and groups, you can control this by assigning one or two users or groups to the app. When scope is set to all users and groups, you can specify an [attribute based scoping filter](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts).
- If you need extra roles, you can [update the application manifest](https://learn.microsoft.com/en-us/entra/identity-platform/howto-add-app-roles-in-apps) to add new roles.

## Step 5: Configure automatic user provisioning to Adobe Identity Management \(SAML\)

This section guides you through the steps to configure the Microsoft Entra provisioning service to create, update, and disable users and/or groups in TestApp based on user and/or group assignments in Microsoft Entra ID.

<iframe src="https://www.youtube-nocookie.com/embed/k2_fk7BY8Ow" allowfullscreen="true" data-linktype="external" frameborder="0"></iframe>

### To configure automatic user provisioning for Adobe Identity Management \(SAML\) in Microsoft Entra ID:

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps**

   ![Screenshot shows the enterprise applications blade.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/enterprise-applications.png "Enterprise application")

3. In the applications list, select **Adobe Identity Management \(SAML\)**.

   ![Screenshot shows the Adobe Identity Management \(SAML\) link in the Applications list.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/all-applications.png "Application List")

4. Select the **Provisioning** tab.

   ![Screenshot shows the provisioning tab.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/provisioning.png "Tab")

5. Set **+ New configuration**.

   ![Screenshot of Provisioning tab automatic.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/application-provisioning.png)

6. In the **Tenant URL** field, input your Adobe Identity Management \(SAML\) Tenant URL and Secret Token. Select **Test Connection** to ensure Microsoft Entra ID can connect to Adobe Identity Management \(SAML\). If the connection fails, ensure your Adobe Identity Management \(SAML\) account has the required admin permissions and try again.

   ![Screenshot of Provisioning test connection.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/provisioning-test-connection.png)

7. Select **Create** to create your configuration.
8. Select **Properties** in the **Overview** page.
9. Select the pencil to edit the properties. Enable notification emails and provide an email to receive quarantine emails. Enable accidental deletions prevention. Select **Apply** to save the changes.

   ![Screenshot of Provisioning properties.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/provisioning-properties.png)

10. Select **Attribute Mapping** in the left panel and select **users**.
11. Review the user attributes that are synchronized from Microsoft Entra ID to Adobe Identity Management \(SAML\) in the **Attribute-Mapping** section. The attributes selected as **Matching** properties are used to match the user accounts in Adobe Identity Management \(SAML\) for update operations. If you choose to change the [matching target attribute](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/customize-application-attributes), you need to ensure that the Adobe Identity Management \(SAML\) API supports filtering users based on that attribute. Select the **Save** button to commit any changes.
    | Attribute | Type | Supported for filtering | Required by Adobe Identity Management \(SAML\) |
    | --- | --- | --- | --- |
    | userName | String | ✓ | ✓ |
    | active | Boolean |  |  |
    | emails\[type eq "work"\].value | String |  |  |
    | addresses\[type eq "work"\].country | String |  |  |
    | name.givenName | String |  |  |
    | name.familyName | String |  |  |
    | urn:ietf:params:scim:schemas:extension:Adobe:2.0:User:emailAliases | String |  |  |
    | urn:ietf:params:scim:schemas:extension:Adobe:2.0:User:eduRole | String |  |  |


    Note


    The **eduRole** field accepts values like `Teacher or Student`, anything else is ignored.

12. Select **Groups**.
13. Review the group attributes that are synchronized from Microsoft Entra ID to Adobe Identity Management \(SAML\) in the **Attribute-Mapping** section. The attributes selected as **Matching** properties are used to match the groups in Adobe Identity Management \(SAML\) for update operations. Select the **Save** button to commit any changes.
    | Attribute | Type | Supported for filtering | Required by Adobe Identity Management \(SAML\) |
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

## Change log

- 07/18/2023 - The app was added to Gov Cloud.
- 08/15/2023 - Added support for Schema Discovery.

## More resources

- [Managing user account provisioning for Enterprise Apps](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/configure-automatic-user-provisioning-portal)
- [What is application access and single sign-on with Microsoft Entra ID?](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/what-is-single-sign-on)

## Related content

- [Learn how to review logs and get reports on provisioning activity](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/check-status-user-account-provisioning)
