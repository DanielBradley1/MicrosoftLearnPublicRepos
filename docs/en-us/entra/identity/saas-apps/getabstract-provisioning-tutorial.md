<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/getabstract-provisioning-tutorial -->
<!-- Sitemap-Last-Modified: 2026-03-12 -->

# Configure getAbstract for automatic user provisioning with Microsoft Entra ID

This article describes the steps you need to perform in both getAbstract and Microsoft Entra ID to configure automatic user provisioning. When configured, Microsoft Entra ID automatically provisions and deprovisions users and groups to [getAbstract](https://www.getabstract.com) by using the Microsoft Entra provisioning service. For important details on what this service does, how it works, and frequently asked questions, see [Automate user provisioning and deprovisioning to software as a service \(SaaS\) applications with Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/user-provisioning).

## Capabilities supported

- Create users in getAbstract.
- Remove users in getAbstract when they don't require access anymore.
- Keep user attributes synchronized between Microsoft Entra ID and getAbstract.
- Provision groups and group memberships in getAbstract.
- Enable [single sign-on \(SSO\)](https://learn.microsoft.com/en-us/entra/identity/saas-apps/getabstract-tutorial) to getAbstract \(recommended\).
- Long lived bearer token authentication supported.

## Prerequisites

The scenario outlined in this article assumes that you already have the following prerequisites:

- [A Microsoft Entra tenant](https://learn.microsoft.com/en-us/entra/identity-platform/quickstart-create-new-tenant).
- One of the following roles: [Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#application-administrator), [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator), or [Application Owner](https://learn.microsoft.com/en-us/entra/fundamentals/users-default-permissions#owned-enterprise-applications).
- A getAbstract tenant \(getAbstract corporate license\).
- SSO enabled on Microsoft Entra tenant and getAbstract tenant.
- Approval and System for Cross-domain Identity Management \(SCIM\) enabling for getAbstract. \(Send email to b2b.itsupport@getabstract.com.\)

## Step 1: Plan your provisioning deployment

1. Learn about [how the provisioning service works](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/user-provisioning).
2. Determine who's in [scope for provisioning](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts).
3. Determine what data to [map between Microsoft Entra ID and getAbstract](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/customize-application-attributes).

## Step 2: Configure getAbstract to support provisioning with Microsoft Entra ID

1. Sign in to getAbstract.
2. Select the person icon located in the upper-right corner, and select the **My Central Admin** option.

   ![Screenshot that shows the getAbstract My Central Admin.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/getabstract-provisioning-tutorial/my-account.png)

3. At the left side menu, select **User Management** and select the **configure scim** button.

   ![Screenshot that shows the getAbstract SCIM Admin.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/getabstract-provisioning-tutorial/scim-admin.png)

4. Select **Go**.

   ![Screenshot that shows the getAbstract SCIM Client Id.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/getabstract-provisioning-tutorial/scim-client-go.png)

5. Select the **Generate new token** button.

   ![Screenshot that shows the getAbstract SCIM Token 1.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/getabstract-provisioning-tutorial/scim-generate-token-step-2.png)

6. If you're sure, then select **Generate new token** button. Otherwise, select **Cancel**.

   ![Screenshot that shows the getAbstract SCIM Token 2.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/getabstract-provisioning-tutorial/scim-generate-token-step-1.png)

7. Lastly, you can either select the copy-to-clipboard icon or select the whole token and copy it. Also make a note that the Tenant/Base URL is `https://www.getabstract.com/api/scim/v2`. These values are entered in the **Secret Token** and **Tenant URL** boxes on the **Provisioning** tab of your getAbstract application.

   ![Screenshot that shows the getAbstract SCIM Token 3.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/getabstract-provisioning-tutorial/scim-generate-token-step-3.png)

## Step 3: Add getAbstract from the Microsoft Entra application gallery

Add getAbstract from the Microsoft Entra application gallery to start managing provisioning to getAbstract. If you've previously set up getAbstract for SSO, you can use the same application. We recommended that you create a separate app when testing out the integration initially. Learn more about adding an application from the gallery, see [this quickstart](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/add-application-portal).

## Step 4: Define who is in scope for provisioning

The Microsoft Entra provisioning service allows you to scope who is provisioned based on assignment to the application, or based on attributes of the user or group. If you choose to scope who is provisioned to your app based on assignment, you can use the [steps to assign users and groups to the application](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/assign-user-or-group-access-portal). If you choose to scope who is provisioned based solely on attributes of the user or group, you can [use a scoping filter](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts).

- Start small. Test with a small set of users and groups before rolling out to everyone. When scope for provisioning is set to assigned users and groups, you can control this by assigning one or two users or groups to the app. When scope is set to all users and groups, you can specify an [attribute based scoping filter](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts).
- If you need extra roles, you can [update the application manifest](https://learn.microsoft.com/en-us/entra/identity-platform/howto-add-app-roles-in-apps) to add new roles.

## Step 5: Configure automatic user provisioning to getAbstract

This section guides you through the steps to configure the Microsoft Entra provisioning service to create, update, and disable users or groups in TestApp based on user or group assignments in Microsoft Entra ID.

### Configure automatic user provisioning for getAbstract in Microsoft Entra ID

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps**.

   ![Screenshot that shows the Enterprise applications pane.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/enterprise-applications.png)

3. In the list of applications, select **getAbstract**.

   ![Screenshot that shows the getAbstract link in the list of applications.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/all-applications.png)

4. Select the **Provisioning** tab.

   ![Screenshot that shows the Provisioning tab.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/provisioning.png)

5. Set **+ New configuration**.

   ![Screenshot of Provisioning tab automatic.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/application-provisioning.png)

6. In the **Tenant URL** field, input your getAbstract Tenant URL and Secret Token. Select **Test Connection** to ensure Microsoft Entra ID can connect to getAbstract. If the connection fails, ensure your getAbstract account has the required admin permissions and try again.

   ![Screenshot of Provisioning test connection.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/provisioning-test-connection.png)

7. Select **Create** to create your configuration.
8. Select **Properties** in the **Overview** page.
9. Select the pencil to edit the properties. Enable notification emails and provide an email to receive quarantine emails. Enable accidental deletions prevention. Select **Apply** to save the changes.

   ![Screenshot of Provisioning properties.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/provisioning-properties.png)

10. Select **Attribute Mapping** in the left panel and select **users**.
11. Review the user attributes that are synchronized from Microsoft Entra ID to getAbstract in the **Attribute Mapping** section. The attributes selected as **Matching** properties are used to match the user accounts in getAbstract for update operations. If you change the [matching target attribute](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/customize-application-attributes), you need to ensure that the getAbstract API supports filtering users based on that attribute. Select **Save** to commit any changes.
    | Attribute | Type | Supported for filtering |
    | --- | --- | --- |
    | userName | String | ✓ |
    | active | Boolean |  |
    | emails\[type eq "work"\].value | String |  |
    | name.givenName | String |  |
    | name.familyName | String |  |
    | externalId | String |  |
    | preferredLanguage | String |  |
12. Select **Groups**.
13. Review the group attributes that are synchronized from Microsoft Entra ID to getAbstract in the **Attribute Mapping** section. The attributes selected as **Matching** properties are used to match the groups in getAbstract for update operations. Select **Save** to commit any changes.
    | Attribute | Type | Supported for filtering |
    | --- | --- | --- |
    | displayName | String | ✓ |
    | externalId | String |  |
    | members | Reference |  |
14. To configure scoping filters, refer to the following instructions provided in the [Scoping filter article](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts).
15. Use [on-demand provisioning](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/provision-on-demand) to validate sync with a small number of users before deploying more broadly in your organization.
16. When you're ready to provision, select **Start Provisioning** from the **Overview** page.

## Step 6: Monitor your deployment

Once you configure provisioning, use the following resources to monitor your deployment:

1. Use the [provisioning logs](https://learn.microsoft.com/en-us/entra/identity/monitoring-health/concept-provisioning-logs) to determine which users are provisioned successfully or unsuccessfully
2. Check the [progress bar](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/application-provisioning-when-will-provisioning-finish-specific-user) to see the status of the provisioning cycle and how close it's to completion
3. If the provisioning configuration seems to be in an unhealthy state, the application goes into quarantine. Learn more about quarantine states the [application provisioning quarantine status](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/application-provisioning-quarantine-status) article.

## Additional resources

- [Managing user account provisioning for enterprise apps](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/configure-automatic-user-provisioning-portal)
- [What is application access and single sign-on with Microsoft Entra ID?](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/what-is-single-sign-on)

## Related content

- [Learn how to review logs and get reports on provisioning activity](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/check-status-user-account-provisioning)
