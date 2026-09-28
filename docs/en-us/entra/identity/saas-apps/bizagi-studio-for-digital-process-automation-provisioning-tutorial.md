<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/bizagi-studio-for-digital-process-automation-provisioning-tutorial -->
<!-- Sitemap-Last-Modified: 2026-03-05 -->

# Configure Bizagi Studio for Digital Process Automation for automatic user provisioning with Microsoft Entra ID

This article describes the steps you need to perform in both Bizagi Studio for Digital Process Automation and Microsoft Entra ID to configure automatic user provisioning. When configured to do so, Microsoft Entra ID automatically provisions and deprovisions users and groups to [Bizagi Studio for Digital Process Automation](https://www.bizagi.com/) by using the Microsoft Entra provisioning service. For important details on what this service does, how it works, and frequently asked questions, see [Automate user provisioning and deprovisioning to SaaS applications with Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/user-provisioning).

## Capabilities supported

- Create users in Bizagi Studio for Digital Process Automation.
- Remove users in Bizagi Studio for Digital Process Automation when they don't require access anymore.
- Keep user attributes synchronized between Microsoft Entra ID and Bizagi Studio for Digital Process Automation.
- [Single sign-on](https://learn.microsoft.com/en-us/entra/identity/saas-apps/bizagi-studio-for-digital-process-automation-tutorial) to Bizagi Studio for Digital Process Automation \(recommended\).
- Long lived bearer token authentication supported.

## Prerequisites

The scenario outlined in this article assumes that you already have the following:

- [A Microsoft Entra tenant](https://learn.microsoft.com/en-us/entra/identity-platform/quickstart-create-new-tenant).
- One of the following roles: [Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#application-administrator), [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator), or [Application Owner](https://learn.microsoft.com/en-us/entra/fundamentals/users-default-permissions#owned-enterprise-applications).
- Bizagi Studio for Digital Process Automation version 11.2.4.2X or later.

## Plan your provisioning deployment

Follow these steps for planning:

1. Learn about [how the provisioning service works](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/user-provisioning).
2. Determine who's [in scope for provisioning](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts).
3. Determine what data to [map between Microsoft Entra ID and Bizagi Studio for Digital Process Automation](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/customize-application-attributes).

## Configure to support provisioning with Microsoft Entra ID

To configure Bizagi Studio for Digital Process Automation to support provisioning with Microsoft Entra ID, follow these steps:

1. Sign in to your work portal as a user with **Admin permissions**.
2. Go to **Admin** > **Security** > **OAuth 2 Applications**.

   ![Screenshot of Bizagi, with OAuth 2 Applications highlighted.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/bizagi-studio-for-digital-process-automation-provisioning-tutorial/admin.png)

3. Select **Add**.
4. For **Grant Type**, select **Bearer token**. For **Allowed Scope**, select **API** and **USER SYNC**. Then select **Save**.

   ![Screenshot of Register Application, with Grant Type and Allowed Scope highlighted.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/bizagi-studio-for-digital-process-automation-provisioning-tutorial/token.png)

5. Copy and save the **Client Secret**. In the Azure portal, for your Bizagi Studio for Digital Process Automation application, on the **Provisioning** tab, the client secret value is entered in the **Secret Token** field.

   ![Screenshot of Oauth, with Client Secret highlighted.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/bizagi-studio-for-digital-process-automation-provisioning-tutorial/secret.png)

## Add the application from the Microsoft Entra gallery

To start managing provisioning to Bizagi Studio for Digital Process Automation, add the app from the Microsoft Entra application gallery. If you have previously set up Bizagi Studio for Digital Process Automation for single sign-on, you can use the same application. When you're initially testing the integration, however, you should create a separate app. For more information, see [Quickstart: Add an application to your Microsoft Entra tenant](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/add-application-portal).

## Define who is in scope for provisioning

The Microsoft Entra provisioning service allows you to scope who is provisioned based on assignment to the application, or based on attributes of the user or group. If you choose to scope who is provisioned to your app based on assignment, you can use the [steps to assign users and groups to the application](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/assign-user-or-group-access-portal). If you choose to scope who is provisioned based solely on attributes of the user or group, you can [use a scoping filter](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts).

- Start small. Test with a small set of users and groups before rolling out to everyone. When scope for provisioning is set to assigned users and groups, you can control this by assigning one or two users or groups to the app. When scope is set to all users and groups, you can specify an [attribute based scoping filter](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts).
- If you need extra roles, you can [update the application manifest](https://learn.microsoft.com/en-us/entra/identity-platform/howto-add-app-roles-in-apps) to add new roles.

## Configure automatic user provisioning

This section guides you through the steps to configure the Microsoft Entra provisioning service to create, update, and disable users and groups. You're doing this in your test app, based on user and group assignments in Microsoft Entra ID.

### Configure automatic user provisioning for Bizagi Studio for Digital Process Automation in Microsoft Entra ID

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps**.

   ![Screenshot of the Azure portal, with Enterprise applications and All applications highlighted.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/enterprise-applications.png)

3. In the applications list, select **Bizagi Studio for Digital Process Automation**.
4. Select the **Provisioning** tab.

   ![Screenshot of Manage options, with Provisioning highlighted.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/provisioning.png)

5. Set **+ New configuration**.

   ![Screenshot of Provisioning tab automatic.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/application-provisioning.png)

6. In the **Tenant URL** field, input your Bizagi Studio for Digital Process Automation Tenant URL and Secret Token. Select **Test Connection** to ensure Microsoft Entra ID can connect to Bizagi Studio for Digital Process Automation. If the connection fails, ensure your Bizagi Studio for Digital Process Automation account has the required admin permissions and try again.

   ![Screenshot of Provisioning test connection.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/provisioning-test-connection.png)


   - **Tenant URL:** Enter the Bizagi SCIM endpoint, with the following structure: `<Your_Bizagi_Project>/scim/v2/`. For example: `https://my-company.bizagi.com/scim/v2/`.
   - **Secret token:** This value is retrieved from the step discussed earlier in this article.

7. Select **Create** to create your configuration.
8. Select **Properties** in the **Overview** page.
9. Select the pencil to edit the properties. Enable notification emails and provide an email to receive quarantine emails. Enable accidental deletions prevention. Select **Apply** to save the changes.

   ![Screenshot of Provisioning properties.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/provisioning-properties.png)

10. Select **Attribute Mapping** in the left panel and select **users**.
11. In the **Attribute-Mapping** section, review the user attributes that are synchronized from Microsoft Entra ID to Bizagi Studio for Digital Process Automation. The attributes selected as **Matching** properties are used to match the user accounts in Bizagi Studio for Digital Process Automation for update operations. If you change the [matching target attribute](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/customize-application-attributes), you must ensure that the Bizagi Studio for Digital Process Automation API supports filtering users based on that attribute. Select **Save** to commit any changes.
    | Attribute | Type | Supported for filtering |
    | --- | --- | --- |
    | userName | String | ✓ |
    | active | Boolean |  |
    | emails\[type eq "work"\].value | String |  |
    | name.givenName | String |  |
    | name.familyName | String |  |
    | name.formatted | String |  |
    | phoneNumbers\[type eq "mobile"\].value | String |  |


    Custom extension attributes can be added by navigating to **Show advanced options > Edit attribute list for Bizagi**. The custom extension attributes must be prefixed with **urn:ietf:params:scim:schemas:extension:bizagi:2.0:UserProperties:**. For example, if custom extension attribute is **IdentificationNumber**, the attribute must be added as **urn:ietf:params:scim:schemas:extension:bizagi:2.0:UserProperties:IdentificationNumber**. Select **Save** to commit any changes.


    ![Edit attribute list.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/bizagi-studio-for-digital-process-automation-provisioning-tutorial/edit.png)


    More information on how to add custom attributes can be found in [Customize Application Attributes](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/customize-application-attributes).

Note

Only basic type properties are supported \(for example, String, Integer, Boolean, DateTime, and so on\). The properties linked to parametric tables or multiple types aren't supported yet.

1. To configure scoping filters, refer to the following instructions provided in the [Scoping filter article](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts).
2. Use [on-demand provisioning](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/provision-on-demand) to validate sync with a small number of users before deploying more broadly in your organization.
3. When you're ready to provision, select **Start Provisioning** from the **Overview** page.

For more information on how to read the Microsoft Entra provisioning logs, see [Reporting on automatic user account provisioning](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/check-status-user-account-provisioning).

## Monitor your deployment

Once you configure provisioning, use the following resources to monitor your deployment:

1. Use the [provisioning logs](https://learn.microsoft.com/en-us/entra/identity/monitoring-health/concept-provisioning-logs) to determine which users are provisioned successfully or unsuccessfully
2. Check the [progress bar](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/application-provisioning-when-will-provisioning-finish-specific-user) to see the status of the provisioning cycle and how close it's to completion
3. If the provisioning configuration seems to be in an unhealthy state, the application goes into quarantine. Learn more about quarantine states the [application provisioning quarantine status](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/application-provisioning-quarantine-status) article.

## Additional resources

- [Managing user account provisioning for Enterprise Apps](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/configure-automatic-user-provisioning-portal)
- [What is application access and single sign-on with Microsoft Entra ID?](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/what-is-single-sign-on)

## Related content

- [Learn how to review logs and get reports on provisioning activity](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/check-status-user-account-provisioning)
