<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/smartsheet-provisioning-tutorial -->
<!-- Sitemap-Last-Modified: 2026-03-26 -->

# Configure Smartsheet for automatic user provisioning with Microsoft Entra ID

The objective of this article is to demonstrate the steps to be performed in Smartsheet and Microsoft Entra ID to configure Microsoft Entra ID to automatically provision and de-provision users and/or groups to [Smartsheet](https://www.smartsheet.com/pricing). For important details on what this service does, how it works, and frequently asked questions, see [Automate user provisioning and deprovisioning to SaaS applications with Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/user-provisioning).

## Capabilities supported

- Create users in Smartsheet
- Remove users in Smartsheet when they don't require access anymore
- Keep user attributes synchronized between Microsoft Entra ID and Smartsheet
- Single sign-on to Smartsheet \(recommended\)
- Long lived bearer token authentication supported.

## Prerequisites

The scenario outlined in this article assumes that you already have the following prerequisites:

- [A Microsoft Entra tenant](https://learn.microsoft.com/en-us/entra/identity-platform/quickstart-create-new-tenant).
- A user account in Microsoft Entra ID with [permission](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference) to configure provisioning \(like [Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#application-administrator), [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator), or [Application Owner](https://learn.microsoft.com/en-us/entra/fundamentals/users-default-permissions#owned-enterprise-applications)\).
- [A Smartsheet tenant](https://www.smartsheet.com/pricing).
- A user account on a Smartsheet Enterprise or Enterprise Premier plan with System Administrator permissions.
- **System Admins** and an **IT Administrator** can set up Active Directory with Smartsheet

## Step 1: Plan your provisioning deployment

1. Learn about [how the provisioning service works](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/user-provisioning).
2. Determine who's in [scope for provisioning](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts).
3. Determine what data to [map between Microsoft Entra ID and Smartsheet](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/customize-application-attributes).

## Step 2: Configure Smartsheet to support provisioning with Microsoft Entra ID

Before configuring Smartsheet for automatic user provisioning with Microsoft Entra ID, you need to enable SCIM provisioning on Smartsheet.

1. Sign in as a **System Admin** in the **[Smartsheet portal](https://app.smartsheet.com/b/home)** and navigate to **Account > Admin Center**.

   ![Screenshot of Smartsheet Account Admin](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/smartsheet-provisioning-tutorial/smartsheet-admin-center.png)

2. In the Admin Center page select the **Menu** option to expose the Menu panel.

   ![Screenshot of Smartsheet Security Controls](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/smartsheet-provisioning-tutorial/smartsheet-menu.png)

3. Navigate to **Menu > Settings > Domains & User Auto-Provisioning**.

   ![Screenshot of Smartsheet domain](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/smartsheet-provisioning-tutorial/smartsheet-domain.png)

4. To add a new domain select **Add Domain** and follow instructions. Once the domain is added make sure it gets verified as well.
5. Generate the **Secret Token** required to configure automatic user provisioning with Microsoft Entra ID by navigating **[Smartsheet portal](https://app.smartsheet.com/b/home)** and then navigating to **Account > Apps and Integrations**.
6. Choose **API Access**. Select **Generate new access token**.

   ![Screenshot of the Personal Settings dialog box with the API Access and Generate new access token options called out.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/smartsheet-provisioning-tutorial/smartsheet06.png)

7. Define the name of the API Access Token. Select **OK**.

   ![Screenshot of the Step 1 of 2: Generate API Access Token with the OK option called out.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/smartsheet-provisioning-tutorial/smartsheet07.png)

8. Copy the API Access Token and save it as it's the only time you can view it. This is required in the **Secret Token** field in Microsoft Entra ID.

   ![Smartsheet token](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/smartsheet-provisioning-tutorial/smartsheet08.png)

## Step 3: Add Smartsheet from the Microsoft Entra application gallery

Add Smartsheet from the Microsoft Entra application gallery to start managing provisioning to Smartsheet. If you have previously setup Smartsheet for SSO you can use the same application. However, we recommend that you create a separate app when testing out the integration initially. Learn more about adding an application from the gallery [here](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/add-application-portal).

## Step 4: Define who is in scope for provisioning

The Microsoft Entra provisioning service allows you to scope who is provisioned based on assignment to the application, or based on attributes of the user or group. If you choose to scope who is provisioned to your app based on assignment, you can use the [steps to assign users and groups to the application](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/assign-user-or-group-access-portal). If you choose to scope who is provisioned based solely on attributes of the user or group, you can [use a scoping filter](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts).

- Start small. Test with a small set of users and groups before rolling out to everyone. When scope for provisioning is set to assigned users and groups, you can control this by assigning one or two users or groups to the app. When scope is set to all users and groups, you can specify an [attribute based scoping filter](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts).
- If you need extra roles, you can [update the application manifest](https://learn.microsoft.com/en-us/entra/identity-platform/howto-add-app-roles-in-apps) to add new roles.

## Step 5: Configure automatic user provisioning to Smartsheet

This section guides you through the steps to configure the Microsoft Entra provisioning service to create, update, and disable users and/or groups in Smartsheet based on user and/or group assignments in Microsoft Entra ID.

### To configure automatic user provisioning for Smartsheet in Microsoft Entra ID:

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps**

   ![Screenshot of Enterprise applications blade.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/enterprise-applications.png)

3. In the applications list, select **Smartsheet**.

   ![Screenshot of The Smartsheet link in the Applications list.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/all-applications.png)

4. Select the **Provisioning** tab.

   ![Screenshot of the Manage options with the Provisioning option called out.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/provisioning.png)

5. Select **+ New configuration**.

   ![Screenshot of Provisioning tab automatic.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/application-provisioning.png)

6. In the **Tenant URL** field, input your Smartsheet Tenant URL and Secret Token. Select **Test Connection** to ensure Microsoft Entra ID can connect to Smartsheet. If the connection fails, ensure your Smartsheet account has the required admin permissions and try again.

   ![Screenshot of Provisioning test connection.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/provisioning-test-connection.png)

7. Select **Create** to create your configuration.
8. Select **Properties** on the **Overview** page.
9. Select the **Edit** icon to edit the properties. Enable notification emails and provide an email to receive quarantine emails. Enable accidental deletions prevention. Select **Apply** to save the changes.

   ![Screenshot of Provisioning properties.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/provisioning-properties.png)

10. Select **Attribute Mapping** in the left panel and select **users**.
11. Review the user attributes that are synchronized from Microsoft Entra ID to Smartsheet in the **Attribute Mapping** section. The attributes selected as **Matching** properties are used to match the user accounts in Smartsheet for update operations. Select the **Save** button to commit any changes.
    | Attribute | Type | Supported for filtering |
    | --- | --- | --- |
    | userName | String | ✓ |
    | active | Boolean |  |
    | title | String |  |
    | name.givenName | String |  |
    | name.familyName | String |  |
    | phoneNumbers\[type eq "work"\].value | String |  |
    | phoneNumbers\[type eq "mobile"\].value | String |  |
    | phoneNumbers\[type eq "fax"\].value | String |  |
    | emails\[type eq "work"\].value | String |  |
    | externalId | String |  |
    | roles | String |  |
    | urn:ietf:params:scim:schemas:extension:enterprise:2.0:User:department | String |  |
    | urn:ietf:params:scim:schemas:extension:enterprise:2.0:User:division | String |  |
    | urn:ietf:params:scim:schemas:extension:enterprise:2.0:User:costCenter | String |  |
    | urn:ietf:params:scim:schemas:extension:enterprise:2.0:User:manager | String |  |
12. To configure scoping filters, refer to the following instructions provided in the [Scoping filter article](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts).
13. Use [on-demand provisioning](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/provision-on-demand) to validate sync with a small number of users before deploying more broadly in your organization.
14. When you're ready to provision, select **Start Provisioning** from the **Overview** page.

## Step 6: Monitor your deployment

Once you configure provisioning, use the following resources to monitor your deployment:

1. Use the [provisioning logs](https://learn.microsoft.com/en-us/entra/identity/monitoring-health/concept-provisioning-logs) to determine which users are provisioned successfully or unsuccessfully
2. Check the [progress bar](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/application-provisioning-when-will-provisioning-finish-specific-user) to see the status of the provisioning cycle and how close it's to completion
3. If the provisioning configuration seems to be in an unhealthy state, the application goes into quarantine. Learn more about quarantine states the [application provisioning quarantine status](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/application-provisioning-quarantine-status) article.

## Connector limitations

- Smartsheet doesn't support soft-deletes. When a user's **active** attribute is set to False, Smartsheet deletes the user permanently.

## Change log

- 06/16/2020 - Added support for enterprise extension attributes "Cost Center", "Division", "Manager" and "Department" for users.
- 02/10/2021 - Added support for core attributes "emails\[type eq "work"\]" for users.
- 02/12/2022 - Added SCIM base/tenant URL of `https://scim.smartsheet.com/v2` for SmartSheet integration under Admin Credentials section.

## Additional resources

- [Managing user account provisioning for Enterprise Apps](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/configure-automatic-user-provisioning-portal)
- [What is application access and single sign-on with Microsoft Entra ID?](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/what-is-single-sign-on)

## Related content

- [Learn how to review logs and get reports on provisioning activity](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/check-status-user-account-provisioning)
