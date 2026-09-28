<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/slack-provisioning-tutorial -->
<!-- Sitemap-Last-Modified: 2026-06-19 -->

# Automate User provisioning into Slack with Microsoft Entra ID

Note

Integrating with Slack with a custom / BYOA application isn't supported. Using the gallery application as described in this article is supported. The gallery application has been customized to work with Slack's SCIM v1 server.

The objective of this article is to show you the steps you need to perform in Slack and Microsoft Entra ID to automatically provision and deprovision user accounts from Microsoft Entra ID to Slack. For important details on what this service does, how it works, and frequently asked questions, see [Automate user provisioning and deprovisioning to SaaS applications with Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/user-provisioning).

## Capabilities supported

- Create users in Slack
- Remove users in Slack when they don't require access anymore
- Keep user attributes synchronized between Microsoft Entra ID and Slack
- Provision groups and group memberships in Slack
- [Single sign-on](https://learn.microsoft.com/en-us/entra/identity/saas-apps/slack-tutorial) to Slack \(recommended\)

Slack is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government | China operated by 21Vianet |
| :---: | :---: | :---: |
| ✅ | ✅ |  |

## Prerequisites

The scenario outlined in this article assumes that you already have the following items:

- [A Microsoft Entra tenant](https://learn.microsoft.com/en-us/entra/identity-platform/quickstart-create-new-tenant).
- One of the following roles: [Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#application-administrator), [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator), or [Application Owner](https://learn.microsoft.com/en-us/entra/fundamentals/users-default-permissions#owned-enterprise-applications).
- A Slack tenant with the [Business+ plan](https://slack.com/pricing) only. Enteprise Grid customers should follow [Slack's instructions](https://api.slack.com/admins/scim#enterprise-grid) instead.
- A user account in Slack with Team Admin permissions.

## Step 1: Plan your provisioning deployment

1. Learn about [how the provisioning service works](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/user-provisioning).
2. Determine who's in [scope for provisioning](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts).
3. Determine what data to [map between Microsoft Entra ID and Slack](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/customize-application-attributes).

## Step 2: Add Slack from the Microsoft Entra application gallery

Add Slack from the Microsoft Entra application gallery to start managing provisioning to Slack. If you have previously setup Slack for SSO, you can use the same application. However, we recommend that you create a separate app when testing out the integration initially. Learn more about adding an application from the gallery [here](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/add-application-portal).

## Step 3: Define who is in scope for provisioning

The Microsoft Entra provisioning service allows you to scope who is provisioned based on assignment to the application, or based on attributes of the user or group. If you choose to scope who is provisioned to your app based on assignment, you can use the [steps to assign users and groups to the application](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/assign-user-or-group-access-portal). If you choose to scope who is provisioned based solely on attributes of the user or group, you can [use a scoping filter](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts).

- Start small. Test with a small set of users and groups before rolling out to everyone. When scope for provisioning is set to assigned users and groups, you can control this by assigning one or two users or groups to the app. When scope is set to all users and groups, you can specify an [attribute based scoping filter](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts).
- If you need extra roles, you can [update the application manifest](https://learn.microsoft.com/en-us/entra/identity-platform/howto-add-app-roles-in-apps) to add new roles.

## Step 4: Configure automatic user provisioning to Slack

This section guides you through connecting your Microsoft Entra ID to Slack's user account provisioning API, and configuring the provisioning service to create, update, and disable assigned user accounts in Slack based on user and group assignment in Microsoft Entra ID.

### To configure automatic user account provisioning to Slack in Microsoft Entra ID:

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps**

   ![Enterprise applications blade](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/enterprise-applications.png)

3. In the applications list, select **Slack**.

   ![Screenshot of the Slack link in the Applications list.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/all-applications.png)

4. Select the **Provisioning** tab.

   ![Screenshot of the Manage options with the Provisioning option called out.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/provisioning.png)

5. Select **+ New configuration**.

   ![Screenshot of Provisioning tab automatic.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/application-provisioning.png)

6. In the **Tenant URL** field, enter your Slack Tenant URL and Secret Token. Select **Test Connection** to ensure Microsoft Entra ID can connect to Slack. If the connection fails, ensure your Slack account has the required admin permissions and try again.

   ![Screenshot of Provisioning test connection.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/provisioning-test-connection.png)

7. In the new window, sign into Slack using your Team Admin account. In the resulting authorization dialog, select the Slack team that you want to enable provisioning for, and then select **Authorize**. Once completed, return to the Microsoft Entra admin center to complete the provisioning configuration.

   ![Authorization Dialog](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/slack-provisioning-tutorial/slackauthorize.png)

8. Select **Create** to create your configuration.
9. Select **Properties** on the **Overview** page.
10. In the **Notification Email** field, enter the email address of a person who should receive the provisioning error notifications and select the **Send an email notification when a failure occurs** check box.

    ![Screenshot of the Provisioning properties page showing notification and deletion settings.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/provisioning-properties.png)

11. Select **Attribute Mapping** in the left panel and select **users**.
12. Review the user attributes that are synchronized from Microsoft Entra ID to Slack in the **Attribute-Mapping** section. The attributes selected as **Matching** properties are used to match the user accounts in Slack for update operations. If you choose to change the [matching target attribute](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/customize-application-attributes), you need to ensure that the Slack API supports filtering users based on that attribute. Select the **Save** button to commit any changes.
    | Attribute | Type |
    | --- | --- |
    | active | Boolean |
    | externalId | String |
    | displayName | String |
    | name.familyName | String |
    | name.givenName | String |
    | title | String |
    | emails\[type eq "work"\].value | String |
    | userName | String |
    | nickName | String |
    | addresses\[type eq "untyped"\].streetAddress | String |
    | addresses\[type eq "untyped"\].locality | String |
    | addresses\[type eq "untyped"\].region | String |
    | addresses\[type eq "untyped"\].postalCode | String |
    | addresses\[type eq "untyped"\].country | String |
    | phoneNumbers\[type eq "mobile"\].value | String |
    | phoneNumbers\[type eq "work"\].value | String |
    | roles\[primary eq "True"\].value | String |
    | locale | String |
    | name.honorificPrefix | String |
    | photos\[type eq "photo"\].value | String |
    | profileUrl | String |
    | timezone | String |
    | userType | String |
    | preferredLanguage | String |
    | urn:scim:schemas:extension:enterprise:1.0.department | String |
    | urn:scim:schemas:extension:enterprise:1.0.manager | Reference |
    | urn:scim:schemas:extension:enterprise:1.0.employeeNumber | String |
    | urn:scim:schemas:extension:enterprise:1.0.costCenter | String |
    | urn:scim:schemas:extension:enterprise:1.0.organization | String |
    | urn:scim:schemas:extension:enterprise:1.0.division | String |
13. In the **Attribute Mappings** section, review the group attributes synchronized from Microsoft Entra ID to Slack. The attributes selected as **Matching** properties are used to match the groups in Slack for update operations. Select the Save button to commit any changes.
    | Attribute | Type |
    | --- | --- |
    | displayName | String |
    | members | Reference |
14. To configure scoping filters, refer to the instructions provided in the [Scoping filter article](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts).
15. Use [on-demand provisioning](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/provision-on-demand) to validate sync with a few users before deploying more broadly in your organization.
16. When you're ready to provision, select **Start Provisioning** from the **Overview** page.

## Step 5: Monitor your deployment

Once you configure provisioning, use the following resources to monitor your deployment:

1. Use the [provisioning logs](https://learn.microsoft.com/en-us/entra/identity/monitoring-health/concept-provisioning-logs) to determine which users are provisioned successfully or unsuccessfully
2. Check the [progress bar](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/application-provisioning-when-will-provisioning-finish-specific-user) to see the status of the provisioning cycle and how close it's to completion
3. If the provisioning configuration seems to be in an unhealthy state, the application goes into quarantine. Learn more about quarantine states the [application provisioning quarantine status](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/application-provisioning-quarantine-status) article.

## Troubleshooting Tips

- When configuring Slack's **displayName** attribute, be aware of the following behaviors:

  - Values aren't entirely unique \(such as two users can have the same display name\)
  - Supports non-English characters, spaces, capitalization.
  - Allowed punctuation includes periods, underscores, hyphens, apostrophes, brackets \(for example, `( [ { } ] )`\), and separators \(for example, `, / ;`\).
  - displayName property can't have an '@' character. If an '@' is included, you might find a skipped event in the provisioning logs with the description "AttributeValidationFailed."
  - Only updates if these two settings are configured in Slack's workplace/organization - **Profile syncing is enabled** and **Users can't change their display name**.

- Slack's **userName** attribute has to be under 21 characters and have a unique value.
- Slack only allows matching with the attributes **userName** and **email**.
- Common error codes are documented in the official Slack documentation - [https://api.slack.com/scim#errors](https://api.slack.com/scim#errors)

## Change log

- 06/16/2020 - Modified DisplayName attribute to only be updated during new user creation.

## More Resources

- [Managing user account provisioning for Enterprise Apps](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/configure-automatic-user-provisioning-portal)
- [What is application access and single sign-on with Microsoft Entra ID?](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/what-is-single-sign-on)

## Related content

- [Learn how to review logs and get reports on provisioning activity](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/check-status-user-account-provisioning)
