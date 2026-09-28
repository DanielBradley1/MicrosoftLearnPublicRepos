<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/mediusflow-provisioning-tutorial -->
<!-- Sitemap-Last-Modified: 2026-03-24 -->

# Configure MediusFlow for automatic user provisioning with Microsoft Entra ID

This article describes the steps you need to perform in both MediusFlow and Microsoft Entra ID to configure automatic user provisioning. When configured, Microsoft Entra ID automatically provisions and de-provisions users and groups to [MediusFlow](https://www.mediusflow.com/) using the Microsoft Entra provisioning service. For important details on what this service does, how it works, and frequently asked questions, see [Automate user provisioning and deprovisioning to SaaS applications with Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/user-provisioning).

## Capabilities supported

- Create users in MediusFlow
- Remove users in MediusFlow when they don't require access anymore
- Keep user attributes synchronized between Microsoft Entra ID and MediusFlow
- Provision groups and group memberships in MediusFlow
- Single sign-on to MediusFlow \(recommended\)

## Prerequisites

The scenario outlined in this article assumes that you already have the following prerequisites:

- A Microsoft Entra user account with an active subscription. If you don't already have one, you can [Create an account for free](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
- One of the following roles:

  - [Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#application-administrator)
  - [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator)
  - [Application Owner](https://learn.microsoft.com/en-us/entra/fundamentals/users-default-permissions#owned-enterprise-applications).

- An active MediusFlow subscription with a Quality assurance or Production tenant.
- A user account in MediusFlow with admin access rights to be able to carry out the configuration within MediusFlow.
- The companies added in the MediusFlow tenant where the users should be provisioned to.

## Step 1: Plan your provisioning deployment

1. Learn about [how the provisioning service works](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/user-provisioning).
2. Determine who's in [scope for provisioning](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts).
3. Determine what data to [map between Microsoft Entra ID and MediusFlow](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/customize-application-attributes).

## Step 2: Configure MediusFlow to support provisioning with Microsoft Entra ID

### Activate the Microsoft 365 app within MediusFlow

Start by enabling the access of the Microsoft Entra login and the Microsoft Entra configuration feature within MediusFlow by performing the following steps:

#### User login

To enable the login flow to Microsoft 365 / Microsoft Entra ID, refer to [this](https://success.medius.com/documentation/administration_guide/user_login_and_transfer/end_to_end_support_office365/office365userintegration/#gatsby-focus-wrapper) article.

#### User transfer configuration

To enable the configuration portal of the users for provisioning from Microsoft Entra ID refer to [this](https://success.medius.com/documentation/administration_guide/manage_your_integration/#company-onboarding) article.

#### Configure user provisioning

1. Login to [MediusFlow admin console](https://office365.cloudapp.mediusflow.com/) by providing the tenant ID.

   ![Screenshot of the MediusFlow admin console. The MediusFlow tenant name box and the Authenticate button are highlighted in the first integration step.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/mediusflow-provisioning-tutorial/1-auth.png)

2. Verify the connection with MediusFlow.

   ![Verify](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/mediusflow-provisioning-tutorial/2-verify-connection.png)

3. Provide the Microsoft Entra tenant ID.

   ![provide Tenant ID](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/mediusflow-provisioning-tutorial/3-provide-azuread-tenantid.png)


   You can read more in the [FAQ](https://success.medius.com/documentation/administration_guide/user_login_and_transfer/end_to_end_support_office365/office365userintegration/#getting-azure-tenantid) on how to find it.

4. Save the configuration.

   ![Screenshot of the MediusFlow admin console that shows the fourth integration step. The Save configuration button is highlighted.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/mediusflow-provisioning-tutorial/4-save-config.png)

5. Select user provisioning and select **OK**.

   ![Screenshot of the MediusFlow admin console that shows the fifth integration step. The Use user provisioning and Ok buttons are highlighted.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/mediusflow-provisioning-tutorial/5-select-user-provisioning.png)

6. Select **Generate Secret Key**. Copy and save this value. This value is entered in the **Secret Token** field in the **Provisioning** tab of your MediusFLow application.

   ![Screenshot of the User provisioning configuration tab in the MediusFlow admin console. The Generate secret key and Copy buttons are highlighted.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/mediusflow-provisioning-tutorial/6-create-secret-1.png)

7. Select **OK**.

   ![Screenshot of the MediusFlow admin console with a notification telling users to select Ok to generate a new secret key. The Ok button is highlighted.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/mediusflow-provisioning-tutorial/7-confirm-secret.png)

8. To get the users imported with a pre-defined set of roles, companies and other general configurations in MediusFlow, you need to configure it first. Start by adding the configuration by selecting **Add new configuration**.

   ![Screenshot of the User provisioning configuration tab in the MediusFlow admin console. The Add new configuration button is highlighted.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/mediusflow-provisioning-tutorial/8-configure-user-configuration-1.png)

9. Provide the default settings for the users. In this view, it's possible to set the default attribute. If the standard settings are ok, it's enough to provide just a valid company name. Since these configuration settings are fetched from Mediusflow, they need to be configured first. For more information see the **Prerequisites** section of this article.

   ![Screenshot of the MediusFlow Add new configuration window. Many settings are visible, including locale settings, a filter, and user roles.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/mediusflow-provisioning-tutorial/9-configure-user-config-detail-1.png)

10. Select **Save** to save the user configuration.

    ![Screenshot of the User provisioning configuration tab in the MediusFlow admin console. The Save button is highlighted.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/mediusflow-provisioning-tutorial/10-done-1.png)

11. To get the user provisioning link select **Copy SCIM Link**. Copy and save this value. This value is entered in the **Tenant URL** field in the **Provisioning** tab of your MediusFLow application.

    ![Screenshot of the User provisioning configuration tab in the MediusFlow admin console. The Copy S C I M link button is highlighted.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/mediusflow-provisioning-tutorial/11-get-scim-link.png)

## Step 3: Add MediusFlow from the Microsoft Entra application gallery

Add MediusFlow from the Microsoft Entra application gallery to start managing provisioning to MediusFlow. If you have previously setup MediusFlow for SSO, you can use the same application. However, we recommend that you create a separate app when testing out the integration initially. Learn more about adding an application from the gallery [here](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/add-application-portal).

## Step 4: Define who is in scope for provisioning

The Microsoft Entra provisioning service allows you to scope who is provisioned based on assignment to the application, or based on attributes of the user or group. If you choose to scope who is provisioned to your app based on assignment, you can use the [steps to assign users and groups to the application](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/assign-user-or-group-access-portal). If you choose to scope who is provisioned based solely on attributes of the user or group, you can [use a scoping filter](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts).

- Start small. Test with a small set of users and groups before rolling out to everyone. When scope for provisioning is set to assigned users and groups, you can control this by assigning one or two users or groups to the app. When scope is set to all users and groups, you can specify an [attribute based scoping filter](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts).
- If you need extra roles, you can [update the application manifest](https://learn.microsoft.com/en-us/entra/identity-platform/howto-add-app-roles-in-apps) to add new roles.

## Step 5: Configure automatic user provisioning to MediusFlow

This section guides you through the steps to configure the Microsoft Entra provisioning service to create, update, and disable users and/or groups in TestApp based on user and/or group assignments in Microsoft Entra ID.

### To configure automatic user provisioning for MediusFlow in Microsoft Entra ID:

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps**

   ![Enterprise applications blade](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/enterprise-applications.png)

3. In the applications list, select **MediusFlow**.

   ![The MediusFlow link in the Applications list](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/all-applications.png)

4. Select the **Provisioning** tab.

   ![Screenshot of the Manage options with the Provisioning option called out.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/provisioning.png)

5. Select **+ New configuration**.

   ![Screenshot of Provisioning tab automatic.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/application-provisioning.png)

6. Under the **Admin Credentials** section, input the tenant URL value retrieved earlier in **Tenant URL**. Input the secret Token value retrieved earlier in **Secret Token**. Select **Test Connection** to ensure Microsoft Entra ID can connect to MediusFlow. If the connection fails, ensure your MediusFlow account has Admin permissions and try again.

   ![Screenshot shows the Admin Credentials dialog box, where you can enter your Tenant U R L and Secret Token.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/mediusflow-provisioning-tutorial/provisioning.png)

7. Select **Create** to create your configuration.
8. Select **Properties** on the **Overview** page.
9. Select the **Edit** icon to edit the properties. Enable notification emails and provide an email to receive quarantine emails. Enable accidental deletions prevention. Select **Apply** to save the changes.

   ![Screenshot of Provisioning properties.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/provisioning-properties.png)

10. Select **Attribute Mapping** in the left panel and select **users**.
11. Review the user attributes that are synchronized from Microsoft Entra ID to MediusFlow in the **Attribute-Mapping** section. The attributes selected as **Matching** properties are used to match the user accounts in MediusFlow for update operations. If you choose to change the [matching target attribute](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/customize-application-attributes), you need to ensure that the MediusFlow API supports filtering users based on that attribute. Select the **Save** button to commit any changes.
    | Attribute | Type | Supported for filtering |
    | --- | --- | --- |
    | userName | String | ✓ |
    | emails\[type eq "work"\].value | String |  |
    | name.displayName | String |  |
    | active | Boolean |  |
    | name.givenName | String |  |
    | name.familyName | String |  |
    | name.formatted | String |  |
    | externalId | String |  |
    | urn:ietf:params:scim:schemas:extension:enterprise:2.0:User:manager | Reference |  |
    | urn:ietf:params:scim:schemas:extension:medius:2.0:User:configurationFilter | String |  |
    | urn:ietf:params:scim:schemas:extension:medius:2.0:User:identityProvider | String |  |
    | urn:ietf:params:scim:schemas:extension:medius:2.0:User:nameIdentifier | String |  |
    | urn:ietf:params:scim:schemas:extension:medius:2.0:User:customFieldText1 | String |  |
    | urn:ietf:params:scim:schemas:extension:medius:2.0:User:customFieldText2 | String |  |
    | urn:ietf:params:scim:schemas:extension:medius:2.0:User:customFieldText3 | String |  |
    | urn:ietf:params:scim:schemas:extension:medius:2.0:User:customFieldText4 | String |  |
    | urn:ietf:params:scim:schemas:extension:medius:2.0:User:customFieldText5 | String |  |
12. Select **Groups**.
13. Review the group attributes that are synchronized from Microsoft Entra ID to MediusFlow in the **Attribute-Mapping** section. The attributes selected as **Matching** properties are used to match the groups in MediusFlow for update operations. Select the **Save** button to commit any changes.
    | Attribute | Type |
    | --- | --- |
    | displayName | String |
    | externalID | String |
    | members | Reference |
14. To configure scoping filters, refer to the following instructions provided in the [Scoping filter article](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts).
15. Use [on-demand provisioning](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/provision-on-demand) to validate sync with a small number of users before deploying more broadly in your organization.
16. When you're ready to provision, select **Start Provisioning** from the **Overview** page.

## Step 6: Monitor your deployment

Once you configure provisioning, use the following resources to monitor your deployment:

1. Use the [provisioning logs](https://learn.microsoft.com/en-us/entra/identity/monitoring-health/concept-provisioning-logs) to determine which users are provisioned successfully or unsuccessfully
2. Check the [progress bar](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/application-provisioning-when-will-provisioning-finish-specific-user) to see the status of the provisioning cycle and how close it's to completion
3. If the provisioning configuration seems to be in an unhealthy state, the application goes into quarantine. Learn more about quarantine states the [application provisioning quarantine status](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/application-provisioning-quarantine-status) article.

## Change log

- 01/21/2021 - Custom extension attributes **configurationFilter**, **identityProvider**, **nameIdentifier**, **customFieldText1**, **customFieldText2**, **customFieldText3**, **customFieldText3** and **customFieldText5** has been added.

## Additional resources

- [Managing user account provisioning for Enterprise Apps](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/configure-automatic-user-provisioning-portal)
- [What is application access and single sign-on with Microsoft Entra ID?](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/what-is-single-sign-on)

## Related content

- [Learn how to review logs and get reports on provisioning activity](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/check-status-user-account-provisioning)
