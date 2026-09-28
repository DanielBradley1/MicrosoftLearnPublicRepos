<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/oracle-cloud-infrastructure-console-provisioning-tutorial -->
<!-- Sitemap-Last-Modified: 2026-04-28 -->

# Configure Oracle Cloud Infrastructure Console for automatic user provisioning with Microsoft Entra ID

Note

Integrating with Oracle Cloud Infrastructure Console or Oracle IDCS with a custom / BYOA application isn't supported. Using the gallery application as described in this article is supported. The gallery application has been customized to work with the Oracle SCIM server.

This article describes the steps you need to perform in both Oracle Cloud Infrastructure Console and Microsoft Entra ID to configure automatic user provisioning. When configured, Microsoft Entra ID automatically provisions and deprovisions users and groups to [Oracle Cloud Infrastructure Console](https://www.oracle.com/cloud/free/?source=:ow:o:p:nav:0916BCButton&intcmp=:ow:o:p:nav:0916BCButton) using the Microsoft Entra provisioning service. For important details on what this service does, how it works, and frequently asked questions, see [Automate user provisioning and deprovisioning to SaaS applications with Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/user-provisioning).

## Capabilities supported

- Create users in Oracle Cloud Infrastructure Console
- Remove users in Oracle Cloud Infrastructure Console when they don't require access anymore
- Keep user attributes synchronized between Microsoft Entra ID and Oracle Cloud Infrastructure Console
- Provision groups and group memberships in Oracle Cloud Infrastructure Console
- [Single sign-on](https://learn.microsoft.com/en-us/entra/identity/saas-apps/oracle-cloud-tutorial) to Oracle Cloud Infrastructure Console \(recommended\)

## Prerequisites

The scenario outlined in this article assumes that you already have the following prerequisites:

- 

  - A Microsoft Entra user account with an active subscription. If you don't already have one, you can [Create an account for free](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
  - One of the following roles:

    - [Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#application-administrator)
    - [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator)
    - [Application Owner](https://learn.microsoft.com/en-us/entra/fundamentals/users-default-permissions#owned-enterprise-applications).

- An Oracle Cloud Infrastructure Console [tenant](https://www.oracle.com/cloud/sign-in.html?intcmp=OcomFreeTier&source=:ow:o:p:nav:0916BCButton).
- A user account in Oracle Cloud Infrastructure Console with Admin permissions.

Note

This integration is also available to use from Microsoft Entra US Government Cloud environment. You can find this application in the Microsoft Entra US Government Cloud Application Gallery and configure it in the same way as you do from public cloud

## Step 1: Plan your provisioning deployment

1. Learn about [how the provisioning service works](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/user-provisioning).
2. Determine who's in [scope for provisioning](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts).
3. Determine what data to [map between Microsoft Entra ID and Oracle Cloud Infrastructure Console](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/customize-application-attributes).

## Step 2: Configure Oracle Cloud Infrastructure Console to support provisioning with Microsoft Entra ID

1. Log on to the Oracle Cloud Infrastructure Console admin portal. On the top left corner of the screen navigate to **Identity > Federation**.

   ![Screenshot shows the Oracle Admin console for identity management.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/oracle-cloud-infratstructure-console-provisioning-tutorial/identity.png "Admin")

2. Select the URL displayed on the page beside Oracle Identity Cloud Service Console.
3. Select **Add Identity Provider** to create a new identity provider. Save the IdP ID to be used as a part of tenant URL. Select the plus icon beside the **Applications** tab to create an OAuth Client and Grant IDCS Identity Domain Administrator AppRole.

   ![Screenshot shows the Oracle Cloud Icon for adding applications.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/oracle-cloud-infratstructure-console-provisioning-tutorial/add.png "Icon")

4. Follow the screenshots below to configure your application. When the configuration is done, select **Save**.

   ![Screenshot shows the Oracle Configuration.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/oracle-cloud-infratstructure-console-provisioning-tutorial/configuration.png "Configuration")


   ![Screenshot shows the Oracle Token Issuance Policy.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/oracle-cloud-infratstructure-console-provisioning-tutorial/token-issuance.png "Policy")

5. Under the configurations tab of your application expand the **General Information** option to retrieve the client ID and client secret.

   ![Screenshot shows the Oracle token generation.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/oracle-cloud-infratstructure-console-provisioning-tutorial/general-information.png "Token")

6. To generate a secret token, encode the client ID and client secret as Base64 in the format **client ID:Client Secret**. Note - this value must be generated with line wrapping disabled \(base64 -w 0\). Save the secret token. This value is entered in the **Secret Token** field in the provisioning tab of your Oracle Cloud Infrastructure Console application.

## Step 3: Add Oracle Cloud Infrastructure Console from the Microsoft Entra application gallery

Add Oracle Cloud Infrastructure Console from the Microsoft Entra application gallery to start managing provisioning to Oracle Cloud Infrastructure Console. If you have previously setup Oracle Cloud Infrastructure Console for SSO you can use the same application. However, we recommend that you create a separate app when testing out the integration initially. Learn more about adding an application from the gallery [here](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/add-application-portal).

## Step 4: Define who is in scope for provisioning

The Microsoft Entra provisioning service allows you to scope who's provisioned based on assignment to the application and or based on attributes of the user / group. If you choose to scope who's provisioned to your app based on assignment, you can use the following [steps](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/assign-user-or-group-access-portal) to assign users and groups to the application. If you choose to scope who's provisioned based solely on attributes of the user or group, you can use a scoping filter as described [here](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts).

- If you need additional roles, you can [update the application manifest](https://learn.microsoft.com/en-us/entra/identity-platform/howto-add-app-roles-in-apps) to add new roles.
- If you need additional roles, you can [update the application manifest](https://learn.microsoft.com/en-us/entra/identity-platform/howto-add-app-roles-in-apps) to add new roles.

## Step 5: Configure automatic user provisioning to Oracle Cloud Infrastructure Console

This section guides you through the steps to configure the Microsoft Entra provisioning service to create, update, and disable users and/or groups in TestApp based on user and/or group assignments in Microsoft Entra ID.

### To configure automatic user provisioning for Oracle Cloud Infrastructure Console in Microsoft Entra ID:

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps**

   ![Screenshot shows the enterprise applications blade.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/enterprise-applications.png "Blade")

3. In the applications list, select **Oracle Cloud Infrastructure Console**.

   ![Screenshot shows the Oracle Cloud Infrastructure Console link in the Applications list.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/all-applications.png "List")

4. Select the **Provisioning** tab.

   ![Screenshot of the Manage options with the Provisioning option called out.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/provisioning.png "Provisioning")

5. Select **+ New configuration**.

   ![Screenshot of Provisioning tab automatic.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/application-provisioning.png)

6. In the **Tenant URL** field, enter your Oracle Cloud Infrastructure Console Tenant URL and Secret Token. Select **Test Connection** to ensure Microsoft Entra ID can connect to Oracle Cloud Infrastructure Console. If the connection fails, ensure your Oracle Cloud Infrastructure Console account has the required admin permissions and try again.

   Note

   Enter `https://<IdP ID>.identity.oraclecloud.com/admin/v1` in the **Tenant URL**. Example: If your IdP ID is `idcs-0bfd023ff2xx4a98a760fa2c31k92b1d`, then you would enter `https://idcs-0bfd023ff2xx4a98a760fa2c31k92b1d.identity.oraclecloud.com/admin/v1` in the **Tenant URL**.

   ![Screenshot of Provisioning test connection.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/provisioning-test-connection.png)

7. Select **Create** to create your configuration.
8. Select **Properties** on the **Overview** page.
9. In the **Notification Email** field, enter the email address of a person who should receive the provisioning error notifications and select the **Send an email notification when a failure occurs** check box.

   ![Screenshot of Provisioning properties.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/provisioning-properties.png)

10. Select **Attribute Mapping** in the left panel and select **users**.
11. Review the user attributes that are synchronized from Microsoft Entra ID to Oracle Cloud Infrastructure Console in the **Attribute-Mapping** section. The attributes selected as **Matching** properties are used to match the user accounts in Oracle Cloud Infrastructure Console for update operations. If you choose to change the [matching target attribute](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/customize-application-attributes), you need to ensure that the Oracle Cloud Infrastructure Console API supports filtering users based on that attribute. Select the **Save** button to commit any changes.
    | Attribute | Type |
    | --- | --- |
    | displayName | String |
    | userName | String |
    | active | Boolean |
    | title | String |
    | emails\[type eq "work"\].value | String |
    | preferredLanguage | String |
    | name.givenName | String |
    | name.familyName | String |
    | addresses\[type eq "work"\].formatted | String |
    | addresses\[type eq "work"\].locality | String |
    | addresses\[type eq "work"\].region | String |
    | addresses\[type eq "work"\].postalCode | String |
    | addresses\[type eq "work"\].country | String |
    | addresses\[type eq "work"\].streetAddress | String |
    | urn:ietf:params:scim:schemas:extension:enterprise:2.0:User:employeeNumber | String |
    | urn:ietf:params:scim:schemas:extension:enterprise:2.0:User:department | String |
    | urn:ietf:params:scim:schemas:extension:enterprise:2.0:User:costCenter | String |
    | urn:ietf:params:scim:schemas:extension:enterprise:2.0:User:division | String |
    | urn:ietf:params:scim:schemas:extension:enterprise:2.0:User:manager | Reference |
    | urn:ietf:params:scim:schemas:extension:enterprise:2.0:User:organization | String |
    | urn:ietf:params:scim:schemas:oracle:idcs:extension:user:User:bypassNotification | Boolean |
    | urn:ietf:params:scim:schemas:oracle:idcs:extension:user:User:isFederatedUser | Boolean |


    Note


    Oracle Cloud Infrastructure Console's SCIM endpoint expects `addresses[type eq "work"].country` MUST be in ISO 3166-1 "alpha-2" code format \(for example US,UK, and so on\). Before starting provisioning please check to make sure that all users have their respective "Country or region" field value set in the expected format or else that particular user provisioning will fail. ![Screenshot shows the contact information.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/oracle-cloud-infratstructure-console-provisioning-tutorial/contact.png "Contact")


    Note


    The extension attributes "urn:ietf:params:scim:schemas:oracle:idcs:extension:user:User:bypassNotification" and "urn:ietf:params:scim:schemas:oracle:idcs:extension:user:User:isFederatedUser" are the only custom extension attributes supported in that format. Additional extension attributes should follow the format of urn:ietf:params:scim:schemas:extension:CustomExtensionName:2.0:User:CustomAttribute.

12. Review the group attributes that are synchronized from Microsoft Entra ID to Oracle Cloud Infrastructure Console in the **Attribute-Mapping** section. The attributes selected as **Matching** properties are used to match the groups in Oracle Cloud Infrastructure Console for update operations. Select the **Save** button to commit any changes.
    | Attribute | Type |
    | --- | --- |
    | displayName | String |
    | externalId | String |
    | members | Reference |
13. To configure scoping filters, refer to the instructions provided in the [Scoping filter article](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts).
14. Use [on-demand provisioning](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/provision-on-demand) to validate sync with a small number of users before deploying more broadly in your organization.
15. When you're ready to provision, select **Start Provisioning** from the **Overview** page.

## Step 6: Monitor your deployment

Once you've configured provisioning, use the following resources to monitor your deployment:

- Use the [provisioning logs](https://learn.microsoft.com/en-us/entra/identity/monitoring-health/concept-provisioning-logs) to determine which users have been provisioned successfully or unsuccessfully
- Check the [progress bar](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/application-provisioning-when-will-provisioning-finish-specific-user) to see the status of the provisioning cycle and how close it's to completion
- If the provisioning configuration seems to be in an unhealthy state, the application will go into quarantine. Learn more about quarantine states [here](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/application-provisioning-quarantine-status).

## Change log

08/15/2023 - The app was added to Gov Cloud.

## More resources

- [Managing user account provisioning for Enterprise Apps](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/configure-automatic-user-provisioning-portal)
- [What is application access and single sign-on with Microsoft Entra ID?](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/what-is-single-sign-on)

## Related content

- [Learn how to review logs and get reports on provisioning activity](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/check-status-user-account-provisioning)
