<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/twingate-provisioning-tutorial -->
<!-- Sitemap-Last-Modified: 2026-03-31 -->

# Configure Twingate for automatic user provisioning with Microsoft Entra ID

This article describes the steps you need to perform in both Twingate and Microsoft Entra ID to configure automatic user provisioning. When configured, Microsoft Entra ID automatically provisions and de-provisions users and groups to [Twingate](https://www.twingate.com/) using the Microsoft Entra provisioning service. For important details on what this service does, how it works, and frequently asked questions, see [Automate user provisioning and deprovisioning to SaaS applications with Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/user-provisioning).

## Capabilities Supported

- Create users in Twingate
- Remove users in Twingate when they don't require access anymore
- Keep user attributes synchronized between Microsoft Entra ID and Twingate
- Provision groups and group memberships in Twingate
- Single sign-on to Twingate \(recommended\)
- Long lived bearer token authentication supported.

## Prerequisites

The scenario outlined in this article assumes that you already have the following prerequisites:

- [A Microsoft Entra tenant](https://learn.microsoft.com/en-us/entra/identity-platform/quickstart-create-new-tenant)
- One of the following roles: [Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#application-administrator), [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator), or [Application Owner](https://learn.microsoft.com/en-us/entra/fundamentals/users-default-permissions#owned-enterprise-applications).
- A Twingate tenant in a product tier that supports identity provider integration. See [Twingate pricing](https://www.twingate.com/pricing/) for details on different product tiers.
- A user account in Twingate with Admin permissions.

## Step 1: Plan your provisioning deployment

1. Learn about [how the provisioning service works](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/user-provisioning).
2. Determine who's in [scope for provisioning](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts).
3. Determine what data to [map between Microsoft Entra ID and Twingate](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/customize-application-attributes).

## Step 2: Configure Twingate to support provisioning with Microsoft Entra ID

1. Sign in to your [Twingate Admin Console](https://auth.twingate.com/).
2. Navigate to **Settings > Identity Provider**
3. Select the `...` button to open the action menu. Select **Regenerate SCIM Token**. Note that this would invalidate your existing token if any.

   ![Screenshot of Microsoft Entra action menu.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/twingate-provisioning-tutorial/token.png)

4. Copy the **SCIM Endpoint** and **SCIM token** from the modal. These values are entered in the **Tenant URL** and **Secret Token** fields respectively in the Provisioning tab of your Twingate application.

   ![Screenshot of SCIM info modal.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/twingate-provisioning-tutorial/tenant.png)

## Step 3: Add Twingate from the Microsoft Entra application gallery

Add Twingate from the Microsoft Entra application gallery to start managing provisioning to Twingate. If you have previously setup Twingate for SSO, you can use the same application. However, we recommend that you create a separate app when testing out the integration initially. Learn more about adding an application from the gallery [here](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/add-application-portal).

## Step 4: Define who is in scope for provisioning

The Microsoft Entra provisioning service allows you to scope who is provisioned based on assignment to the application, or based on attributes of the user or group. If you choose to scope who is provisioned to your app based on assignment, you can use the [steps to assign users and groups to the application](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/assign-user-or-group-access-portal). If you choose to scope who is provisioned based solely on attributes of the user or group, you can [use a scoping filter](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts).

- Start small. Test with a small set of users and groups before rolling out to everyone. When scope for provisioning is set to assigned users and groups, you can control this by assigning one or two users or groups to the app. When scope is set to all users and groups, you can specify an [attribute based scoping filter](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts).
- If you need extra roles, you can [update the application manifest](https://learn.microsoft.com/en-us/entra/identity-platform/howto-add-app-roles-in-apps) to add new roles.

## Step 5: Configure automatic user provisioning to Twingate

This section guides you through the steps to configure the Microsoft Entra provisioning service to create, update, and disable users and/or groups in Twingate based on user and/or group assignments in Microsoft Entra ID.

### To configure automatic user provisioning for Twingate in Microsoft Entra ID:

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps**

   ![Screenshot of Enterprise applications blade.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/enterprise-applications.png)

3. In the applications list, select **Twingate**.

   ![Screenshot of The Twingate link in the Applications list.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/all-applications.png)

4. Select the **Provisioning** tab.

   ![Screenshot of Provisioning tab.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/provisioning.png)

5. Select **+ New configuration**.

   ![Screenshot of Provisioning tab automatic.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/application-provisioning.png)

6. In the **Tenant URL** field, input your Twingate Tenant URL and Secret Token. Select **Test Connection** to ensure Microsoft Entra ID can connect to Twingate. If the connection fails, ensure your Twingate account has the required admin permissions and try again.

   ![Screenshot of Provisioning test connection.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/provisioning-test-connection.png)

7. Select **Create** to create your configuration.
8. Select **Properties** on the **Overview** page.
9. Select the **Edit** icon to edit the properties. Enable notification emails and provide an email to receive quarantine notifications. Enable **Accidental deletions prevention**. Select **Apply** to save the changes.

   ![Screenshot of Provisioning properties.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/provisioning-properties.png)

10. Select **Attribute Mapping** in the left panel and select **users**.
11. Review the user attributes that are synchronized from Microsoft Entra ID to Twingate in the **Attribute-Mapping** section. The attributes selected as **Matching** properties are used to match the user accounts in Twingate for update operations. If you choose to change the [matching target attribute](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/customize-application-attributes), you need to ensure that the Twingate API supports filtering users based on that attribute. Select the **Save** button to commit any changes.
    | Attribute | Type | Supported For Filtering |
    | --- | --- | --- |
    | externalId | String | ✓ |
    | userName | String |  |
    | active | Boolean |  |
    | emails\[type eq "work"\].value | String |  |
    | name.givenName | String |  |
    | name.familyName | String |  |
12. Select **Groups**.
13. Review the group attributes that are synchronized from Microsoft Entra ID to Twingate in the **Attribute-Mapping** section. The attributes selected as **Matching** properties are used to match the groups in Twingate for update operations. Select the **Save** button to commit any changes.
    | Attribute | Type | Supported For Filtering |
    | --- | --- | --- |
    | externalId | String | ✓ |
    | displayName | String |  |
    | members | Reference |  |
14. To configure scoping filters, refer to the instructions provided in the [Scoping filter article](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts).
15. Use [on-demand provisioning](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/provision-on-demand) to validate sync with a small number of users before deploying more broadly in your organization.
16. When you're ready to provision, select **Start Provisioning** from the **Overview** page.

## Step 6: Change Assignment required setting

The default setting is **No** which allows users to log into Twingate without being assigned in the enterprise application.

1. Select **Properties**.

   ![Screenshot of Properties.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/properties.png)

2. Set **Assignment required** to **Yes**

   ![Screenshot of Properties assignment.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/twingate-provisioning-tutorial/properties-assignment-required.png)

3. Select **Save**

   ![Screenshot of Properties saved.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/twingate-provisioning-tutorial/properties-save.png)

## Step 7: Monitor your deployment

Once you've configured provisioning, use the following resources to monitor your deployment:

1. Use the [provisioning logs](https://learn.microsoft.com/en-us/entra/identity/monitoring-health/concept-provisioning-logs) to determine which users have been provisioned successfully or unsuccessfully
2. Check the [progress bar](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/application-provisioning-when-will-provisioning-finish-specific-user) to see the status of the provisioning cycle and how close it's to completion
3. If the provisioning configuration seems to be in an unhealthy state, the application will go into quarantine. Learn more about quarantine states [here](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/application-provisioning-quarantine-status).

## Additional resources

- [Managing user account provisioning for Enterprise Apps](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/configure-automatic-user-provisioning-portal)
- [What is application access and single sign-on with Microsoft Entra ID?](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/what-is-single-sign-on)

## Related content

- [Learn how to review logs and get reports on provisioning activity](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/check-status-user-account-provisioning)
