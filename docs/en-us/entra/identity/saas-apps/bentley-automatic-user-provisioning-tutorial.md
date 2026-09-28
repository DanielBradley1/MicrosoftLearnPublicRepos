<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/bentley-automatic-user-provisioning-tutorial -->
<!-- Sitemap-Last-Modified: 2026-02-24 -->

# Configure Bentley - Automatic User Provisioning for automatic user provisioning with Microsoft Entra ID

This article describes the steps you need to perform in both Bentley - Automatic User Provisioning and Microsoft Entra ID to configure automatic user provisioning. When configured, Microsoft Entra ID automatically provisions and de-provisions users and groups to [Bentley - Automatic User Provisioning](https://www.bentley.com) using the Microsoft Entra provisioning service. For important details on what this service does, how it works, and frequently asked questions, see [Automate user provisioning and deprovisioning to SaaS applications with Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/user-provisioning).

## Capabilities supported

- Create users in Bentley - Automatic User Provisioning
- Remove users in Bentley - Automatic User Provisioning when they don't require access anymore
- Keep user attributes synchronized between Microsoft Entra ID and Bentley - Automatic User Provisioning
- Provision groups and group memberships in Bentley - Automatic User Provisioning
- Long lived bearer token authentication supported.

## Prerequisites

The scenario outlined in this article assumes that you already have the following prerequisites:

- A Microsoft Entra user account with an active subscription. If you don't already have one, you can [Create an account for free](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
- One of the following roles:

  - [Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#application-administrator)
  - [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator)
  - [Application Owner](https://learn.microsoft.com/en-us/entra/fundamentals/users-default-permissions#owned-enterprise-applications).

- A Federated account with Bentley IMS.

## Step 1: Plan your provisioning deployment

1. Learn about [how the provisioning service works](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/user-provisioning).
2. Determine who's in [scope for provisioning](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts).
3. Determine what data to [map between Microsoft Entra ID and Bentley - Automatic User Provisioning](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/customize-application-attributes).

## Step 2: Configure Bentley - Automatic User Provisioning to support provisioning with Microsoft Entra ID

Reach out to the Bentley User Provisioning [support](https://communities.bentley.com/communities/other_communities/licensing_cloud_and_web_services/w/wiki/52836/microsoft-azure-ad-automatic-user-provisioning-configuration) team for Tenant URL and Secret Token. These values are entered in the Provisioning tab of the Bentley application.

## Step 3: Add Bentley - Automatic User Provisioning from the Microsoft Entra application gallery

Add Bentley - Automatic User Provisioning from the Microsoft Entra application gallery to start managing provisioning to Bentley - Automatic User Provisioning. Learn more about adding an application from the gallery [here](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/add-application-portal).

## Step 4: Define who is in scope for provisioning

The Microsoft Entra provisioning service allows you to scope who is provisioned based on assignment to the application, or based on attributes of the user or group. If you choose to scope who is provisioned to your app based on assignment, you can use the [steps to assign users and groups to the application](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/assign-user-or-group-access-portal). If you choose to scope who is provisioned based solely on attributes of the user or group, you can [use a scoping filter](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts).

- Start small. Test with a small set of users and groups before rolling out to everyone. When scope for provisioning is set to assigned users and groups, you can control this by assigning one or two users or groups to the app. When scope is set to all users and groups, you can specify an [attribute based scoping filter](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts).
- If you need extra roles, you can [update the application manifest](https://learn.microsoft.com/en-us/entra/identity-platform/howto-add-app-roles-in-apps) to add new roles.

## Step 5: Configure automatic user provisioning to Bentley - Automatic User Provisioning

This section guides you through the steps to configure the Microsoft Entra provisioning service to create, update, and disable users and/or groups in TestApp based on user and/or group assignments in Microsoft Entra ID.

### To configure automatic user provisioning for Bentley - Automatic User Provisioning in Microsoft Entra ID:

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps**

   ![Enterprise applications blade](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/enterprise-applications.png)

3. In the applications list, select **Bentley - Automatic User Provisioning**.

   ![The Bentley - Automatic User Provisioning link in the Applications list](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/all-applications.png)

4. Select the **Provisioning** tab.

   ![Provisioning tab](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/provisioning.png)

5. Set **+ New configuration**.

   ![Screenshot of Provisioning tab automatic.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/application-provisioning.png)

6. In the **Tenant URL** field, input your Bentley - Automatic User Provisioning Tenant URL and Secret Token. Select **Test Connection** to ensure Microsoft Entra ID can connect to Bentley - Automatic User Provisioning. If the connection fails, ensure your Bentley - Automatic User Provisioning account has the required admin permissions and try again.

   ![Screenshot of Provisioning test connection.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/provisioning-test-connection.png)

7. Select **Create** to create your configuration.
8. Select **Properties** in the **Overview** page.
9. Select the pencil to edit the properties. Enable notification emails and provide an email to receive quarantine emails. Enable accidental deletions prevention. Select **Apply** to save the changes.

   ![Screenshot of Provisioning properties.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/provisioning-properties.png)

10. Select **Attribute Mapping** in the left panel and select users.
11. Review the user attributes that are synchronized from Microsoft Entra ID to Bentley - Automatic User Provisioning in the **Attribute-Mapping** section. The attributes selected as **Matching** properties are used to match the user accounts in Bentley - Automatic User Provisioning for update operations. If you choose to change the [matching target attribute](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/customize-application-attributes), you need to ensure that the Bentley - Automatic User Provisioning API supports filtering users based on that attribute. Select the **Save** button to commit any changes.
    | Attribute | Type | Supported for Filtering |
    | --- | --- | --- |
    | userName | String | ✓ |
    | title | String |  |
    | emails\[type eq "work"\].value | String |  |
    | preferredLanguage | String |  |
    | name.givenName | String |  |
    | name.familyName | String |  |
    | addresses\[type eq "work"\].streetAddress | String |  |
    | addresses\[type eq "work"\].locality | String |  |
    | addresses\[type eq "work"\].region | String |  |
    | addresses\[type eq "work"\].postalCode | String |  |
    | addresses\[type eq "work"\].country | String |  |
    | phoneNumbers\[type eq "work"\].value | String |  |
    | externalId | String |  |
    | urn:ietf:params:scim:schemas:extension:Bentley:2.0:User:isSoftDeleted | String |  |
12. Select **Groups**.
13. Review the group attributes that are synchronized from Microsoft Entra ID to Bentley - Automatic User Provisioning in the **Attribute-Mapping** section. The attributes selected as **Matching** properties are used to match the groups in Bentley - Automatic User Provisioning for update operations. Select the **Save** button to commit any changes.
    | Attribute | Type | Supported for Filtering |
    | --- | --- | --- |
    | displayName | String | ✓ |
    | externalId | String |  |
    | members | Reference |  |
    | urn:ietf:params:scim:schemas:extension:Bentley:2.0:Group:description | String |  |
14. To configure scoping filters, refer to the following instructions provided in the [Scoping filter article](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts) article.
15. Use [on-demand provisioning](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/provision-on-demand) to validate sync with a small number of users before deploying more broadly in your organization.
16. When you're ready to provision, select **Start Provisioning** from the **Overview** page.

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
