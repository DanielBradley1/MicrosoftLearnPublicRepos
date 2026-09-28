<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/zendesk-provisioning-tutorial -->
<!-- Sitemap-Last-Modified: 2026-03-31 -->

# Configure Zendesk for automatic user provisioning with Microsoft Entra ID

This article describes the steps you need to perform in both Zendesk and Microsoft Entra ID to configure automatic user provisioning. When configured, Microsoft Entra ID automatically provisions and de-provisions users and groups to [Zendesk](http://www.zendesk.com/) using the Microsoft Entra provisioning service. For important details on what this service does, how it works, and frequently asked questions, see [Automate user provisioning and deprovisioning to SaaS applications with Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/user-provisioning).

## Capabilities supported

- Create users in Zendesk.
- Remove users in Zendesk when they don't require access anymore.
- Keep user attributes synchronized between Microsoft Entra ID and Zendesk.
- Provision groups and group memberships in Zendesk.
- [Single sign-on](https://learn.microsoft.com/en-us/entra/identity/saas-apps/zendesk-tutorial) to Zendesk \(recommended\)

## Prerequisites

The scenario outlined in this article assumes that you already have the following prerequisites:

- [A Microsoft Entra tenant](https://learn.microsoft.com/en-us/entra/identity-platform/quickstart-create-new-tenant).
- One of the following roles: [Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#application-administrator), [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator), or [Application Owner](https://learn.microsoft.com/en-us/entra/fundamentals/users-default-permissions#owned-enterprise-applications).
- A user account in Zendesk with Admin rights.
- A Zendesk tenant with the Professional plan or better enabled.

## Step 1: Plan your provisioning deployment

1. Learn about [how the provisioning service works](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/user-provisioning).
2. Determine who's in [scope for provisioning](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts).
3. Determine what data to [map between Microsoft Entra ID and Zendesk](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/customize-application-attributes).

## Step 2: Configure Zendesk to support provisioning with Microsoft Entra ID

1. Sign in to [Zendesk Admin Center](https://support.zendesk.com/hc/en-us/articles/4581766374554#topic_hfg_dyz_1hb).
2. Navigate to **Apps and integrations** > **APIs** > **Zendesk APIs**.
3. Select the **Settings** tab, and make sure Token Access is **enabled**.
4. Select the **Add API token** button to the right of **Active API Tokens**. The token is generated and displayed.
5. Enter an **API token description**.
6. **Copy** the token and paste it somewhere secure. Once you close this window, the full token will never be displayed again.
7. Select **Save** to return to the API page. If you select the token to reopen it, a truncated version of the token is displayed.

## Step 3: Add Zendesk from the Microsoft Entra application gallery

Add Zendesk from the Microsoft Entra application gallery to start managing provisioning to Zendesk. If you have previously setup Zendesk for SSO, you can use the same application. However, we recommend that you create a separate app when testing out the integration initially. Learn more about adding an application from the gallery [here](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/add-application-portal).

## Step 4: Define who is in scope for provisioning

The Microsoft Entra provisioning service allows you to scope who is provisioned based on assignment to the application, or based on attributes of the user or group. If you choose to scope who is provisioned to your app based on assignment, you can use the [steps to assign users and groups to the application](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/assign-user-or-group-access-portal). If you choose to scope who is provisioned based solely on attributes of the user or group, you can [use a scoping filter](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts).

- Start small. Test with a small set of users and groups before rolling out to everyone. When scope for provisioning is set to assigned users and groups, you can control this by assigning one or two users or groups to the app. When scope is set to all users and groups, you can specify an [attribute based scoping filter](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts).
- If you need extra roles, you can [update the application manifest](https://learn.microsoft.com/en-us/entra/identity-platform/howto-add-app-roles-in-apps) to add new roles.

## Step 5: Configure automatic user provisioning to Zendesk

This section guides you through the steps to configure the Microsoft Entra provisioning service to create, update, and disable users and/or groups in Zendesk based on user and/or group assignments in Microsoft Entra ID.

### Important tips for assigning users to Zendesk

- Today, Zendesk roles are automatically and dynamically populated in the Azure portal UI. Before you assign Zendesk roles to users, make sure that an initial sync is completed against Zendesk to retrieve the latest roles in your Zendesk tenant.
- We recommend that you assign a single Microsoft Entra user to Zendesk to test your initial automatic user provisioning configuration. You can assign more users or groups later after the tests are successful.
- When you assign a user to Zendesk, select any valid application-specific role, if available, in the assignment dialog box. Users with the **Default Access** role are excluded from provisioning.

### Configure automatic user provisioning for Zendesk in Microsoft Entra ID

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps**

   ![Screenshot of Enterprise applications blade.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/enterprise-applications.png)

3. In the applications list, select **Zendesk**.

   ![Screenshot of the Zendesk link in the Applications list.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/all-applications.png)

4. Select the **Provisioning** tab.

   ![Screenshot of Provisioning tab.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/provisioning.png)

5. Select **+ New configuration**.

   ![Screenshot of Provisioning tab automatic.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/application-provisioning.png)

6. Under the **Admin Credentials** section, input the admin username, secret token, and domain of your Zendesk account. Examples of these values are:

   - In the **Admin Username** box, fill in the username of the admin account on your Zendesk tenant. An example is admin@contoso.com.
   - In the **Secret Token** box, fill in the secret token as described in Step 6.
   - In the **Domain** box, fill in the subdomain of your Zendesk tenant. For example, for an account with a tenant URL of `https://my-tenant.zendesk.com`, your subdomain is **my-tenant**.

7. The secret token for your Zendesk account can be generated by following steps mentioned in **Step 2** above.
8. After you fill in the boxes shown in Step 5, select **Test Connection** to make sure that Microsoft Entra ID can connect to Zendesk. If the connection fails, make sure your Zendesk account has admin permissions and try again.

   ![Screenshot of Zendesk Test Connection](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/zendesk-provisioning-tutorial/zendesk19.png)

9. Select **Create** to create your configuration.
10. Select **Properties** on the **Overview** page.
11. Select the **Edit** icon to edit the properties. Enable notification emails and provide an email to receive quarantine notifications. Enable **Accidental deletions prevention**. Select **Apply** to save the changes.

    ![Screenshot of Provisioning properties.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/provisioning-properties.png)

12. Select **Attribute Mapping** in the left panel and select **users**.
13. Review the user attributes that are synchronized from Microsoft Entra ID to Zendesk in the **Attribute Mappings** section. The attributes selected as **Matching** properties are used to match the user accounts in Zendesk for update operations. To save any changes, select **Save**.

    ![Screenshot of Zendesk matching user attributes](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/zendesk-provisioning-tutorial/zendesk11.png)

14. Select **Groups**.
15. Review the group attributes that are synchronized from Microsoft Entra ID to Zendesk in the **Attribute Mappings** section. The attributes selected as **Matching** properties are used to match the groups in Zendesk for update operations. To save any changes, select **Save**.

    ![Screenshot of Zendesk matching group attributes](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/zendesk-provisioning-tutorial/zendesk13.png)

16. To configure scoping filters, refer to the instructions provided in the [Scoping filter article](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts).
17. Use [on-demand provisioning](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/provision-on-demand) to validate sync with a small number of users before deploying more broadly in your organization.
18. When you're ready to provision, select **Start Provisioning** from the **Overview** page.

You can use the **Synchronization Details** section to monitor progress and follow links to the provisioning activity report. The report describes all the actions performed by the Microsoft Entra provisioning service on Zendesk.

## Connector limitations

- Zendesk supports the use of groups for users with **Agent** roles only. For more information, see the [Zendesk documentation](https://support.zendesk.com/hc/en-us/articles/203661966-Creating-managing-and-using-groups).
- When a custom role is assigned to a user or group, the Microsoft Entra automatic user provisioning service also assigns the default role **Agent**. Only Agents can be assigned a custom role. For more information, see the [Zendesk API documentation](https://developer.zendesk.com/rest_api/docs/support/users#json-format-for-agent-or-admin-requests).
- Import of all roles fails if any of the custom roles has a display name similar to the built-in roles of "agent" or "end-user". To avoid this, ensure that none of the custom roles being imported has the above display names.

## More resources

- [Managing user account provisioning for Enterprise Apps](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/configure-automatic-user-provisioning-portal)
- [What is application access and single sign-on with Microsoft Entra ID?](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/what-is-single-sign-on)

## Related content

- [Learn how to review logs and get reports on provisioning activity](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/check-status-user-account-provisioning)
