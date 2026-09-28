<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/samanage-provisioning-tutorial -->
<!-- Sitemap-Last-Modified: 2026-03-26 -->

# Configure SolarWinds Service Desk \(previously Samanage\) for automatic user provisioning with Microsoft Entra ID

This article describes the steps you need to perform in both SolarWinds Service Desk \(previously Samanage\) and Microsoft Entra ID to configure automatic user provisioning. When configured, Microsoft Entra ID automatically provisions and de-provisions users and groups to [SolarWinds Service Desk](https://www.samanage.com/pricing/) using the Microsoft Entra provisioning service. For important details on what this service does, how it works, and frequently asked questions, see [Automate user provisioning and deprovisioning to SaaS applications with Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/user-provisioning).

## Migrate to the new SolarWinds Service Desk application

If you have an existing integration with SolarWinds Service Desk, see the following section about upcoming changes. If you're setting up SolarWinds Service Desk for the first time, you can skip this section and move to **Capabilities supported**.

#### What's changing?

- Changes on the Microsoft Entra ID side: The authorization method to provision users in Samange has historically been **Basic auth**. Soon you see the authorization method changed to **Long lived secret token**.

#### What do I need to do to migrate my existing custom integration to the new application?

If you have an existing SolarWinds Service Desk integration with valid admin credentials, **no action is required**. We automatically migrate customers to the new application. This process is done completely behind the scenes. If the existing credentials expire, or if you need to authorize access to the application again, you need to generate a long-lived secret token. To generate a new token, refer to Step 2 of this article.

#### How can I tell if my application has been migrated?

When your application is migrated, in the **Admin Credentials** section, the **Admin Username** and **Admin Password** fields are replaced with a single **Secret Token** field.

## Capabilities supported

- Create users in SolarWinds Service Desk
- Remove users in SolarWinds Service Desk when they don't require access anymore
- Keep user attributes synchronized between Microsoft Entra ID and SolarWinds Service Desk
- Provision groups and group memberships in SolarWinds Service Desk
- [Single sign-on](https://learn.microsoft.com/en-us/entra/identity/saas-apps/samanage-tutorial) to SolarWinds Service Desk \(recommended\)

## Prerequisites

The scenario outlined in this article assumes that you already have the following prerequisites:

- A Microsoft Entra user account with an active subscription. If you don't already have one, you can [Create an account for free](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
- One of the following roles:

  - [Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#application-administrator)
  - [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator)
  - [Application Owner](https://learn.microsoft.com/en-us/entra/fundamentals/users-default-permissions#owned-enterprise-applications).

- A [SolarWinds Service Desk tenant](https://www.samanage.com/pricing/) with the Professional package.
- A user account in SolarWinds Service Desk with admin permissions.

Note

Roles shouldn't be manually edited in Microsoft Entra ID when doing role imports.

## Step 1: Plan your provisioning deployment

1. Learn about [how the provisioning service works](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/user-provisioning).
2. Determine who's in [scope for provisioning](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts).
3. Determine what data to [map between Microsoft Entra ID and SolarWinds Service Desk](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/customize-application-attributes).

## Step 2: Configure SolarWinds Service Desk to support provisioning with Microsoft Entra ID

To generate a secret token for authentication, see [Article tokens authentication for API integration](https://help.samanage.com/s/article/Tutorial-Tokens-Authentication-for-API-Integration-1536721557657).

## Step 3: Add SolarWinds Service Desk from the Microsoft Entra application gallery

Add SolarWinds Service Desk from the Microsoft Entra application gallery to start managing provisioning to SolarWinds Service Desk. If you previously set up SolarWinds Service Desk for SSO, you can use the same application. However, we recommend that you create a separate app when testing out the integration initially. Learn more about adding an application from the gallery [here](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/add-application-portal).

## Step 4: Define who is in scope for provisioning

The Microsoft Entra provisioning service allows you to scope who is provisioned based on assignment to the application, or based on attributes of the user or group. If you choose to scope who is provisioned to your app based on assignment, you can use the [steps to assign users and groups to the application](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/assign-user-or-group-access-portal). If you choose to scope who is provisioned based solely on attributes of the user or group, you can [use a scoping filter](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts).

- Start small. Test with a small set of users and groups before rolling out to everyone. When scope for provisioning is set to assigned users and groups, you can control this by assigning one or two users or groups to the app. When scope is set to all users and groups, you can specify an [attribute based scoping filter](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts).
- If you need extra roles, you can [update the application manifest](https://learn.microsoft.com/en-us/entra/identity-platform/howto-add-app-roles-in-apps) to add new roles.

## Step 5: Configure automatic user provisioning to SolarWinds Service Desk

This section guides you through the steps to configure the Microsoft Entra provisioning service to create, update, and disable users and/or groups in TestApp based on user and/or group assignments in Microsoft Entra ID.

### To configure automatic user provisioning for SolarWinds Service Desk in Microsoft Entra ID:

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps**

   ![Enterprise applications blade](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/enterprise-applications.png)

3. In the applications list, select **SolarWinds Service Desk**.
4. Select the **Provisioning** tab.

   ![Screenshot that shows the Provisioning tab selected.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/provisioning.png)

5. Select **+ New configuration**.

   ![Screenshot of Provisioning tab automatic.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/application-provisioning.png)

6. In the **Tenant URL** field, input `https://api.samanage.com`. Input the secret token value retrieved earlier in **Secret Token**. Select **Test Connection** to ensure Microsoft Entra ID can connect to SolarWinds Service Desk. If the connection fails, ensure your SolarWinds Service Desk account has the required admin permissions and try again.

   ![Screenshot of Provisioning test connection.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/provisioning-test-connection.png)

7. Select **Create** to create your configuration.
8. Select **Properties** on the **Overview** page.
9. Select the **Edit** icon to edit the properties. Enable notification emails and provide an email to receive quarantine emails. Enable accidental deletions prevention. Select **Apply** to save the changes.

   ![Screenshot of Provisioning properties.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/provisioning-properties.png)

10. Select **Attribute Mapping** in the left panel and select **users**.
11. Review the user attributes that are synchronized from Microsoft Entra ID to SolarWinds Service Desk in the **Attribute-Mapping** section. The attributes selected as **Matching** properties are used to match the user accounts in SolarWinds Service Desk for update operations. If you choose to change the [matching target attribute](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/customize-application-attributes), you need to ensure that the SolarWinds Service Desk API supports filtering users based on that attribute. Select the **Save** button to commit any changes.

    ![Samange User mappings](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/samanage-provisioning-tutorial/user-attributes.png)

12. Select **Groups**.
13. Review the group attributes that are synchronized from Microsoft Entra ID to SolarWinds Service Desk in the **Attribute-Mapping** section. The attributes selected as **Matching** properties are used to match the groups in SolarWinds Service Desk for update operations. Select the **Save** button to commit any changes.

    ![Samange Group mappings](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/samanage-provisioning-tutorial/group-attributes.png)

14. To configure scoping filters, refer to the following instructions provided in the [Scoping filter article](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts).
15. Use [on-demand provisioning](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/provision-on-demand) to validate sync with a small number of users before deploying more broadly in your organization.
16. When you're ready to provision, select **Start Provisioning** from the **Overview** page.

## Step 6: Monitor your deployment

Once you configure provisioning, use the following resources to monitor your deployment:

1. Use the [provisioning logs](https://learn.microsoft.com/en-us/entra/identity/monitoring-health/concept-provisioning-logs) to determine which users are provisioned successfully or unsuccessfully
2. Check the [progress bar](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/application-provisioning-when-will-provisioning-finish-specific-user) to see the status of the provisioning cycle and how close it's to completion
3. If the provisioning configuration seems to be in an unhealthy state, the application goes into quarantine. Learn more about quarantine states the [application provisioning quarantine status](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/application-provisioning-quarantine-status) article.

## Connector limitations

If you select the **Sync all users and groups** option and configure a value for the SolarWinds Service Desk **roles** attribute, the value under the **Default value if null \(is optional\)** box must be expressed in the following format:

- {"displayName":"role"}, where role is the default value you want.

## Change log

- 09/14/2020 - Changed the company name in two SaaS articles from Samanage to SolarWinds Service Desk \(previously Samanage\) per `https://github.com/ravitmorales`.
- 04/22/2020 - Updated authorization method from basic auth to long lived secret token.

## Additional resources

- [Managing user account provisioning for Enterprise Apps](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/configure-automatic-user-provisioning-portal)

## Related content

- [Learn how to review logs and get reports on provisioning activity](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/check-status-user-account-provisioning)
