<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/looop-provisioning-tutorial -->
<!-- Sitemap-Last-Modified: 2026-03-18 -->

# Configure Looop for automatic user provisioning with Microsoft Entra ID

The objective of this article is to demonstrate the steps to be performed in Looop and Microsoft Entra ID to configure Microsoft Entra ID to automatically provision and de-provision users and/or groups to Looop.

Note

This article describes a connector built on top of the Microsoft Entra user Provisioning Service. For important details on what this service does, how it works, and frequently asked questions, see [Automate user provisioning and deprovisioning to SaaS applications with Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/user-provisioning).

## Prerequisites

The scenario outlined in this article assumes that you already have the following prerequisites:

- A Microsoft Entra user account with an active subscription. If you don't already have one, you can [Create an account for free](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
- One of the following roles:

  - [Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#application-administrator)
  - [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator)
  - [Application Owner](https://learn.microsoft.com/en-us/entra/fundamentals/users-default-permissions#owned-enterprise-applications).

- [A Looop tenant](https://www.looop.co/pricing/)
- A user account on a Looop with Administrator permissions.

## Assign users to Looop

Microsoft Entra ID uses a concept called assignments to determine which users should receive access to selected apps. In the context of automatic user provisioning, only the users and/or groups that have been assigned to an application in Microsoft Entra ID are synchronized.

Before configuring and enabling automatic user provisioning, you should decide which users and/or groups in Microsoft Entra ID need access to Looop. Once decided, you can assign these users and/or groups to Looop by following the instructions here:

- [Assign a user or group to an enterprise app](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/assign-user-or-group-access-portal)

### Important tips for assigning users to Looop

- It's recommended that a single Microsoft Entra user is assigned to Looop to test the automatic user provisioning configuration. More users and/or groups may be assigned later.
- When assigning a user to Looop, you must select any valid application-specific role \(if available\) in the assignment dialog. Users with the **Default Access** role are excluded from provisioning.

## Set up Looop for provisioning

Before configuring Looop for automatic user provisioning with Microsoft Entra ID, you need to retrieve some provisioning information from Looop.

1. Sign in to your Looop Admin Console and select **Account**. Under **Account Settings**, select **Authentication**.

   ![Looop Admin](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/looop-provisioning-tutorial/admin.png)

2. Generate a new token by selecting **Reset Token** under **SCIM Integration**.

   ![Looop Token](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/looop-provisioning-tutorial/resettoken.png)

3. Copy the **SCIM Endpoint** and the **Token**. These values are entered in the **Tenant URL** and **Secret Token** fields in the Provisioning tab of your Looop application.

   ![Looop Create Token](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/looop-provisioning-tutorial/token.png)

## Add Looop from the gallery

To configure Looop for automatic user provisioning with Microsoft Entra ID, you need to add Looop from the Microsoft Entra application gallery to your list of managed SaaS applications.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **New application**.
3. In the **Add from the gallery** section, type **Looop**, select **Looop** in the results panel.

   ![Looop in the results list](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/search-new-app.png)

4. Select the **Sign-up for Looop** button, which will redirect you to Looop's login page.

   ![Looop OIDC Add](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/looop-provisioning-tutorial/signup.png)

5. As Looop is an OpenIDConnect app, choose to log in to Looop using your Microsoft work account.

   ![Looop OIDC login](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/looop-provisioning-tutorial/msftlogin.png)

6. After a successful authentication, accept the consent prompt for the consent page. The application will then be automatically added to your tenant and you'll be redirected to your Looop account.

## Configure automatic user provisioning to Looop

This section guides you through the steps to configure the Microsoft Entra provisioning service to create, update, and disable users and/or groups in Looop based on user and/or group assignments in Microsoft Entra ID.

### To configure automatic user provisioning for Looop in Microsoft Entra ID:

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps**

   ![Enterprise applications blade](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/enterprise-applications.png)

3. In the applications list, select **Looop**.

   ![The Looop link in the Applications list](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/all-applications.png)

4. Select the **Provisioning** tab.

   ![Screenshot of the Manage options with the Provisioning option called out.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/provisioning.png)

5. Select **+ New configuration**.

   ![Screenshot of Provisioning tab automatic.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/application-provisioning.png)

6. In the **Tenant URL** field, input your Looop Tenant URL and Secret Token. Select **Test Connection** to ensure Microsoft Entra ID can connect to Looop. If the connection fails, ensure your Looop account has the required admin permissions and try again.

   ![Screenshot of Provisioning test connection.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/provisioning-test-connection.png)

7. Select **Create** to create your configuration.
8. Select **Properties** on the **Overview** page.
9. Select the **Edit** icon to edit the properties. Enable notification emails and provide an email to receive quarantine emails. Enable accidental deletions prevention. Select **Apply** to save the changes.

   ![Screenshot of Provisioning properties.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/provisioning-properties.png)

10. Select **Attribute Mapping** in the left panel and select **users**.
11. Review the user attributes that are synchronized from Microsoft Entra ID to Looop in the **Attribute Mapping** section. The attributes selected as **Matching** properties are used to match the user accounts in Looop for update operations. Select the **Save** button to commit any changes.
    | Attribute | Type | Supported for filtering |
    | --- | --- | --- |
    | userName | String | ✓ |
    | active | Boolean |  |
    | emails\[type eq "work"\].value | String |  |
    | name.givenName | String |  |
    | name.familyName | String |  |
    | externalId | String |  |
    | urn:ietf:params:scim:schemas:extension:enterprise:2.0:User:department | String |  |
    | urn:ietf:params:scim:schemas:extension:enterprise:2.0:User:employeeNumber | String |  |
    | urn:ietf:params:scim:schemas:extension:enterprise:2.0:User:manager | String |  |
    | urn:ietf:params:scim:schemas:extension:Looop:2.0:User:area | String |  |
    | urn:ietf:params:scim:schemas:extension:Looop:2.0:User:custom\_1 | String |  |
    | urn:ietf:params:scim:schemas:extension:Looop:2.0:User:custom\_2 | String |  |
    | urn:ietf:params:scim:schemas:extension:Looop:2.0:User:custom\_3 | String |  |
    | urn:ietf:params:scim:schemas:extension:Looop:2.0:User:location | String |  |
    | urn:ietf:params:scim:schemas:extension:Looop:2.0:User:position | String |  |
    | urn:ietf:params:scim:schemas:extension:Looop:2.0:User:startAt | String |  |
12. Select **Groups**.
13. Review the group attributes that are synchronized from Microsoft Entra ID to Meta Networks Connector in the **Attribute Mapping** section. The attributes selected as **Matching** properties are used to match the groups in Meta Networks Connector for update operations. Select the **Save** button to commit any changes.
    | Attribute | Type | Supported for filtering |
    | --- | --- | --- |
    | displayName | String | ✓ |
    | members | Reference |  |
    | externalId | String |  |
14. To configure scoping filters, refer to the following instructions provided in the [Scoping filter article](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts).
15. Use [on-demand provisioning](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/provision-on-demand) to validate sync with a small number of users before deploying more broadly in your organization.
16. When you're ready to provision, select **Start Provisioning** from the **Overview** page.

## Monitor your deployment

Once you configure provisioning, use the following resources to monitor your deployment:

1. Use the [provisioning logs](https://learn.microsoft.com/en-us/entra/identity/monitoring-health/concept-provisioning-logs) to determine which users are provisioned successfully or unsuccessfully
2. Check the [progress bar](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/application-provisioning-when-will-provisioning-finish-specific-user) to see the status of the provisioning cycle and how close it's to completion
3. If the provisioning configuration seems to be in an unhealthy state, the application goes into quarantine. Learn more about quarantine states the [application provisioning quarantine status](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/application-provisioning-quarantine-status) article.

## Change log

- 07/15/2021 - Enterprise extension user attributes **urn:ietf:params:scim:schemas:extension:enterprise:2.0:User:department**, **urn:ietf:params:scim:schemas:extension:enterprise:2.0:User:employeeNumber** and **urn:ietf:params:scim:schemas:extension:enterprise:2.0:User:manager** have been added.
- 07/15/2021 - Custom extension user attributes **urn:ietf:params:scim:schemas:extension:Looop:2.0:User:department** and **urn:ietf:params:scim:schemas:extension:Looop:2.0:User:employee\_id** have been removed.

## More resources

- [Managing user account provisioning for Enterprise Apps](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/configure-automatic-user-provisioning-portal)
- [What is application access and single sign-on with Microsoft Entra ID?](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/what-is-single-sign-on)

## Related content

- [Learn how to review logs and get reports on provisioning activity](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/check-status-user-account-provisioning)
