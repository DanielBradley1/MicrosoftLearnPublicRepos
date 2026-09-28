<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/zenya-provisioning-tutorial -->
<!-- Sitemap-Last-Modified: 2026-03-31 -->

# Configure Zenya for automatic user provisioning with Microsoft Entra ID

The objective of this article is to demonstrate the steps to be performed in Zenya and Microsoft Entra ID to configure Microsoft Entra ID to automatically provision and deprovision users and/or groups to [Zenya](https://www.infoland.nl/). For important details on what this service does, how it works, and frequently asked questions, see [Automate user provisioning and deprovisioning to SaaS applications with Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/user-provisioning). Before you attempt to use this article, be sure that you know and meet all requirements. If you have questions, contact Infoland.

## Capabilities supported

> - Create users in Zenya
> - Remove/disable users in Zenya when they don't require access anymore
> - Keep user attributes synchronized between Microsoft Entra ID and Zenya
> - Provision groups and group memberships in Zenya
> - [Single sign-on](https://learn.microsoft.com/en-us/entra/identity/saas-apps/zenya-tutorial) to Zenya \(recommended\)

## Prerequisites

The scenario outlined in this article assumes that you already have the following prerequisites:

- [A Microsoft Entra tenant](https://learn.microsoft.com/en-us/entra/identity-platform/quickstart-create-new-tenant).
- One of the following roles: [Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#application-administrator), [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator), or [Application Owner](https://learn.microsoft.com/en-us/entra/fundamentals/users-default-permissions#owned-enterprise-applications).
- [A Zenya tenant](https://www.infoland.nl/).
- A user account in Zenya with admin permissions.

## Step 1: Plan your provisioning deployment

1. Learn about [how the provisioning service works](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/user-provisioning).
2. Determine who's in [scope for provisioning](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts).
3. Determine what data to [map between Microsoft Entra ID and Zenya](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/customize-application-attributes).

## Step 2: Configure Zenya to support provisioning with Microsoft Entra ID

1. Sign in to your [Zenya Admin Console](https://www.infoland.nl/). Navigate to **Go to > Application Management**.

   ![Screenshot showing the Zenya Admin Console.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/zenya-provisioning-tutorial/admin.png)

2. Select **External user management**.

   ![Screenshot showing the Zenya Users and Groups page with the External user management link highlighted.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/zenya-provisioning-tutorial/external.png)

3. To add a new provider, select the **plus** icon. In the new **Add provider** dialog box, provide a **Title**. You can choose to add **IP-based access restriction**. Select **OK**.

   ![Screenshot showing the Zenya add new button.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/zenya-provisioning-tutorial/add.png)


   ![Screenshot showing the Zenya add provider page.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/zenya-provisioning-tutorial/add-provider.png)

4. Select the **Permanent token** button. Copy the **Permanent token** and save it. You won't be able to view it later. This value is entered in the Secret Token field in the Provisioning tab of your Zenya application.

   ![Screenshot showing the Zenya User provisioning page for creating a Token.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/zenya-provisioning-tutorial/token.png)

## Step 3: Add Zenya from the Microsoft Entra application gallery

Add Zenya from the Microsoft Entra application gallery to start managing provisioning to Zenya. If you have previously setup Zenya for SSO, you can use the same application. However it's recommended that you create a separate app when testing out the integration initially. Learn more about adding an application from the gallery [here](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/add-application-portal).

## Step 4: Define who is in scope for provisioning

The Microsoft Entra provisioning service allows you to scope who is provisioned based on assignment to the application, or based on attributes of the user or group. If you choose to scope who is provisioned to your app based on assignment, you can use the [steps to assign users and groups to the application](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/assign-user-or-group-access-portal). If you choose to scope who is provisioned based solely on attributes of the user or group, you can [use a scoping filter](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts).

- Start small. Test with a small set of users and groups before rolling out to everyone. When scope for provisioning is set to assigned users and groups, you can control this by assigning one or two users or groups to the app. When scope is set to all users and groups, you can specify an [attribute based scoping filter](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts).
- If you need extra roles, you can [update the application manifest](https://learn.microsoft.com/en-us/entra/identity-platform/howto-add-app-roles-in-apps) to add new roles.

## Step 5: Configure automatic user provisioning to Zenya

This section guides you through the steps to configure the Microsoft Entra provisioning service to create, update, and disable users and/or groups in Zenya based on user and/or group assignments in Microsoft Entra ID.

For more information \(in Dutch\) also read: [`Implementatie SCIM koppeling`](https://webshare.iprova.nl/8my7yg8c1ofsmdj9/Document.aspx)

### To configure automatic user provisioning for Zenya in Microsoft Entra ID:

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps**

   ![Screenshot showing the Enterprise applications blade.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/enterprise-applications.png)

3. In the applications list, select **Zenya**.

   ![Screenshot to select the application from the Applications list.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/all-applications.png)

4. Select the **Provisioning** tab.

   ![Screenshot of the Manage options with the Provisioning option called out.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/provisioning.png)

5. Select **+ New configuration**.

   ![Screenshot of Provisioning tab automatic.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/application-provisioning.png)

6. In the **Admin Credentials** section, input the **SCIM 2.0 base URL and Permanent Token** values retrieved earlier in the **Tenant URL** and add /scim/ to it. Also add the **Secret Token**. You can generate a secret token in Zenya by using the **permanent token** button. Select **Test Connection** to ensure Microsoft Entra ID can connect to Zenya. If the connection fails, ensure your Zenya account has Admin permissions and try again.

   ![Screenshot showing the Test connection page and fields for Tenant URL and Token.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/provisioning-testconnection-tenanturltoken.png)

7. Select **Create** to create your configuration.
8. Select **Properties** on the **Overview** page.
9. Select the **Edit** icon to edit the properties. Enable notification emails and provide an email to receive quarantine notifications. Enable **Accidental deletions prevention**. Select **Apply** to save the changes.

   ![Screenshot of Provisioning properties.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/provisioning-properties.png)

10. Select **Attribute Mapping** in the left panel and select **users**.
11. Review the user attributes that are synchronized from Microsoft Entra ID to Zenya in the **Attribute Mapping** section. The attributes selected as **Matching** properties are used to match the user accounts in Zenya for update operations. Select the **Save** button to commit any changes.
    | Attribute | Type |
    | --- | --- |
    | active | Boolean |
    | displayName | String |
    | emails\[type eq "work"\].value | String |
    | preferredLanguage | String |
    | userName | String |
    | phoneNumbers\[type eq "work"\].value | String |
    | externalId | String |
    | urn:ietf:params:scim:schemas:extension:enterprise:2.0:User:department | String |
    | title | String |
    | urn:ietf:params:scim:schemas:extension:enterprise:2.0:User:manager | String |
12. Select **Groups**.
13. Review the group attributes that are synchronized from Microsoft Entra ID to Zenya in the **Attribute Mapping** section. The attributes selected as **Matching** properties are used to match the groups in Zenya for update operations. Select the **Save** button to commit any changes.
    | Attribute | Type |
    | --- | --- |
    | displayName | String |
    | members | Reference |
    | externalID | String |
14. To configure scoping filters, refer to the instructions provided in the [Scoping filter article](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts).
15. Use [on-demand provisioning](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/provision-on-demand) to validate sync with a small number of users before deploying more broadly in your organization.
16. When you're ready to provision, select **Start Provisioning** from the **Overview** page.

## Step 6: Monitor your deployment

Once you configure provisioning, use the following resources to monitor your deployment:

1. Use the [provisioning logs](https://learn.microsoft.com/en-us/entra/identity/monitoring-health/concept-provisioning-logs) to determine which users are provisioned successfully or unsuccessfully
2. Check the [progress bar](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/application-provisioning-when-will-provisioning-finish-specific-user) to see the status of the provisioning cycle and how close it's to completion
3. If the provisioning configuration seems to be in an unhealthy state, the application goes into quarantine. Learn more about quarantine states the [application provisioning quarantine status](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/application-provisioning-quarantine-status) article.

## Change log

- 06/17/2020 - Removed support for enterprise extension attribute **urn:ietf:params:scim:schemas:extension:enterprise:2.0:User:manager**.
- 10/11/2023 - Added support for core attribute **title** and added support for enterprise extension attributes **urn:ietf:params:scim:schemas:extension:enterprise:2.0:User:department** and **urn:ietf:params:scim:schemas:extension:enterprise:2.0:User:manager**.

## More resources

- [Managing user account provisioning for Enterprise Apps](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/configure-automatic-user-provisioning-portal)
- [What is application access and single sign-on with Microsoft Entra ID?](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/what-is-single-sign-on)
- [`Implementatie SCIM koppeling`](https://webshare.iprova.nl/8my7yg8c1ofsmdj9/Document.aspx)

## Related content

- [Learn how to review logs and get reports on provisioning activity](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/check-status-user-account-provisioning)
