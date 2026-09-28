<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/ringcentral-provisioning-tutorial -->
<!-- Sitemap-Last-Modified: 2026-06-09 -->

# Configure RingCentral for automatic user provisioning with Microsoft Entra ID

This article describes the steps you need to perform in both RingCentral and Microsoft Entra ID to configure automatic user provisioning. When configured, Microsoft Entra ID automatically provisions and de-provisions users and groups to [RingCentral](https://www.ringcentral.com/office/plansandpricing.html) using the Microsoft Entra provisioning service. For important details on what this service does, how it works, and frequently asked questions, see [Automate user provisioning and deprovisioning to SaaS applications with Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/user-provisioning).

## Capabilities supported

- Create users in RingCentral
- Remove users in RingCentral when they don't require access anymore
- Keep user attributes synchronized between Microsoft Entra ID and RingCentral
- [Single sign-on](https://learn.microsoft.com/en-us/entra/identity/saas-apps/ringcentral-tutorial) to RingCentral \(recommended\)
- Code Auth Grant flow authentication supported.

RingCentral is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government | China operated by 21Vianet |
| :---: | :---: | :---: |
| ✅ | ✅ |  |

## Prerequisites

The scenario outlined in this article assumes that you already have the following prerequisites:

- [A Microsoft Entra tenant](https://learn.microsoft.com/en-us/entra/identity-platform/quickstart-create-new-tenant)
- A user account in Microsoft Entra ID with [permission](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference) to configure provisioning \(like [Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#application-administrator), [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator), or [Application Owner](https://learn.microsoft.com/en-us/entra/fundamentals/users-default-permissions#owned-enterprise-applications)\).
- [A RingCentral tenant](https://www.ringcentral.com/office/plansandpricing.html)
- A user account in RingCentral with Admin permissions.

## Step 1: Plan your provisioning deployment

1. Learn about [how the provisioning service works](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/user-provisioning).
2. Determine who's in [scope for provisioning](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts).
3. Determine what data to [map between Microsoft Entra ID and RingCentral](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/customize-application-attributes).

## Step 2: Configure RingCentral to support provisioning with Microsoft Entra ID

A [RingCentral](https://www.ringcentral.com/office/plansandpricing.html) admin account is required to Authorize in the Admin Credentials section in Step 5.

In the RingCentral admin portal, under Account Settings -> Directory Integrations, set the *Directory Provider* setting to *SCIM* ![image](https://user-images.githubusercontent.com/49566142/134523440-20320d8e-3c25-4358-9ace-d4888ce8e4ea.png)

Note

To assign licenses to users, refer to the video link [here](https://support.ringcentral.com/s/article/5-10-Adding-Extensions-via-Web?language).

## Step 3: Add RingCentral from the Microsoft Entra application gallery

Add RingCentral from the Microsoft Entra application gallery to start managing provisioning to RingCentral. If you have previously setup RingCentral for SSO you can use the same application. However, we recommend that you create a separate app when testing out the integration initially. Learn more about adding an application from the gallery [here](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/add-application-portal).

## Step 4: Define who is in scope for provisioning

The Microsoft Entra provisioning service allows you to scope who is provisioned based on assignment to the application, or based on attributes of the user or group. If you choose to scope who is provisioned to your app based on assignment, you can use the [steps to assign users and groups to the application](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/assign-user-or-group-access-portal). If you choose to scope who is provisioned based solely on attributes of the user or group, you can [use a scoping filter](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts).

- Start small. Test with a small set of users and groups before rolling out to everyone. When scope for provisioning is set to assigned users and groups, you can control this by assigning one or two users or groups to the app. When scope is set to all users and groups, you can specify an [attribute based scoping filter](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts).
- If you need extra roles, you can [update the application manifest](https://learn.microsoft.com/en-us/entra/identity-platform/howto-add-app-roles-in-apps) to add new roles.

## Step 5: Configure automatic user provisioning to RingCentral

This section guides you through the steps to configure the Microsoft Entra provisioning service to create, update, and disable users and/or groups in TestApp based on user and/or group assignments in Microsoft Entra ID.

### To configure automatic user provisioning for RingCentral in Microsoft Entra ID:

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps**

   ![Screenshot of Enterprise applications blade.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/enterprise-applications.png)

3. In the applications list, select **RingCentral**.

   ![Screenshot of the RingCentral link in the Applications list.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/all-applications.png)

4. Select the **Provisioning** tab.

   ![Screenshot of the Manage options with the Provisioning option called out.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/provisioning.png)

5. Set **+ New configuration**.

   ![Screenshot of Provisioning tab automatic.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/application-provisioning.png)

6. In the **Tenant URL** field, input your RingCentral Tenant URL and Secret Token. Select **Test Connection** to ensure Microsoft Entra ID can connect to RingCentral. If the connection fails, ensure your RingCentral account has the required admin permissions and try again.

   ![Screenshot of Provisioning test connection.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/provisioning-test-connection.png)

7. Select **Create** to create your configuration.
8. Select **Properties** in the **Overview** page.
9. Select the pencil to edit the properties. Enable notification emails and provide an email to receive quarantine emails. Enable accidental deletions prevention. Select **Apply** to save the changes.

   ![Screenshot of the Provisioning properties page showing notification and deletion settings.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/provisioning-properties.png)

10. Select **Attribute Mapping** in the left panel and select users.
11. Review the user attributes that are synchronized from Microsoft Entra ID to RingCentral in the **Attribute-Mapping** section. The attributes selected as **Matching** properties are used to match the user accounts in RingCentral for update operations. If you choose to change the [matching target attribute](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/customize-application-attributes), you need to ensure that the RingCentral API supports filtering users based on that attribute. Select the **Save** button to commit any changes.
    | Attribute | Type |
    | --- | --- |
    | userName | String |
    | externalId | String |
    | active | Boolean |
    | title | String |
    | emails\[type eq "work"\].value | String |
    | addresses\[type eq "work"\].country | String |
    | addresses\[type eq "work"\].region | String |
    | addresses\[type eq "work"\].locality | String |
    | addresses\[type eq "work"\].postalCode | String |
    | addresses\[type eq "work"\].streetAddress | String |
    | name.givenName | String |
    | name.familyName | String |
    | phoneNumbers\[type eq "mobile"\].value | String |
    | urn:ietf:params:scim:schemas:extension:enterprise:2.0:User:department | String |
12. To configure scoping filters, refer to the following instructions provided in the [Scoping filter article](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts) article.
13. Use [on-demand provisioning](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/provision-on-demand) to validate sync with a small number of users before deploying more broadly in your organization.
14. When you're ready to provision, select **Start Provisioning** from the **Overview** page.

## Step 6: Monitor your deployment

Once you configure provisioning, use the following resources to monitor your deployment:

1. Use the [provisioning logs](https://learn.microsoft.com/en-us/entra/identity/monitoring-health/concept-provisioning-logs) to determine which users are provisioned successfully or unsuccessfully
2. Check the [progress bar](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/application-provisioning-when-will-provisioning-finish-specific-user) to see the status of the provisioning cycle and how close it's to completion
3. If the provisioning configuration seems to be in an unhealthy state, the application goes into quarantine. Learn more about quarantine states the [application provisioning quarantine status](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/application-provisioning-quarantine-status) article.

## Change log

- 09/10/2020 - Removed support for "displayName" and "manager" attributes.
- 03/15/2021 - Updated authorization method from permanent bearer token to OAuth code grant flow.
- 10/28/2021 - Updated default mapping to **mail-> emails\[type eq “work”\].value**.
- 10/28/2021 - Rate limiting updated to 300/min for read, 1000/min for write.

## Additional resources

- [Managing user account provisioning for Enterprise Apps](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/configure-automatic-user-provisioning-portal)
- [What is application access and single sign-on with Microsoft Entra ID?](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/what-is-single-sign-on)

## Related content

- [Learn how to review logs and get reports on provisioning activity](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/check-status-user-account-provisioning)
