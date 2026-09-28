<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/jostle-provisioning-tutorial -->
<!-- Sitemap-Last-Modified: 2026-06-16 -->

# Configure Jostle for automatic user provisioning with Microsoft Entra ID

This article describes the steps you need to perform in both Jostle and Microsoft Entra ID to configure automatic user provisioning. When configured, Microsoft Entra ID automatically provisions and de-provisions users and groups to [Jostle](https://www.jostle.me/) using the Microsoft Entra provisioning service. For important details on what this service does, how it works, and frequently asked questions, see [Automate user provisioning and deprovisioning to SaaS applications with Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/user-provisioning).

## Capabilities Supported

- Create users in Jostle
- Remove users in Jostle when they don't require access anymore
- Keep user attributes synchronized between Microsoft Entra ID and Jostle
- [Single sign-on](https://learn.microsoft.com/en-us/entra/identity/saas-apps/jostle-tutorial) to Jostle \(recommended\)
- Long lived bearer token authentication supported.

## Prerequisites

The scenario outlined in this article assumes that you already have the following prerequisites:

- 

  - A Microsoft Entra user account with an active subscription. If you don't already have one, you can [Create an account for free](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
  - One of the following roles:

    - [Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#application-administrator)
    - [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator)
    - [Application Owner](https://learn.microsoft.com/en-us/entra/fundamentals/users-default-permissions#owned-enterprise-applications).

- A [Jostle tenant](https://www.jostle.me/).
- A user account in Jostle with Admin permissions.

## Step 1: Plan your provisioning deployment

1. Learn about [how the provisioning service works](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/user-provisioning).
2. Determine who's in [scope for provisioning](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts).
3. Determine what data to [map between Microsoft Entra ID and Jostle](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/customize-application-attributes).

## Step 2: Configure Jostle to support provisioning with Microsoft Entra ID

### Automation account

Before you begin, you’ll need to create an **Automation user** in your Jostle intranet. This is the account you’ll use to configure with Azure. Automation users can be created in Admin **Settings > User accounts and data > Manage Automation users**.

For more details on Automation users and how to create one, see [this article](https://forum.jostle.us/hc/en-us/articles/360057364073).

Once created, the Automation user account **must be activated** \(that is, logged in to your intranet at least once\) before it can be used to configure Azure.

### Manage user provisioning

Before you begin, ensure that your account subscription **includes SSO/user provisioning features**. If it doesn't, you can contact your Customer Success Manager [success@jostle.me](mailto:success@jostle.me) and they can assist you in adding it to your account.

The next step is to obtain the **API URL** and **API key** from Jostle:

1. Go to the Main Navigation and select **Admin Settings**.
2. Under **User data to/from other systems** select **Manage user provisioning** .If you don't see "Manage user provisioning" here and have verified that your account includes SSO/user provisioning, contact Support [support@jostle.me](mailto:support@jostle.me) to have this page enabled in your Admin Settings\).
3. In the **User Provisioning API details** section, go to **Your Base URL** field, select the Copy button and save the URL somewhere you can easily access it later.

   ![Screenshot of User Provisioning API details.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/jostle-provisioning-tutorial/manage-user-provisioning.png)

4. Next, select the **Add a new key**... button
5. On the following screen, go to the **Automation User** field and use the drop-down menu to select your Automation user account.

   ![Screenshot of Integration Account.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/jostle-provisioning-tutorial/select-integration-account.png)

6. In the **Provisioning API key description** field give your key a name \(such as `Azure`\) and then select the **Add** button.
7. Once your key is generated, **make sure to copy it right away** and save it where you saved your URL \(since it's the only time your key appears\).
8. Next, you’ll use the **API URL** and **API key** to configure the integration in Azure.

## Step 3: Add Jostle from the Microsoft Entra application gallery

Add Jostle from the Microsoft Entra application gallery to start managing provisioning to Jostle. If you have previously setup Jostle for SSO, you can use the same application. However it's recommended that you create a separate app when testing out the integration initially. Learn more about adding an application from the gallery [here](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/add-application-portal).

## Step 4: Define who is in scope for provisioning

The Microsoft Entra provisioning service allows you to scope who is provisioned based on assignment to the application, or based on attributes of the user or group. If you choose to scope who is provisioned to your app based on assignment, you can use the [steps to assign users and groups to the application](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/assign-user-or-group-access-portal). If you choose to scope who is provisioned based solely on attributes of the user or group, you can [use a scoping filter](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts).

- Start small. Test with a small set of users and groups before rolling out to everyone. When scope for provisioning is set to assigned users and groups, you can control this by assigning one or two users or groups to the app. When scope is set to all users and groups, you can specify an [attribute based scoping filter](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts).
- If you need extra roles, you can [update the application manifest](https://learn.microsoft.com/en-us/entra/identity-platform/howto-add-app-roles-in-apps) to add new roles.

## Step 5: Configure automatic user provisioning to Jostle

This section guides you through the steps to configure the Microsoft Entra provisioning service to create, update, and disable users and groups in Jostle app based on user and group assignments in Microsoft Entra ID.

Note

For more information on automatic user provisioning to Jostle, see [User-Provisioning-Azure-Integration](https://forum.jostle.us/hc/en-us/articles/360056368534-User-Provisioning-Azure-Integration).

### To configure automatic user provisioning for Jostle in Microsoft Entra ID:

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps**

   ![Screenshot of Enterprise applications blade.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/enterprise-applications.png)

3. In the applications list, select **Jostle**.

   ![Screenshot of the Jostle link in the Applications list.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/all-applications.png)

4. Select the **Provisioning** tab and select **Get Started**.

   ![Screenshot of the Provisioning tab.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/provisioning.png)

5. Select **+ New configuration**.

   ![Screenshot of Provisioning tab automatic.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/application-provisioning.png)

6. In the **Tenant URL** field, enter your Jostle Tenant URL and Secret Token. Select **Test Connection** to ensure Microsoft Entra ID can connect to Jostle. If the connection fails, ensure your Jostle account has the required admin permissions and try again.

   ![Screenshot of Provisioning test connection.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/provisioning-test-connection.png)

7. Select **Create** to create your configuration.
8. Select **Properties** on the **Overview** page.
9. In the **Notification Email** field, enter the email address of a person who should receive the provisioning error notifications and select the **Send an email notification when a failure occurs** check box.

   ![Screenshot of Provisioning properties.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/provisioning-properties.png)

10. Select **Attribute Mapping** in the left panel and select **users**.
11. Review the user attributes that are synchronized from Microsoft Entra ID to Jostle in the **Attribute-Mapping** section. The attributes selected as **Matching** properties are used to match the user accounts in Jostle for update operations. If you choose to change the [matching target attribute](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/customize-application-attributes), you need to ensure that the Jostle API supports filtering users based on that attribute. Select the **Save** button to commit any changes.
    | Attribute | Type | Supported for filtering |
    | --- | --- | --- |
    | userName | String | ✓ |
    | active | Boolean |  |
    | name.givenName | String |  |
    | name.familyName | String |  |
    | emails\[type eq "work"\].value | String |  |
    | emails\[type eq "personal"\].value | String |  |
    | emails\[type eq "alternate1"\].value | String |  |
    | emails\[type eq "alternate2"\].value | String |  |
    | urn:ietf:params:scim:schemas:extension:jostle:2.0:User:alternateEmail1Label | String |  |
    | urn:ietf:params:scim:schemas:extension:jostle:2.0:User:alternateEmail2Label | String |  |
    | DisplayName | String |  |
    | ExternalIdentifier | String |  |
    | Title | String |  |
    | Nickname | String |  |
    | UserType | String |  |
    | BirthDate | String |  |
    | urn:ietf:params:scim:schemas:extension:jostle:2.0:User:CustomBadge | String |  |
    | urn:ietf:params:scim:schemas:extension:jostle:2.0:User:CustomFilterCategory | String |  |
    | urn:ietf:params:scim:schemas:extension:jostle:2.0:User:CustomProfile | String |  |
    | urn:ietf:params:scim:schemas:extension:jostle:2.0:User:JoinDate | String |  |
    | urn:ietf:params:scim:schemas:extension:jostle:2.0:User:Locations | String |  |
    | urn:ietf:params:scim:schemas:extension:jostle:2.0:User:LoginType | String |  |
    | urn:ietf:params:scim:schemas:extension:jostle:2.0:User:PersonalPronouns | String |  |
    | urn:ietf:params:scim:schemas:extension:jostle:2.0:User:Address1Country | String |  |
    | urn:ietf:params:scim:schemas:extension:jostle:2.0:User:Address1Locality | String |  |
    | urn:ietf:params:scim:schemas:extension:jostle:2.0:User:Address1PostalCode | String |  |
    | urn:ietf:params:scim:schemas:extension:jostle:2.0:User:Address1StreetAddress | String |  |
    | urn:ietf:params:scim:schemas:extension:jostle:2.0:User:Address1Region | String |  |
    | urn:ietf:params:scim:schemas:extension:jostle:2.0:User:Address2Country | String |  |
    | urn:ietf:params:scim:schemas:extension:jostle:2.0:User:Address2Locality | String |  |
    | urn:ietf:params:scim:schemas:extension:jostle:2.0:User:Address2PostalCode | String |  |
    | urn:ietf:params:scim:schemas:extension:jostle:2.0:User:Address2StreetAddress | String |  |
    | urn:ietf:params:scim:schemas:extension:jostle:2.0:User:Address2Region | String |  |
    | phoneNumbers\[type eq "workofficephone"\].value | String |  |
    | phoneNumbers\[type eq "homephone"\].value | String |  |
    | phoneNumbers\[type eq "workmobilephone"\].value | String |  |
    | phoneNumbers\[type eq "personalmobilephone"\].value | String |  |
12. To configure scoping filters, refer to the instructions provided in the [Scoping filter article](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts).
13. Use [on-demand provisioning](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/provision-on-demand) to validate sync with a small number of users before deploying more broadly in your organization.
14. When you're ready to provision, select **Start Provisioning** from the **Overview** page.

## Step 6: Monitor your deployment

Once you configure provisioning, use the following resources to monitor your deployment:

1. Use the [provisioning logs](https://learn.microsoft.com/en-us/entra/identity/monitoring-health/concept-provisioning-logs) to determine which users are provisioned successfully or unsuccessfully
2. Check the [progress bar](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/application-provisioning-when-will-provisioning-finish-specific-user) to see the status of the provisioning cycle and how close it's to completion
3. If the provisioning configuration seems to be in an unhealthy state, the application goes into quarantine. Learn more about quarantine states the [application provisioning quarantine status](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/application-provisioning-quarantine-status) article.

## More resources

- [Managing user account provisioning for enterprise apps](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/configure-automatic-user-provisioning-portal)
- [What is application access and single sign-on with Microsoft Entra ID?](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/what-is-single-sign-on)

## Related content

- [Learn how to review logs and get reports on provisioning activity](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/check-status-user-account-provisioning)
