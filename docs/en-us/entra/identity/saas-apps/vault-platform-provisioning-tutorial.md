<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/vault-platform-provisioning-tutorial -->
<!-- Sitemap-Last-Modified: 2026-04-10 -->

# Configure Vault Platform for automatic user provisioning with Microsoft Entra ID

This article describes the steps you need to perform in both Vault Platform and Microsoft Entra ID to configure automatic user provisioning. When configured, Microsoft Entra ID automatically provisions and de-provisions users to [Vault Platform](https://vaultplatform.com) using the Microsoft Entra provisioning service. For important details on what this service does, how it works, and frequently asked questions, see [Automate user provisioning and deprovisioning to SaaS applications with Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/user-provisioning).

## Supported capabilities

- Create users in Vault Platform.
- Remove users in Vault Platform when they don't require access anymore.
- Keep user attributes synchronized between Microsoft Entra ID and Vault Platform.
- [Single sign-on](https://learn.microsoft.com/en-us/entra/identity/saas-apps/vault-platform-tutorial) to Vault Platform \(recommended\).

## Prerequisites

The scenario outlined in this article assumes that you already have the following prerequisites:

- [A Microsoft Entra tenant](https://learn.microsoft.com/en-us/entra/identity-platform/quickstart-create-new-tenant)
- One of the following roles: [Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#application-administrator), [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator), or [Application Owner](https://learn.microsoft.com/en-us/entra/fundamentals/users-default-permissions#owned-enterprise-applications).
- An administrator account with Vault Platform.

## Step 1: Plan your provisioning deployment

1. Learn about [how the provisioning service works](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/user-provisioning).
2. Determine who's in [scope for provisioning](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts).
3. Determine what data to [map between Microsoft Entra ID and Vault Platform](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/customize-application-attributes).

## Step 2: Configure Vault Platform to support provisioning with Microsoft Entra ID

Contact Vault Platform support to configure Vault Platform to support provisioning with Microsoft Entra ID.

### 1. Authentication

Go to the Vault Platform, login with your email and password \(initial login method\), then head to the **Administration > Authentication page**.

There, first change the login method dropdown to **Identity Provider - Azure - SAML**

Using the details in the SAML setup instructions page, enter the information:

![Screenshot of VaultPlatform Authentication page.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/vault-platform-provisioning-tutorial/authentication.png)

1. Issuer URI must be set to `vaultplatform`
2. SSO URL must be set to the value of Login URL ![Screenshot for identifying SSO URL.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/vault-platform-provisioning-tutorial/sso-url-entry-point-uri.png)
3. Download the **Certificate \(Base64\)** file, open it in a text editor and copy its contents \(including the `-----BEGIN/END CERTIFICATE-----` markers\) into the **Certificate** text field ![Screenshot of Certificate.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/vault-platform-provisioning-tutorial/certificate-base64.png)

### 2. Data Integration

Next go to **Administration > Data Integration** inside Vault Platform

![Screenshot of Data Integration page.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/vault-platform-provisioning-tutorial/data-integration.png)

1. For **Data Integration** select `Azure`.
2. For **Method of providing SCIM secret location** set `bearer`.
3. For **Secret** set a complex string, similar to a strong password. Keep this string secure as it's used later on at **Step 5**
4. Toggle **Set as active SCIM Provider** to be active.

## Step 3: Add Vault Platform from the Microsoft Entra application gallery

Add Vault Platform from the Microsoft Entra application gallery to start managing provisioning to Vault Platform. If you have previously setup Vault Platform for SSO you can use the same application. However it's recommended that you create a separate app when testing out the integration initially. Learn more about adding an application from the gallery [here](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/add-application-portal).

## Step 4: Define who is in scope for provisioning

The Microsoft Entra provisioning service allows you to scope who is provisioned based on assignment to the application, or based on attributes of the user or group. If you choose to scope who is provisioned to your app based on assignment, you can use the [steps to assign users and groups to the application](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/assign-user-or-group-access-portal). If you choose to scope who is provisioned based solely on attributes of the user or group, you can [use a scoping filter](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts).

- Start small. Test with a small set of users and groups before rolling out to everyone. When scope for provisioning is set to assigned users and groups, you can control this by assigning one or two users or groups to the app. When scope is set to all users and groups, you can specify an [attribute based scoping filter](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts).
- If you need extra roles, you can [update the application manifest](https://learn.microsoft.com/en-us/entra/identity-platform/howto-add-app-roles-in-apps) to add new roles.

## Step 5: Configure automatic user provisioning to Vault Platform

This section guides you through the steps to configure the Microsoft Entra provisioning service to create, update, and disable users in TestApp based on user and/or group assignments in Microsoft Entra ID.

### Configure automatic user provisioning for Vault Platform in Microsoft Entra ID

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps**

   ![Screenshot of Enterprise applications blade.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/enterprise-applications.png)

3. In the applications list, select **Vault Platform**.

   ![Screenshot of the Vault Platform link in the Applications list.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/all-applications.png)

4. Select the **Provisioning** tab.

   ![Screenshot of Provisioning tab.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/provisioning.png)

5. Select **+ New configuration**.

   ![Screenshot of new configuration.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/application-provisioning.png)

6. Under the **Admin Credentials** section, input your Vault Platform Tenant URL \(URL with structure `https://app.vaultplatform.com/api/scim/${organization-slug}`\) and Secret Token \(from Step 2.2\). Select **Test Connection** to ensure Microsoft Entra ID can connect to Vault Platform. If the connection fails, ensure your Vault Platform account has Admin permissions and try again.

   ![Screenshot of Token.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/provisioning-testconnection-tenanturltoken.png)

7. Select **Create** to create your configuration.
8. Select **Properties** on the **Overview** page.
9. Select the **Edit** icon to edit the properties. Enable notification emails and provide an email to receive quarantine notifications. Enable **Accidental deletions prevention**. Select **Apply** to save the changes.

   ![Screenshot of Provisioning properties.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/provisioning-properties.png)

10. Select **Attribute Mapping** in the left panel and select **users**.
11. Review the user attributes that are synchronized from Microsoft Entra ID to Vault Platform in the **Attribute-Mapping** section. The attributes selected as **Matching** properties are used to match the user accounts in Vault Platform for update operations. If you choose to change the [matching target attribute](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/customize-application-attributes), you need to ensure that the Vault Platform API supports filtering users based on that attribute. Select the **Save** button to commit any changes.
    | Attribute | Type | Supported for filtering | Required by Vault Platform |
    | --- | --- | --- | --- |
    | userName | String | ✓ | ✓ |
    | externalId | String | ✓ | ✓ |
    | active | Boolean |  | ✓ |
    | displayName | String |  |  |
    | title | String |  | ✓ |
    | emails\[type eq "work"\].value | String |  | ✓ |
    | name.givenName | String |  | ✓ |
    | name.familyName | String |  | ✓ |
    | addresses\[type eq "work"\].locality | String |  | ✓ |
    | addresses\[type eq "work"\].country | String |  | ✓ |
    | urn:ietf:params:scim:schemas:extension:enterprise:2.0:User:employeeNumber | String |  | ✓ |
    | urn:ietf:params:scim:schemas:extension:enterprise:2.0:User:department | String |  | ✓ |
    | urn:ietf:params:scim:schemas:extension:enterprise:2.0:User:manager | String |  |  |
    | userType | String |  |  |
    | urn:ietf:params:scim:schemas:extension:enterprise:2.0:User:division | String |  |  |
    | urn:ietf:params:scim:schemas:extension:enterprise:2.0:User:organization | String |  |  |


    Note


    The attribute "externalID" is only sent to Vault on object creation and will not be updated if changed in Entra ID.

12. To configure scoping filters, refer to the instructions provided in the [Scoping filter article](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts).
13. Use [on-demand provisioning](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/provision-on-demand) to validate sync with a small number of users before deploying more broadly in your organization.
14. When you're ready to provision, select **Start Provisioning** from the **Overview** page.

## Step 6: Monitor your deployment

Once you configure provisioning, use the following resources to monitor your deployment:

1. Use the [provisioning logs](https://learn.microsoft.com/en-us/entra/identity/monitoring-health/concept-provisioning-logs) to determine which users are provisioned successfully or unsuccessfully
2. Check the [progress bar](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/application-provisioning-when-will-provisioning-finish-specific-user) to see the status of the provisioning cycle and how close it's to completion
3. If the provisioning configuration seems to be in an unhealthy state, the application goes into quarantine. Learn more about quarantine states the [application provisioning quarantine status](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/application-provisioning-quarantine-status) article.

## More resources

- [Managing user account provisioning for Enterprise Apps](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/configure-automatic-user-provisioning-portal)
- [What is application access and single sign-on with Microsoft Entra ID?](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/what-is-single-sign-on)

## Related content

- [Learn how to review logs and get reports on provisioning activity](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/check-status-user-account-provisioning)
