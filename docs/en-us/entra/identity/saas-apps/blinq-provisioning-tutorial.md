<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/blinq-provisioning-tutorial -->
<!-- Sitemap-Last-Modified: 2026-03-05 -->

# Configure Blinq for automatic user provisioning with Microsoft Entra ID

This article describes the steps you need to do in both Blinq and Microsoft Entra ID to configure automatic user provisioning. When configured, Microsoft Entra ID automatically provisions and deprovisions users and groups to [Blinq](https://blinq.me/) using the Microsoft Entra provisioning service. For important details on what this service does, how it works, and frequently asked questions, see [Automate user provisioning and deprovisioning to SaaS applications with Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/user-provisioning).

## Capabilities supported

- Create users in Blinq.
- Remove users in Blinq when they don't require access anymore.
- Keep user attributes synchronized between Microsoft Entra ID and Blinq.
- Long lived bearer token authentication supported.

## Prerequisites

The scenario outlined in this article assumes that you already have the following prerequisites:

- [A Microsoft Entra tenant](https://learn.microsoft.com/en-us/entra/identity-platform/quickstart-create-new-tenant)
- One of the following roles: [Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#application-administrator), [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator), or [Application Owner](https://learn.microsoft.com/en-us/entra/fundamentals/users-default-permissions#owned-enterprise-applications).
- A user account in Blinq with Admin permission

## Step 1: Plan your provisioning deployment

1. Learn about [how the provisioning service works](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/user-provisioning).
2. Determine who's in [scope for provisioning](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts).
3. Determine what data to [map between Microsoft Entra ID and Blinq](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/customize-application-attributes).

## Step 2: Configure Blinq to support provisioning with Microsoft Entra ID

1. Navigate to [Blinq Admin Console](https://dash.blinq.me) in a separate browser tab.
2. If you aren't logged in to Blinq, you need to do so.
3. Select your workspace in the top left hand corner of the screen and select **Settings** in the dropdown menu.

   [![Screenshot of the Blinq settings option.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/blinq-provisioning-tutorial/blinq-settings.png)](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/blinq-provisioning-tutorial/blinq-settings.png#lightbox)

4. Under the **Integrations** page you should see **Team Card Provisioning** which contains a URL and Token. You need to generate the token by selecting **Generate**. Copy the **URL** and **Token**. The URL and the Token are to be inserted into the **Tenant URL** and **Secret Token** field in the Azure portal respectively.

   [![Screenshot of the Blinq integration page.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/blinq-provisioning-tutorial/blinq-integrations-page.png)](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/blinq-provisioning-tutorial/blinq-integrations-page.png#lightbox)

## Step 3: Add Blinq from the Microsoft Entra application gallery

Add Blinq from the Microsoft Entra application gallery to start managing provisioning to Blinq. If you have previously setup Blinq for SSO, you can use the same application. However it's recommended you create a separate app when testing out the integration initially. Learn more about adding an application from the gallery [here](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/add-application-portal).

## Step 4: Define who is in scope for provisioning

The Microsoft Entra provisioning service allows you to scope who is provisioned based on assignment to the application, or based on attributes of the user or group. If you choose to scope who is provisioned to your app based on assignment, you can use the [steps to assign users and groups to the application](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/assign-user-or-group-access-portal). If you choose to scope who is provisioned based solely on attributes of the user or group, you can [use a scoping filter](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts).

- Start small. Test with a small set of users and groups before rolling out to everyone. When scope for provisioning is set to assigned users and groups, you can control this by assigning one or two users or groups to the app. When scope is set to all users and groups, you can specify an [attribute based scoping filter](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts).
- If you need extra roles, you can [update the application manifest](https://learn.microsoft.com/en-us/entra/identity-platform/howto-add-app-roles-in-apps) to add new roles.

## Step 5: Configure automatic user provisioning to Blinq

This section guides you through the steps to configure the Microsoft Entra provisioning service to create, update, and disable users and groups in Blinq based on user and group assignments in Microsoft Entra ID.

### To configure automatic user provisioning for Blinq in Microsoft Entra ID:

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps**

   ![Screenshot of Enterprise applications blade.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/enterprise-applications.png)

3. In the applications list, select **Blinq**.

   ![Screenshot of the Blinq link in the Applications list.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/all-applications.png)

4. Select the **Provisioning** tab.

   ![Screenshot of Provisioning tab.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/provisioning.png)

5. Set **+ New configuration**.

   ![Screenshot of Provisioning tab automatic.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/application-provisioning.png)

6. In the **Tenant URL** field, input your Blinq Tenant URL and Secret Token. Select **Test Connection** to ensure Microsoft Entra ID can connect to Blinq. If the connection fails, ensure your Blinq account has the required admin permissions and try again.

   ![Screenshot of Provisioning test connection.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/provisioning-test-connection.png)

7. Select **Create** to create your configuration.
8. Select **Properties** in the **Overview** page.
9. Select the pencil to edit the properties. Enable notification emails and provide an email to receive quarantine emails. Enable accidental deletions prevention. Select **Apply** to save the changes.

   ![Screenshot of Provisioning properties.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/provisioning-properties.png)

10. Select **Attribute Mapping** in the left panel and select **users**.
11. Review the user attributes that are synchronized from Microsoft Entra ID to Blinq in the **Attribute-Mapping** section. The attributes selected as **Matching** properties are used to match the user accounts in Blinq for update operations. If you choose to change the [matching target attribute](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/customize-application-attributes), you need to ensure that the Blinq API supports filtering users based on that attribute. Select the **Save** button to commit any changes.
    | Attribute | Type | Supported for filtering | Required by Blinq |
    | --- | --- | --- | --- |
    | userName | String | ✓ | ✓ |
    | active | Boolean |  |  |
    | displayName | String |  |  |
    | nickName | String |  |  |
    | title | String |  |  |
    | preferredLanguage | String |  |  |
    | locale | String |  |  |
    | timezone | String |  |  |
    | name.givenName | String |  |  |
    | name.familyName | String |  |  |
    | name.formatted | String |  |  |
    | name.middleName | String |  |  |
    | name.honorificPrefix | String |  |  |
    | name.honorificSuffix | String |  |  |
    | externalId | String |  |  |
    | emails\[type eq "work"\].value | String |  |  |
    | emails\[type eq "home"\].value | String |  |  |
    | emails\[type eq "other"\].value | String |  |  |
    | phoneNumbers\[type eq "work"\].value | String |  |  |
    | phoneNumbers\[type eq "mobile"\].value | String |  |  |
    | phoneNumbers\[type eq "fax"\].value | String |  |  |
    | phoneNumbers\[type eq "home"\].value | String |  |  |
    | phoneNumbers\[type eq "other"\].value | String |  |  |
    | phoneNumbers\[type eq "pager"\].value | String |  |  |
    | addresses\[type eq "work"\].formatted | String |  |  |
    | addresses\[type eq "work"\].streetAddress | String |  |  |
    | addresses\[type eq "work"\].locality | String |  |  |
    | addresses\[type eq "work"\].region | String |  |  |
    | addresses\[type eq "work"\].postalCode | String |  |  |
    | addresses\[type eq "work"\].country | String |  |  |
    | addresses\[type eq "home"\].formatted | String |  |  |
    | addresses\[type eq "home"\].streetAddress | String |  |  |
    | addresses\[type eq "home"\].locality | String |  |  |
    | addresses\[type eq "home"\].region | String |  |  |
    | addresses\[type eq "home"\].postalCode | String |  |  |
    | addresses\[type eq "home"\].country | String |  |  |
    | addresses\[type eq "other"\].formatted | String |  |  |
    | addresses\[type eq "other"\].streetAddress | String |  |  |
    | addresses\[type eq "other"\].locality | String |  |  |
    | addresses\[type eq "other"\].region | String |  |  |
    | addresses\[type eq "other"\].postalCode | String |  |  |
    | addresses\[type eq "other"\].country | String |  |  |
    | urn:ietf:params:scim:schemas:extension:enterprise:2.0:User:employeeNumber | String |  |  |
    | urn:ietf:params:scim:schemas:extension:enterprise:2.0:User:organization | String |  |  |
    | urn:ietf:params:scim:schemas:extension:enterprise:2.0:User:division | String |  |  |
    | urn:ietf:params:scim:schemas:extension:enterprise:2.0:User:department | String |  |  |
12. To configure scoping filters, refer to the following instructions provided in the [Scoping filter article](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts).
13. Use [on-demand provisioning](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/provision-on-demand) to validate sync with a few users before deploying more broadly in your organization.
14. When you're ready to provision, select **Start Provisioning** from the **Overview** page.

## Step 6: Monitor your deployment

Once you configure provisioning, use the following resources to monitor your deployment:

1. Use the [provisioning logs](https://learn.microsoft.com/en-us/entra/identity/monitoring-health/concept-provisioning-logs) to determine which users are provisioned successfully or unsuccessfully
2. Check the [progress bar](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/application-provisioning-when-will-provisioning-finish-specific-user) to see the status of the provisioning cycle and how close it's to completion
3. If the provisioning configuration seems to be in an unhealthy state, the application goes into quarantine. Learn more about quarantine states the [application provisioning quarantine status](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/application-provisioning-quarantine-status) article.

## Change Logs

- 05/25/2022 - **Schema Discovery** feature enabled on this app.
- 12/22/2022 - The source attribute of **addresses\[type eq "work"\].formatted** ha been changed to **Join\("", \[streetAddress\], IIF\(IsPresent\(\[city\]\),", ",""\), \[city\], IIF\(IsPresent\(\[state\]\),", ",""\), \[state\], IIF\(IsPresent\(\[postalCode\]\)," ",""\), \[postalCode\]\) --> addresses\[type eq "work"\].formatted**.

## More resources

- [Managing user account provisioning for Enterprise Apps](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/configure-automatic-user-provisioning-portal)
- [What is application access and single sign-on with Microsoft Entra ID?](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/what-is-single-sign-on)

## Related content

- [Learn how to review logs and get reports on provisioning activity](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/check-status-user-account-provisioning)
