<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/meta-networks-connector-provisioning-tutorial -->
<!-- Sitemap-Last-Modified: 2026-03-24 -->

# Configure Meta Networks Connector for automatic user provisioning with Microsoft Entra ID

The objective of this article is to demonstrate the steps to be performed in Meta Networks Connector and Microsoft Entra ID to configure Microsoft Entra ID to automatically provision and de-provision users and/or groups to Meta Networks Connector.

Note

This article describes a connector built on top of the Microsoft Entra user Provisioning Service. For important details on what this service does, how it works, and frequently asked questions, see [Automate user provisioning and deprovisioning to SaaS applications with Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/user-provisioning).

## Prerequisites

The scenario outlined in this article assumes that you already have the following prerequisites:

- A Microsoft Entra user account with an active subscription. If you don't already have one, you can [Create an account for free](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
- One of the following roles:

  - [Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#application-administrator)
  - [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator)
  - [Application Owner](https://learn.microsoft.com/en-us/entra/fundamentals/users-default-permissions#owned-enterprise-applications).

- [A Meta Networks Connector tenant](https://www.metanetworks.com/)
- A user account in Meta Networks Connector with Admin permissions.

## Step 1: Plan your provisioning deployment

1. Learn about [how the provisioning service works](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/user-provisioning).
2. Determine who's in [scope for provisioning](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts).
3. Determine what data to [map between Microsoft Entra ID and Meta Networks Connector](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/customize-application-attributes).

## Assigning users to Meta Networks Connector

Microsoft Entra ID uses a concept called *assignments* to determine which users should receive access to selected apps. In the context of automatic user provisioning, only the users and/or groups that have been assigned to an application in Microsoft Entra ID are synchronized.

Before configuring and enabling automatic user provisioning, you should decide which users and/or groups in Microsoft Entra ID need access to Meta Networks Connector. Once decided, you can assign these users and/or groups to Meta Networks Connector by following the instructions here:

- [Assign a user or group to an enterprise app](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/assign-user-or-group-access-portal)

## Important tips for assigning users to Meta Networks Connector

- It's recommended that a single Microsoft Entra user is assigned to Meta Networks Connector to test the automatic user provisioning configuration. Additional users and/or groups may be assigned later.
- When assigning a user to Meta Networks Connector, you must select any valid application-specific role \(if available\) in the assignment dialog. Users with the **Default Access** role are excluded from provisioning.

## Step 2: Configure Meta Networks Connector for provisioning

1. Sign in to your [Meta Networks Connector Admin Console](https://login.metanetworks.com/login/) using your organization name. Navigate to **Administration > API Keys**.

   ![Meta Networks Connector Admin Console](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/meta-networks-connector-provisioning-tutorial/apikey.png)

2. Select the plus sign on the upper right side of the screen to create a new **API Key**.
3. Set the **API Key Name** and **API Key Description**.

   ![Screenshot of the Meta Networks Connector Admin Console with highlighted A P I key name and A P I key description values of Microsoft Entra ID and A P I key.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/meta-networks-connector-provisioning-tutorial/keyname.png)

4. Turn on **Write** privileges for **Groups** and **Users**.

   ![Meta Networks Connector privileges](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/meta-networks-connector-provisioning-tutorial/privileges.png)

5. Select **Add**. Copy the **SECRET** and save it as it's the only time you can view it. This value is entered in the Secret Token field in the Provisioning tab of your Meta Networks Connector application.

   ![Screenshot of a window telling users that the A P I key was added. The Secret box contains an indecipherable value and is highlighted.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/meta-networks-connector-provisioning-tutorial/token.png)

6. Add an IdP by navigating to **Administration > Settings > IdP > Create New**.

   ![Meta Networks Connector Add IdP](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/meta-networks-connector-provisioning-tutorial/newidp.png)

7. In the **IdP Configuration** page you can **Name** your IdP configuration and choose an **Icon**.

   ![Meta Networks Connector IdP Name](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/meta-networks-connector-provisioning-tutorial/idpname.png)


   ![Meta Networks Connector IdP Icon](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/meta-networks-connector-provisioning-tutorial/icon.png)

8. Under **Configure SCIM** select the API key name created in the previous steps. Select **Save**.

   ![Meta Networks Connector configure SCIM](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/meta-networks-connector-provisioning-tutorial/configure.png)

9. Navigate to **Administration > Settings > IdP tab**. Select the name of the IdP configuration created in the previous steps to view the **IdP ID**. This **ID** is added to the end of **Tenant URL** while entering the value in **Tenant URL** field in the Provisioning tab of your Meta Networks Connector application.

## Step 3: Add Meta Networks Connector from the Microsoft Entra application gallery

Add Meta Networks Connector from the Microsoft Entra application gallery to start managing provisioning to Meta Networks Connector. If you have previously setup Meta Networks Connector for SSO you can use the same application. However, we recommend that you create a separate app when testing out the integration initially. Learn more about adding an application from the gallery [here](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/add-application-portal).

## Step 4: Define who is in scope for provisioning

The Microsoft Entra provisioning service allows you to scope who is provisioned based on assignment to the application, or based on attributes of the user or group. If you choose to scope who is provisioned to your app based on assignment, you can use the [steps to assign users and groups to the application](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/assign-user-or-group-access-portal). If you choose to scope who is provisioned based solely on attributes of the user or group, you can [use a scoping filter](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts).

- Start small. Test with a small set of users and groups before rolling out to everyone. When scope for provisioning is set to assigned users and groups, you can control this by assigning one or two users or groups to the app. When scope is set to all users and groups, you can specify an [attribute based scoping filter](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts).
- If you need extra roles, you can [update the application manifest](https://learn.microsoft.com/en-us/entra/identity-platform/howto-add-app-roles-in-apps) to add new roles.

## Step 5: Configuring automatic user provisioning to Meta Networks Connector

This section guides you through the steps to configure the Microsoft Entra provisioning service to create, update, and disable users and/or groups in Meta Networks Connector based on user and/or group assignments in Microsoft Entra ID.

Tip

You may also choose to enable SAML-based single sign-on for Meta Networks Connector, following the instructions provided in the [Meta Networks Connector Single sign-on article](https://learn.microsoft.com/en-us/entra/identity/saas-apps/metanetworksconnector-tutorial). Single sign-on can be configured independently of automatic user provisioning, though these two features complement each other

### To configure automatic user provisioning for Meta Networks Connector in Microsoft Entra ID:

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps**

   ![Enterprise applications blade](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/enterprise-applications.png)

3. In the applications list, select **Meta Networks Connector**.

   ![The Meta Networks Connector link in the Applications list](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/all-applications.png)

4. Select the **Provisioning** tab.

   ![Screenshot of the Manage options with the Provisioning option called out.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/provisioning.png)

5. Select **+ New configuration**.

   ![Screenshot of Provisioning tab automatic.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/application-provisioning.png)

6. Under the **Admin Credentials** section, input `https://api.metanetworks.com/v1/scim/<IdP ID>` in **Tenant URL**. Input the **SCIM Authentication Token** value retrieved earlier in **Secret Token**. Select **Test Connection** to ensure Microsoft Entra ID can connect to Meta Networks Connector. If the connection fails, ensure your Meta Networks Connector account has Admin permissions and try again.

   ![Tenant URL + Token](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/provisioning-testconnection-tenanturltoken.png)

7. Select **Create** to create your configuration.
8. Select **Properties** on the **Overview** page.
9. Select the **Edit** icon to edit the properties. Enable notification emails and provide an email to receive quarantine emails. Enable accidental deletions prevention. Select **Apply** to save the changes.

   ![Screenshot of Provisioning properties.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/provisioning-properties.png)

10. Select **Attribute Mapping** in the left panel and select **users**.
11. Review the user attributes that are synchronized from Microsoft Entra ID to Meta Networks Connector in the **Attribute-Mapping** section. The attributes selected as **Matching** properties are used to match the user accounts in Meta Networks Connector for update operations. If you choose to change the [matching target attribute](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/customize-application-attributes), you need to ensure that the Meta Networks Connector API supports filtering users based on that attribute. Select the **Save** button to commit any changes.
    | Attribute | Type | Supported for filtering | Required by Meta Networks Connector |
    | --- | --- | --- | --- |
    | userName | String | ✓ | ✓ |
    | active | Boolean |  |  |
    | phonenumbers\[type eq "work"\].value | String |  |  |
    | name.givenName | String |  | ✓ |
    | name.familyName | String |  | ✓ |


    Note


    phonenumbers value should be in E164 format. For example +16175551212

12. Select **Groups**.
13. Review the group attributes that are synchronized from Microsoft Entra ID to Meta Networks Connector in the **Attribute-Mapping** section. The attributes selected as **Matching** properties are used to match the user accounts in Meta Networks Connector for update operations. If you choose to change the [matching target attribute](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/customize-application-attributes), you need to ensure that the Meta Networks Connector API supports filtering users based on that attribute. Select the **Save** button to commit any changes.
    | Attribute | Type | Supported for filtering | Required by Meta Networks Connector |
    | --- | --- | --- | --- |
    | displayName | String | ✓ | ✓ |
    | members | Reference |  |  |
14. To configure scoping filters, refer to the following instructions provided in the [Scoping filter article](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts).
15. Use [on-demand provisioning](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/provision-on-demand) to validate sync with a small number of users before deploying more broadly in your organization.
16. When you're ready to provision, select **Start Provisioning** from the **Overview** page.

## Step 6: Monitor your deployment

Once you configure provisioning, use the following resources to monitor your deployment:

1. Use the [provisioning logs](https://learn.microsoft.com/en-us/entra/identity/monitoring-health/concept-provisioning-logs) to determine which users are provisioned successfully or unsuccessfully
2. Check the [progress bar](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/application-provisioning-when-will-provisioning-finish-specific-user) to see the status of the provisioning cycle and how close it's to completion
3. If the provisioning configuration seems to be in an unhealthy state, the application goes into quarantine. Learn more about quarantine states the [application provisioning quarantine status](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/application-provisioning-quarantine-status) article.

## Change Log

04/06/2022 - Added support for **phoneNumbers\[type eq "work"\].value**. Removed support for **emails\[type eq "work"\].value** and **manager** . **name.givenName** and **name.familyName** made required attributes.

## More resources

- [Managing user account provisioning for Enterprise Apps](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/configure-automatic-user-provisioning-portal)
- [What is application access and single sign-on with Microsoft Entra ID?](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/what-is-single-sign-on)

## Related content

- [Learn how to review logs and get reports on provisioning activity](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/check-status-user-account-provisioning)
