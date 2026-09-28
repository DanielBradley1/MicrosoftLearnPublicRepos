<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/servicenow-provisioning-tutorial -->
<!-- Sitemap-Last-Modified: 2026-04-24 -->

# Configure ServiceNow for automatic user provisioning with Microsoft Entra ID

This article describes the steps that you take in both ServiceNow and Microsoft Entra ID to configure automatic user provisioning. When Microsoft Entra ID is configured, it automatically provisions and deprovisions users and groups to [ServiceNow](https://www.servicenow.com) by using the Microsoft Entra provisioning service.

For more information on the Microsoft Entra automatic user provisioning service, see [Automate user provisioning and deprovisioning to SaaS applications with Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/user-provisioning).

## Capabilities supported

- Create users in ServiceNow.
- Remove users in ServiceNow when they don't need access anymore.
- Keep user attributes synchronized between Microsoft Entra ID and ServiceNow.
- Provision groups and group memberships in ServiceNow.
- Allow [single sign-on](https://learn.microsoft.com/en-us/entra/identity/saas-apps/servicenow-tutorial) to ServiceNow \(recommended\).
- Basic Authentication authentication supported.

ServiceNow is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government | China operated by 21Vianet |
| :---: | :---: | :---: |
| ✅ | ✅ |  |

## Prerequisites

- A Microsoft Entra user account with an active subscription. If you don't already have one, you can [Create an account for free](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
- One of the following roles: [Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#application-administrator), [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator), or [Application Owner](https://learn.microsoft.com/en-us/entra/fundamentals/users-default-permissions#owned-enterprise-applications).
- A [ServiceNow instance](https://www.servicenow.com) of Calgary or higher.
- A [ServiceNow Express instance](https://www.servicenow.com) of Helsinki or higher.
- A user account in ServiceNow with the admin role.

## Step 1: Plan your provisioning deployment

- Learn about [how the provisioning service works](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/user-provisioning).
- Determine who's in [scope for provisioning](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts).
- Determine what data to [map between Microsoft Entra ID and ServiceNow](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/customize-application-attributes).

## Step 2: Configure ServiceNow to support provisioning with Microsoft Entra ID

1. Identify your ServiceNow instance name. You can find the instance name in the URL that you use to access ServiceNow. In the following example, the instance name is **dev35214**.

   ![Screenshot that shows a ServiceNow instance.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/servicenow-provisioning-tutorial/servicenow-instance.png)

2. Obtain credentials for an admin in ServiceNow. Go to the user profile in ServiceNow and verify that the user has the admin role.

   ![Screenshot that shows a ServiceNow admin role.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/servicenow-provisioning-tutorial/servicenow-admin-role.png)

## Step 3: Add ServiceNow from the Microsoft Entra application gallery

Add ServiceNow from the Microsoft Entra application gallery to start managing provisioning to ServiceNow. If you previously set up ServiceNow for single sign-on \(SSO\), you can use the same application. However, we recommend that you create a separate app when you're testing the integration. [Learn more about adding an application from the gallery](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/add-application-portal).

## Step 4: Define who is in scope for provisioning

The Microsoft Entra provisioning service allows you to scope who is provisioned based on assignment to the application, or based on attributes of the user or group. If you choose to scope who is provisioned to your app based on assignment, you can use the [steps to assign users and groups to the application](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/assign-user-or-group-access-portal). If you choose to scope who is provisioned based solely on attributes of the user or group, you can [use a scoping filter](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts).

- Start small. Test with a small set of users and groups before rolling out to everyone. When scope for provisioning is set to assigned users and groups, you can control this by assigning one or two users or groups to the app. When scope is set to all users and groups, you can specify an [attribute based scoping filter](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts).
- If you need extra roles, you can [update the application manifest](https://learn.microsoft.com/en-us/entra/identity-platform/howto-add-app-roles-in-apps) to add new roles.

## Step 5: Configure automatic user provisioning to ServiceNow

This section guides you through the steps to configure the Microsoft Entra provisioning service to create, update, and disable users and groups in TestApp. You can base the configuration on user and group assignments in Microsoft Entra ID.

### Configure automatic user provisioning for ServiceNow in Microsoft Entra ID

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps**.

   ![Screenshot that shows the Enterprise applications pane.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/enterprise-applications.png)

3. In the list of applications, select **ServiceNow**.
4. Select the **Provisioning** tab.

   ![Screenshot of the Manage options with the Provisioning option called out.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/provisioning.png)

5. Select **+ New configuration**.

   ![Screenshot of the New configuration option on the Provisioning page.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/application-provisioning.png)

6. In the **Tenant URL** field, enter your ServiceNow Tenant URL and Secret Token. Select **Test Connection** to ensure Microsoft Entra ID can connect to ServiceNow. If the connection fails, ensure your ServiceNow account has the required admin permissions and try again.
7. Select **Create** to create your configuration.
8. Select **Properties** on the **Overview** page.
9. Select the **Edit** icon to edit the properties. Enable notification emails and provide an email to receive quarantine notifications. Enable **Accidental deletions prevention**. Select **Apply** to save the changes.

   ![Screenshot of the Provisioning properties page.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/provisioning-properties.png)

10. Select **Attribute Mapping** in the left panel and select **users**.
11. Review the user attributes that are synchronized from Microsoft Entra ID to ServiceNow in the **Attribute-Mapping** section. The attributes selected as **Matching** properties are used to match the user accounts in ServiceNow for update operations.

    If you choose to change the [matching target attribute](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/customize-application-attributes), you need to ensure that the ServiceNow API supports filtering users based on that attribute.

    Select the **Save** button to commit any changes.
12. Select **Groups**.
13. Review the group attributes that are synchronized from Microsoft Entra ID to ServiceNow in the **Attribute-Mapping** section. The attributes selected as **Matching** properties are used to match the groups in ServiceNow for update operations. Select the **Save** button to commit any changes.
14. To configure scoping filters, refer to the instructions provided in the [Scoping filter article](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts).
15. Use [on-demand provisioning](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/provision-on-demand) to validate sync with a small number of users before deploying more broadly in your organization.
16. When you're ready to provision, select **Start Provisioning** from the **Overview** page.

## Step 6: Monitor your deployment

Once you configure provisioning, use the following resources to monitor your deployment:

1. Use the [provisioning logs](https://learn.microsoft.com/en-us/entra/identity/monitoring-health/concept-provisioning-logs) to determine which users are provisioned successfully or unsuccessfully
2. Check the [progress bar](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/application-provisioning-when-will-provisioning-finish-specific-user) to see the status of the provisioning cycle and how close it's to completion
3. If the provisioning configuration seems to be in an unhealthy state, the application goes into quarantine. Learn more about quarantine states the [application provisioning quarantine status](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/application-provisioning-quarantine-status) article.

## Troubleshooting tips

- When you're provisioning certain attributes \(such as **Department** and **Location**\) in ServiceNow, the values must already exist in a reference table in ServiceNow. If they don't, you get an **InvalidLookupReference** error.

  For example, you might have two locations \(Seattle, Los Angeles\) and three departments \(Sales, Finance, Marketing\) in a certain table in ServiceNow. If you try to provision a user whose department is "Sales" and whose location is "Seattle," that user is provisioned successfully. If you try to provision a user whose department is "Sales" and whose location is "LA," the user won't be provisioned. The location "LA" must be added to the reference table in ServiceNow, or the user attribute in Microsoft Entra ID must be updated to match the format in ServiceNow.
- If you get an **EntryJoiningPropertyValueIsMissing** error, review your [attribute mappings](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/customize-application-attributes) to identify the matching attribute. This value must be present on the user or group you're trying to provision.
- To understand any requirements or limitations \(for example, the format to specify a country code for a user\), review the [ServiceNow SOAP API](https://docs.servicenow.com/bundle/rome-application-development/page/integrate/web-services-apis/reference/r_DirectWebServiceAPIFunctions.html).
- Provisioning requests are sent by default to https://{your-instance-name}.service-now.com/{table-name}. If you need a custom tenant URL, you can provide the entire URL as the instance name.
- The **ServiceNowInstanceInvalid** error indicates a problem communicating with the ServiceNow instance. Here's the text of the error:

  `Details: Your ServiceNow instance name appears to be invalid.  Please provide a current ServiceNow administrative user name and          password along with the name of a valid ServiceNow instance.`

  If you're having test connection problems, try selecting **No** for the following settings in ServiceNow:

  - **System Security** > **High security settings** > **Require basic authentication for incoming SCHEMA requests**
  - **System Properties** > **Web Services** > **Require basic authorization for incoming SOAP requests**

    ![Screenshot that shows the option for authorizing SOAP requests.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/servicenow-provisioning-tutorial/servicenow-webservice.png)


  If you still can't resolve your problem, contact ServiceNow support, and ask them to turn on SOAP debugging to help troubleshoot.

- The Microsoft Entra provisioning service currently operates under particular [IP ranges](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/use-scim-to-provision-users-and-groups#ip-ranges). If necessary, you can restrict other IP ranges and add these particular IP ranges to the allow list of your application. That technique will allow traffic flow from the Microsoft Entra provisioning service to your application.
- Self-hosted ServiceNow instances aren't supported.
- When an update to the *active* attribute in ServiceNow is provisioned, the attribute *locked\_out* is also updated accordingly, even if *locked\_out* isn't mapped in the Azure provisioning service.

## Additional resources

- [Managing user account provisioning for enterprise apps](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/configure-automatic-user-provisioning-portal)
- [What is single sign-on with Microsoft Entra ID?](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/what-is-single-sign-on)

## Related content

- [Learn how to review logs and get reports on provisioning activity](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/check-status-user-account-provisioning)
