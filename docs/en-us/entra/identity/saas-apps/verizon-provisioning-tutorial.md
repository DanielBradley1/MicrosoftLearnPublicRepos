<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/verizon-provisioning-tutorial -->
<!-- Sitemap-Last-Modified: 2026-05-21 -->

# Configure Verizon Provisioning for automatic user provisioning with Microsoft Entra ID

This article describes the steps you need to perform in both Verizon User Provisioning and Microsoft Entra ID to configure automatic user provisioning. When configured, Microsoft Entra ID automatically provisions and deprovisions users to [Verizon User Provisioning](https://www.verizon.com) using the Microsoft Entra provisioning service. For important details on what this service does, how it works, and frequently asked questions, see [Automate user provisioning and deprovisioning to SaaS applications with Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/user-provisioning).

## Capabilities supported

- Create users in Verizon Provisioning
- Remove users in Verizon Provisioning when they don't require access anymore
- Keep user attributes synchronized between Microsoft Entra ID and Verizon Provisioning
- Provision groups and group memberships in Verizon.
- Verizon supports Client Credentials Authentication.

## Prerequisites

The scenario outlined in this article assumes that you already have the following prerequisites:

- [A Microsoft Entra tenant](https://learn.microsoft.com/en-us/entra/identity-platform/quickstart-create-new-tenant)
- One of the following roles: [Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#application-administrator), [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator), or [Application Owner](https://learn.microsoft.com/en-us/entra/fundamentals/users-default-permissions#owned-enterprise-applications).
- A user account in Verizon User Provisioning with Admin permissions.

## Step 1: Plan your provisioning deployment

- Learn about [how the provisioning service works](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/user-provisioning).
- Determine who's in [scope for provisioning](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts).
- Determine what data to [map between Microsoft Entra ID and Verizon User Provisioning](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/customize-application-attributes).

## Step 2: Configure Verizon Provisioning to support provisioning with Microsoft Entra ID

1. Log in to the Verizon On Site Network Dashboard with your administrator credentials.
2. Navigate to **SIM Management > Directory Sync** and make sure **Discovery Sync** is toggled **ON** \(toggle button will show green\).

   ![Screenshot of showing verizon configuration.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/verizon-provisioning-tutorial/configuration.png)

3. Copy the **URL Endpoint**, the **Token URL endpoint** and **Client ID** required for configuration and you will need to enter these in Microsoft Entra side.
4. Select any **additional attributes** you want to synchronize with Verizon’s Private Network.

   Note

   Certain mandatory attributes \(e.g. ICCID\) are preselected and grayed out.
5. Click **Save**.

## Step 3: Add Verizon Provisioning from the Microsoft Entra application gallery

Add Verizon from the Microsoft Entra application gallery to start managing provisioning to Verizon. If you have previously setup Verizon OSND, you can use the same application. However, we recommend that you create a separate app when testing out the integration initially. Learn more about adding an application from the gallery here. [here](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/add-application-portal).

## Step 4: Define who is in scope for provisioning

The Microsoft Entra provisioning service allows you to scope who is provisioned based on assignment to the application, or based on attributes of the user or group. If you choose to scope who is provisioned to your app based on assignment, you can use the [steps to assign users and groups to the application](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/assign-user-or-group-access-portal). If you choose to scope who is provisioned based solely on attributes of the user or group, you can [use a scoping filter](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts).

- Start small. Test with a small set of users and groups before rolling out to everyone. When scope for provisioning is set to assigned users and groups, you can control this by assigning one or two users or groups to the app. When scope is set to all users and groups, you can specify an [attribute based scoping filter](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts).
- If you need extra roles, you can [update the application manifest](https://learn.microsoft.com/en-us/entra/identity-platform/howto-add-app-roles-in-apps) to add new roles.

## Step 5: Configure automatic user provisioning to Verizon Provisioning

This section guides you through the steps to configure the Microsoft Entra provisioning service to create, update, and disable users in Verizon Provisioning based on user assignments in Microsoft Entra ID.

### Configure automatic user provisioning for Verizon Provisioning in Microsoft Entra ID

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least an app owner or a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps**

   ![Screenshot shows the enterprise applications blade.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/enterprise-applications.png "Enterprise application")

3. In the applications list, select **Verizon**.

   ![Screenshot shows the Verizon link in the Applications list.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/all-applications.png "Application List")

4. Select the **Provisioning** tab.

   ![Screenshot shows the provisioning tab configuration.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/provisioning.png "Tab")

5. Select **+ New configuration**.

   ![Screenshot of new configuration Provisioning tab automatic.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/application-provisioning.png)

6. In the Tenant URL field, input your Verizon **Tenant URL, Client identifier, Client secret** and **OAuth token endpoint**. Select **Test connection** to ensure Microsoft Entra ID can connect to Verizon. If the connection fails, ensure your Verizon account has Admin permissions and try again.

   ![Screenshot of Provisioning test connection.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/provisioning-test-button.png)

7. Select **Create** to create your configuration.
8. Select **Properties** in the **Overview** page.
9. Select the **Edit** icon to edit the properties. Enable notification emails and provide an email to receive quarantine emails. Enable accidental deletions prevention. Click **Apply** to save the changes.

   ![Screenshot of Provisioning properties.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/provisioning-properties.png)

10. Select **Attribute Mapping** in the left panel and select users.
11. Review the user attributes that are synchronized from Microsoft Entra ID to Verizon in the **Attribute-Mapping** section. The attributes selected as **Matching** properties are used to match the user accounts in Verizon for update operations. If you choose to change the [matching target attribute](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/customize-application-attributes), you need to ensure that the Verizon API supports filtering users based on that attribute. Select the **Save** button to commit any changes.
    | Attribute | Type | Supported for filtering | Required by Verizon |
    | --- | --- | --- | --- |
    | userName | String | ✓ | ✓ |
    | displayname | String |  |  |
    | active | Boolean |  |  |
    | urn:ietf:params:scim:schemas:extension:vzosnd:2.0:User:iccid | String |  | ✓ |
    | urn:ietf:params:scim:schemas:extension:vzosnd:2.0:User:profile | String |  | ✓ |
    | urn:ietf:params:scim:schemas:extension:vzosnd:2.0:User:imei | String |  |  |
    | urn:ietf:params:scim:schemas:extension:vzosnd:2.0:User:ipv4address | String |  |  |
12. Select **groups**.
13. Review the group attributes that are synchronized from Microsoft Entra ID to Verizon in the **Attribute-Mapping** section. The attributes selected as **Matching** properties are used to match the groups in Verizon for update operations. Select the **Save** button to commit any changes.
14. To configure scoping filters, refer to the following instructions provided in the [Scoping filter article](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts).
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

[Learn how to review logs and get reports on provisioning activity](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/check-status-user-account-provisioning)
