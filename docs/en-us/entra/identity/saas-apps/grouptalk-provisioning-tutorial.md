<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/grouptalk-provisioning-tutorial -->
<!-- Sitemap-Last-Modified: 2026-04-10 -->

# Configure GroupTalk for automatic user provisioning with Microsoft Entra ID

This article describes the steps you need to perform in both GroupTalk and Microsoft Entra ID to configure automatic user provisioning. When configured, Microsoft Entra ID automatically provisions and de-provisions users and groups to [GroupTalk](https://www.grouptalk.com/) using the Microsoft Entra provisioning service. For important details on what this service does, how it works, and frequently asked questions, see [Automate user provisioning and deprovisioning to SaaS applications with Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/user-provisioning).

## Capabilities Supported

- Create users in GroupTalk
- Remove users in GroupTalk when they don't require access anymore
- Keep user attributes synchronized between Microsoft Entra ID and GroupTalk
- Provision groups and group memberships in GroupTalk
- Long lived bearer token authentication supported.

## Prerequisites

The scenario outlined in this article assumes that you already have the following prerequisites:

- 

  - A Microsoft Entra user account with an active subscription. If you don't already have one, you can [Create an account for free](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
  - One of the following roles:

    - [Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#application-administrator)
    - [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator)
    - [Application Owner](https://learn.microsoft.com/en-us/entra/fundamentals/users-default-permissions#owned-enterprise-applications).

- A user account in GroupTalk with Admin permissions.

## Step 1: Plan your provisioning deployment

1. Learn about [how the provisioning service works](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/user-provisioning).
2. Determine who's in [scope for provisioning](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts).
3. Determine what data to [map between Microsoft Entra ID and GroupTalk](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/customize-application-attributes).

## Step 2: Configure GroupTalk to support provisioning with Microsoft Entra ID

1. Reach out to GroupTalk Support at support@grouptalk.com with the **Tenant name** and **ID** you would like to integrate with Microsoft Entra ID.
2. When you've been notified that the necessary setup for your Microsoft Entra integration is ready, login to GroupTalk Admin and navigate to your Organization view.
3. A Microsoft Entra Integration configuration item should be visible. Select it to verify the **Tenant name** and **ID** to obtain a **JWT \(Secret Token\)**.
4. The GroupTalk Tenant URL is `https://api.grouptalk.com/api/scim/`. The **Tenant URL** and the **Secret Token** retrieved in the previous step is entered in the Provisioning tab of your GroupTalk application.

## Step 3: Add GroupTalk from the Microsoft Entra application gallery

Add **GroupTalk** from the Microsoft Entra application gallery to start managing provisioning to GroupTalk.

1. Select the **Sign up for GroupTalk** button, which will route you to the GroupTalk administrative application.
2. If you're already logged in to GroupTalk, logout to get to the login screen. Select the Microsoft Entra ID tab, and select the **Sign in** button.

   ![GroupTalk](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/grouptalk-provisioning-tutorial/login.png)

3. Login with your AD Administrative account, and accept the GroupTalk application's access rights. You get an error message after this is done indicating the user isn't present. This is expected since your user isn't provisioned to GroupTalk yet but you have now added GroupTalk to your tenant.
4. Go back to the Azure portal and verify that **GroupTalk** is now added to your Enterprise Applications.

Learn more about adding an application from the gallery [here](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/add-application-portal).

## Step 4: Define who is in scope for provisioning

The Microsoft Entra provisioning service allows you to scope who is provisioned based on assignment to the application, or based on attributes of the user or group. If you choose to scope who is provisioned to your app based on assignment, you can use the [steps to assign users and groups to the application](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/assign-user-or-group-access-portal). If you choose to scope who is provisioned based solely on attributes of the user or group, you can [use a scoping filter](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts).

- Start small. Test with a small set of users and groups before rolling out to everyone. When scope for provisioning is set to assigned users and groups, you can control this by assigning one or two users or groups to the app. When scope is set to all users and groups, you can specify an [attribute based scoping filter](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts).
- If you need extra roles, you can [update the application manifest](https://learn.microsoft.com/en-us/entra/identity-platform/howto-add-app-roles-in-apps) to add new roles.

## Step 5: Configure automatic user provisioning to GroupTalk

This section guides you through the steps to configure the Microsoft Entra provisioning service to create, update, and disable users and/or groups in TestApp based on user and/or group assignments in Microsoft Entra ID.

### To configure automatic user provisioning for GroupTalk in Microsoft Entra ID:

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps**

   ![Enterprise applications blade](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/enterprise-applications.png)

3. In the applications list, select **GroupTalk**.

   ![The GroupTalk link in the Applications list](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/all-applications.png)

4. Select the **Provisioning** tab.

   ![Provisioning tab](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/provisioning.png)

5. Select **+ New configuration**.

   ![Screenshot of Provisioning tab automatic.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/application-provisioning.png)

6. In the **Tenant URL** field, enter your GroupTalk Tenant URL and Secret Token. Select **Test Connection** to ensure Microsoft Entra ID can connect to GroupTalk. If the connection fails, ensure your GroupTalk account has the required admin permissions and try again.

   ![Screenshot of Provisioning test connection.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/provisioning-test-connection.png)

7. Select **Create** to create your configuration.
8. Select **Properties** on the **Overview** page.
9. In the **Notification Email** field, enter the email address of a person who should receive the provisioning error notifications and select the **Send an email notification when a failure occurs** check box.

   ![Screenshot of Provisioning properties.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/provisioning-properties.png)

10. Select **Attribute Mapping** in the left panel and select **users**.
11. Review the user attributes that are synchronized from Microsoft Entra ID to GroupTalk in the **Attribute-Mapping** section. The attributes selected as **Matching** properties are used to match the user accounts in GroupTalk for update operations. If you choose to change the [matching target attribute](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/customize-application-attributes), you need to ensure that the GroupTalk API supports filtering users based on that attribute. Select the **Save** button to commit any changes.
    | Attribute | Type | Supported for filtering |
    | --- | --- | --- |
    | userName | String | ✓ |
    | phoneNumbers\[type eq "mobile"\].value | String | ✓ |
    | emails\[type eq "work"\].value | String | ✓ |
    | active | Boolean |  |
    | name.givenName | String |  |
    | name.familyName | String |  |
    | externalId | String |  |
    | urn:ietf:params:scim:schemas:extension:enterprise:2.0:User:costCenter | String |  |
    | urn:ietf:params:scim:schemas:extension:enterprise:2.0:User:organization | String |  |
    | urn:ietf:params:scim:schemas:extension:grouptalk:2.0:User:label1 | String |  |
    | urn:ietf:params:scim:schemas:extension:grouptalk:2.0:User:label2 | String |  |
    | urn:ietf:params:scim:schemas:extension:grouptalk:2.0:User:label3 | String |  |
    | urn:ietf:params:scim:schemas:extension:grouptalk:2.0:User:label4 | String |  |
    | urn:ietf:params:scim:schemas:extension:grouptalk:2.0:User:label5 | String |  |
12. Review the group attributes that are synchronized from Microsoft Entra ID to GroupTalk in the **Attribute-Mapping** section. The attributes selected as **Matching** properties are used to match the groups in GroupTalk for update operations. Select the **Save** button to commit any changes.
    | Attribute | Type | Supported for filtering |
    | --- | --- | --- |
    | displayName | String | ✓ |
    | members | Reference |  |
    | externalId | String |  |
    | urn:ietf:params:scim:schemas:extension:grouptalk:2.0:Group:description | String |  |
13. To configure scoping filters, refer to the instructions provided in the [Scoping filter article](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts).
14. Use [on-demand provisioning](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/provision-on-demand) to validate sync with a small number of users before deploying more broadly in your organization.
15. When you're ready to provision, select **Start Provisioning** from the **Overview** page.

## Step 6: Monitor your deployment

Once you configure provisioning, use the following resources to monitor your deployment:

1. Use the [provisioning logs](https://learn.microsoft.com/en-us/entra/identity/monitoring-health/concept-provisioning-logs) to determine which users are provisioned successfully or unsuccessfully
2. Check the [progress bar](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/application-provisioning-when-will-provisioning-finish-specific-user) to see the status of the provisioning cycle and how close it's to completion
3. If the provisioning configuration seems to be in an unhealthy state, the application goes into quarantine. Learn more about quarantine states the [application provisioning quarantine status](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/application-provisioning-quarantine-status) article.

## Additional resources

- [Managing user account provisioning for Enterprise Apps](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/configure-automatic-user-provisioning-portal)
- [What is application access and single sign-on with Microsoft Entra ID?](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/what-is-single-sign-on)

## Related content

- [Learn how to review logs and get reports on provisioning activity](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/check-status-user-account-provisioning)
