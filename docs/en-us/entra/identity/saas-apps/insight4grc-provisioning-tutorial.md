<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/insight4grc-provisioning-tutorial -->
<!-- Sitemap-Last-Modified: 2026-04-10 -->

# Configure Insight4GRC for automatic user provisioning with Microsoft Entra ID

This article describes the steps you need to perform in both Insight4GRC and Microsoft Entra ID to configure automatic user provisioning. When configured, Microsoft Entra ID automatically provisions and de-provisions users and groups to [Insight4GRC](https://www.rsmuk.com/) using the Microsoft Entra provisioning service. For important details on what this service does, how it works, and frequently asked questions, see [Automate user provisioning and deprovisioning to SaaS applications with Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/user-provisioning).

## Capabilities supported

- Create users in Insight4GRC
- Remove users in Insight4GRC when they don't require access anymore
- Keep user attributes synchronized between Microsoft Entra ID and Insight4GRC
- Provision groups and group memberships in Insight4GRC
- [Single sign-on](https://learn.microsoft.com/en-us/entra/identity/saas-apps/insight4grc-tutorial) to Insight4GRC \(recommended\)

Insight4GRC is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government | China operated by 21Vianet |
| :---: | :---: | :---: |
| ✅ | ✅ |  |

## Prerequisites

The scenario outlined in this article assumes that you already have the following prerequisites:

- [A Microsoft Entra tenant](https://learn.microsoft.com/en-us/entra/identity-platform/quickstart-create-new-tenant)
- A user account in Microsoft Entra ID with [permission](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference) to configure provisioning \(like [Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#application-administrator), [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator), or [Application Owner](https://learn.microsoft.com/en-us/entra/fundamentals/users-default-permissions#owned-enterprise-applications)\).
- A user account in Insight4GRC with Admin permissions.

## Step 1: Plan your provisioning deployment

1. Learn about [how the provisioning service works](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/user-provisioning).
2. Determine who's in [scope for provisioning](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts).
3. Determine what data to [map between Microsoft Entra ID and Insight4GRC](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/customize-application-attributes).

## Step 2: Configure Insight4GRC to support provisioning with Microsoft Entra ID

Before configuring Insight4GRC for automatic user provisioning with Microsoft Entra ID, you need to enable SCIM provisioning on Insight4GRC.

1. To obtain the bearer token, end-customer needs to contact [support team](mailto:support.ss@rsmuk.com).
2. To obtain the SCIM endpoint URL, you need to have your Insight4GRC domain name ready as it's used to construct your SCIM endpoint URL. You can retrieve your Insight4GRC domain name as part of the initial software purchase with Insight4GRC.

## Step 3: Add Insight4GRC from the Microsoft Entra application gallery

Add Insight4GRC from the Microsoft Entra application gallery to start managing provisioning to Insight4GRC. If you have previously setup Insight4GRC for SSO you can use the same application. However, we recommend that you create a separate app when testing out the integration initially. Learn more about adding an application from the gallery [here](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/add-application-portal).

## Step 4: Define who is in scope for provisioning

The Microsoft Entra provisioning service allows you to scope who is provisioned based on assignment to the application, or based on attributes of the user or group. If you choose to scope who is provisioned to your app based on assignment, you can use the [steps to assign users and groups to the application](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/assign-user-or-group-access-portal). If you choose to scope who is provisioned based solely on attributes of the user or group, you can [use a scoping filter](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts).

- Start small. Test with a small set of users and groups before rolling out to everyone. When scope for provisioning is set to assigned users and groups, you can control this by assigning one or two users or groups to the app. When scope is set to all users and groups, you can specify an [attribute based scoping filter](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts).
- If you need extra roles, you can [update the application manifest](https://learn.microsoft.com/en-us/entra/identity-platform/howto-add-app-roles-in-apps) to add new roles.

## Step 5: Configure automatic user provisioning to Insight4GRC

This section guides you through the steps to configure the Microsoft Entra provisioning service to create, update, and disable users and/or groups in TestApp based on user and/or group assignments in Microsoft Entra ID.

### To configure automatic user provisioning for Insight4GRC in Microsoft Entra ID:

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps**

   ![Enterprise applications blade](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/enterprise-applications.png)

3. In the applications list, select **Insight4GRC**.

   ![The Insight4GRC link in the Applications list](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/all-applications.png)

4. Select the **Provisioning** tab.

   ![Screenshot of the Manage options with the Provisioning option called out.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/provisioning.png)

5. Select **+ New configuration**.

   ![Screenshot of Provisioning tab automatic.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/application-provisioning.png)

6. Under the **Admin Credentials** section, input the SCIM endpoint URL in **Tenant URL**. The endpoint URL should be in the format `https://<Insight4GRC Domain Name>.insight4grc.com/public/api/scim/v2` where **Insight4GRC Domain Name** is the value retrieved in previous steps. Enter the bearer token value retrieved earlier in **Secret Token**. Select **Test Connection** to ensure Microsoft Entra ID can connect to Insight4GRC. If the connection fails, ensure your Insight4GRC account has Admin permissions and try again.

   ![Screenshot shows the Admin Credentials dialog box, where you can enter your Tenant U R L and Secret Token.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/insight4grc-provisioning-tutorial/provisioning.png)

7. In the **Notification Email** field, enter the email address of a person who should receive the provisioning error notifications and select the **Send an email notification when a failure occurs** check box.

   ![Screenshot of Provisioning properties.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/provisioning-properties.png)

8. Select **Attribute Mapping** in the left panel and select **users**.
9. Review the user attributes that are synchronized from Microsoft Entra ID to Insight4GRC in the **Attribute-Mapping** section. The attributes selected as **Matching** properties are used to match the user accounts in Insight4GRC for update operations. If you choose to change the [matching target attribute](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/customize-application-attributes), you need to ensure that the Insight4GRC API supports filtering users based on that attribute. Select the **Save** button to commit any changes.
   | Attribute | Type | Supported for filtering |
   | --- | --- | --- |
   | userName | String | ✓ |
   | externalId | String | ✓ |
   | active | Boolean |  |
   | urn:ietf:params:scim:schemas:extension:enterprise:2.0:User:manager | String |  |
   | title | String |  |
   | name.givenName | String |  |
   | name.familyName | String |  |
   | emails\[type eq "work"\].value | String |  |
   | phoneNumbers\[type eq "work"\].value | String |  |
10. Review the group attributes that are synchronized from Microsoft Entra ID to Insight4GRC in the **Attribute-Mapping** section. The attributes selected as **Matching** properties are used to match the groups in Insight4GRC for update operations. Select the **Save** button to commit any changes.
    | Attribute | Type |
    | --- | --- |
    | displayName | String |
    | externalId | String |
    | members | Reference |
11. To configure scoping filters, refer to the instructions provided in the [Scoping filter article](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts).
12. Use [on-demand provisioning](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/provision-on-demand) to validate sync with a small number of users before deploying more broadly in your organization.
13. When you're ready to provision, select **Start Provisioning** from the **Overview** page.

## Step 6: Monitor your deployment

Once you configure provisioning, use the following resources to monitor your deployment:

1. Use the [provisioning logs](https://learn.microsoft.com/en-us/entra/identity/monitoring-health/concept-provisioning-logs) to determine which users are provisioned successfully or unsuccessfully
2. Check the [progress bar](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/application-provisioning-when-will-provisioning-finish-specific-user) to see the status of the provisioning cycle and how close it's to completion
3. If the provisioning configuration seems to be in an unhealthy state, the application goes into quarantine. Learn more about quarantine states the [application provisioning quarantine status](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/application-provisioning-quarantine-status) article.

## Change log

- 08/19/2021 - Enterprise extension User attribute **manager** has been added.

## Additional resources

- [Managing user account provisioning for Enterprise Apps](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/configure-automatic-user-provisioning-portal).
- [What is application access and single sign-on with Microsoft Entra ID?](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/what-is-single-sign-on)

## Related content

- [Learn how to review logs and get reports on provisioning activity](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/check-status-user-account-provisioning).
