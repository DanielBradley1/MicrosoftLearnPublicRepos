<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/schoolstream-asa-provisioning-tutorial -->
<!-- Sitemap-Last-Modified: 2026-03-26 -->

# Configure SchoolStream ASA for automatic user provisioning with Microsoft Entra ID

This article describes the steps you need to perform in both SchoolStream ASA and Microsoft Entra ID to configure automatic user provisioning. When configured, Microsoft Entra ID automatically provisions and de-provisions users and groups to [SchoolStream ASA](https://www.ssk12.com/) using the Microsoft Entra provisioning service. For important details on what this service does, how it works, and frequently asked questions, see [Automate user provisioning and deprovisioning to SaaS applications with Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/user-provisioning).

## Capabilities Supported

- Create users in SchoolStream ASA
- Remove users in SchoolStream ASA when they don't require access anymore.
- Keep user attributes synchronized between Microsoft Entra ID and SchoolStream ASA.
- Provision groups and group memberships in SchoolStream ASA.
- [Single sign-on](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/add-application-portal-setup-oidc-sso) to SchoolStream ASA \(recommended\).
- Long lived bearer token authentication supported.

## Prerequisites

The scenario outlined in this article assumes that you already have the following prerequisites:

- A Microsoft Entra user account with an active subscription. If you don't already have one, you can [Create an account for free](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
- One of the following roles:

  - [Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#application-administrator)
  - [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator)
  - [Application Owner](https://learn.microsoft.com/en-us/entra/fundamentals/users-default-permissions#owned-enterprise-applications).

- A SchoolStream Website. Please contact [SchoolStream support](mailto:support@rtresponse.com) if you don't have one.

## Step 1: Plan your provisioning deployment

1. Learn about [how the provisioning service works](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/user-provisioning).
2. Determine who's in [scope for provisioning](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts).
3. Determine what data to [map between Microsoft Entra ID and SchoolStream ASA](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/customize-application-attributes).

## Step 2: Configure SchoolStream ASA to support provisioning with Microsoft Entra ID

1. Contact [SchoolStream support](mailto:support@rtresponse.com) to request SchoolStream ASA integration, you need to provide your **Microsoft Entra tenant Id** and your **SchoolStream Website URL**.
2. You get your **Secret Token** and SchoolStream ASA **Tenant URL** after SchoolStream has mapped your SchoolStream Website and Microsoft Entra tenant ID.

## Step 3: Add SchoolStream ASA from the Microsoft Entra application gallery

To start managing provisioning to SchoolStream ASA in your Microsoft Entra ID, you need to add SchoolStream ASA from the Microsoft Entra application gallery.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **New application**.
3. In the **Browse Microsoft Entra Gallery** section, type **SchoolStream ASA** in the search box.
4. Select **SchoolStream ASA** from results panel and then **Sign up for the app**. Wait a few seconds while the app is added to your tenant.

If you have previously setup SchoolStream ASA for SSO you can use the same application. However, we recommend that you create a separate app when testing out the integration initially. Learn more about adding an application from the gallery [here](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/add-application-portal).

## Step 4: Define who is in scope for provisioning

The Microsoft Entra provisioning service allows you to scope who is provisioned based on assignment to the application, or based on attributes of the user or group. If you choose to scope who is provisioned to your app based on assignment, you can use the [steps to assign users and groups to the application](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/assign-user-or-group-access-portal). If you choose to scope who is provisioned based solely on attributes of the user or group, you can [use a scoping filter](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts).

- Start small. Test with a small set of users and groups before rolling out to everyone. When scope for provisioning is set to assigned users and groups, you can control this by assigning one or two users or groups to the app. When scope is set to all users and groups, you can specify an [attribute based scoping filter](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts).
- If you need extra roles, you can [update the application manifest](https://learn.microsoft.com/en-us/entra/identity-platform/howto-add-app-roles-in-apps) to add new roles.

## Step 5: Configure automatic user provisioning to SchoolStream ASA

This section guides you through the steps to configure the Microsoft Entra provisioning service to create, update, and disable users and/or groups in SchoolStream ASA based on user and/or group assignments in Microsoft Entra ID.

### To configure automatic user provisioning for SchoolStream ASA in Microsoft Entra ID:

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps**

   ![Enterprise applications blade](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/enterprise-applications.png)

3. In the applications list, select **SchoolStream ASA**.

   ![The SchoolStream ASA link in the Applications list](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/all-applications.png)

4. Select the **Provisioning** tab.

   ![Provisioning tab](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/provisioning.png)

5. If you're configuring provisioning for the first time, select **Get started**.
6. Select **+ New configuration**.

   ![Screenshot of Provisioning tab automatic.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/application-provisioning.png)

7. In the **Tenant URL** field, input your SchoolStream ASA Tenant URL and Secret Token. Select **Test Connection** to ensure Microsoft Entra ID can connect to SchoolStream ASA. If the connection fails, ensure your SchoolStream ASA account has the required admin permissions and try again.

   ![Screenshot of Provisioning test connection.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/provisioning-test-connection.png)

8. Select **Create** to create your configuration.
9. Select **Properties** on the **Overview** page.
10. Select the **Edit** icon to edit the properties. Enable notification emails and provide an email to receive quarantine emails. Enable accidental deletions prevention. Select **Apply** to save the changes.

    ![Screenshot of Provisioning properties.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/provisioning-properties.png)

11. In the **Mappings** section, select **Provision Microsoft Entra users**.
12. Select **Add New Mapping** at the bottom.
13. In the dialog **Edit Attribute**:

    - In the **Mapping type** field, select **Direct** from the dropdown,
    - In the **Source attribute** field, select **extensionAttribute1** from the dropdown,
    - Enter your **Microsoft Entra tenant Id** in the field **Default value if null\(optional\)**,
    - In the **Target attribute** field, select **urn:ietf:params:scim:schemas:extension:enterprise:2.0:User:organization** from the dropdown,
    - In the **Match objects using this attribute** field, select **No** from the dropdown,
    - In the **Apply this mapping** field, select **Always** from the dropdown,
    - Select **OK**.

      ![Edit Attribute](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/schoolstream-asa-provisioning-tutorial/add-mappings-attribute.png)

14. Review the user attributes that are synchronized from Microsoft Entra ID to SchoolStream ASA in the **Attribute-Mapping** section. The attributes selected as **Matching** properties are used to match the user accounts in SchoolStream ASA for update operations. If you choose to change the [matching target attribute](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/customize-application-attributes), you need to ensure that the SchoolStream ASA API supports filtering users based on that attribute.
    | Attribute | Type | Supported for filtering |
    | --- | --- | --- |
    | userName | String | ✓ |
    | active | Boolean |  |
    | displayName | String |  |
    | emails\[type eq "work"\].value | String |  |
    | preferredLanguage | String |  |
    | name.givenName | String |  |
    | name.familyName | String |  |
    | name.formatted | String |  |
    | phoneNumbers\[type eq "mobile"\].value | String |  |
    | externalId | String |  |
    | urn:ietf:params:scim:schemas:extension:enterprise:2.0:User:organization | String |  |
15. Select **Groups**.
16. Review the group attributes that are synchronized from Microsoft Entra ID to SchoolStream ASA in the **Attribute-Mapping** section. The attributes selected as **Matching** properties are used to match the groups in SchoolStream ASA for update operations. Select the **Save** button to commit any changes.
    | Attribute | Type | Supported for filtering |
    | --- | --- | --- |
    | displayName | String | ✓ |
    | members | Reference |  |
    | externalId | String |  |
17. Select the **Save** button to commit any changes. You can go back to the **Application** tab and select **Edit provisioning** to continue.
18. To configure scoping filters, refer to the following instructions provided in the [Scoping filter article](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts).
19. Use [on-demand provisioning](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/provision-on-demand) to validate sync with a small number of users before deploying more broadly in your organization.
20. When you're ready to provision, select **Start Provisioning** from the **Overview** page.

## Step 6: Monitor your deployment

Once you configure provisioning, use the following resources to monitor your deployment:

1. Use the [provisioning logs](https://learn.microsoft.com/en-us/entra/identity/monitoring-health/concept-provisioning-logs) to determine which users are provisioned successfully or unsuccessfully
2. Check the [progress bar](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/application-provisioning-when-will-provisioning-finish-specific-user) to see the status of the provisioning cycle and how close it's to completion
3. If the provisioning configuration seems to be in an unhealthy state, the application goes into quarantine. Learn more about quarantine states the [application provisioning quarantine status](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/application-provisioning-quarantine-status) article.

## Change log

- 09/24/2020 - Group provisioning got enabled.

## More resources

- [Managing user account provisioning for Enterprise Apps](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/configure-automatic-user-provisioning-portal)
- [What is application access and single sign-on with Microsoft Entra ID?](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/what-is-single-sign-on)

## Related content

- [Learn how to review logs and get reports on provisioning activity](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/check-status-user-account-provisioning)
