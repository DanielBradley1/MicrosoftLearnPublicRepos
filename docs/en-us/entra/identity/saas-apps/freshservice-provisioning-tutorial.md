<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/freshservice-provisioning-tutorial -->
<!-- Sitemap-Last-Modified: 2026-04-10 -->

# Configure Freshservice Provisioning for automatic user provisioning with Microsoft Entra ID

This article describes the steps you need to perform in both Freshservice Provisioning and Microsoft Entra ID to configure automatic user provisioning. When configured, Microsoft Entra ID automatically provisions and de-provisions users to [Freshservice Provisioning](https://effy.co.in/) using the Microsoft Entra provisioning service. For important details on what this service does, how it works, and frequently asked questions, see [Automate user provisioning and deprovisioning to SaaS applications with Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/user-provisioning).

## Capabilities supported

- Create users in Freshservice Provisioning
- Remove users in Freshservice Provisioning when they don't require access anymore
- Keep user attributes synchronized between Microsoft Entra ID and Freshservice Provisioning
- Long lived bearer token authentication supported.

## Prerequisites

The scenario outlined in this article assumes that you already have the following prerequisites:

- A Microsoft Entra user account with an active subscription. If you don't already have one, you can [Create an account for free](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
- One of the following roles:

  - [Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#application-administrator)
  - [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator)
  - [Application Owner](https://learn.microsoft.com/en-us/entra/fundamentals/users-default-permissions#owned-enterprise-applications).

- A [Freshservice account](https://www.freshservice.com) with the Organizational Admin permissions.

## Step 1: Plan your provisioning deployment

1. Learn about [how the provisioning service works](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/user-provisioning).
2. Determine who's in [scope for provisioning](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts).
3. Determine what data to [map between Microsoft Entra ID and Freshservice Provisioning](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/customize-application-attributes).

## Step 2: Configure Freshservice Provisioning to support provisioning with Microsoft Entra ID

1. On your Freshservice account, install the **Azure Provisioning \(SCIM\)** app from the marketplace by navigating to **Freshservice Admin** > **Apps** > **Get Apps**.
2. In the configuration screen, provide your **Freshservice Domain** \(for example, `acme.freshservice.com`\) and the **Organization Admin API key**.
3. Select **Continue**.
4. Highlight and copy the **Bearer Token**. This value is entered in the **Secret Token** field in the Provisioning tab of your Freshservice Provisioning application.
5. Select **Install** to complete the installation.
6. The **Tenant URL** is `https://scim.freshservice.com/scim/v2`. This value is entered in the **Tenant URL** field in the Provisioning tab of your Freshservice Provisioning application.

## Step 3: Add Freshservice Provisioning from the Microsoft Entra application gallery

Add Freshservice Provisioning from the Microsoft Entra application gallery to start managing provisioning to Freshservice Provisioning. Learn more about adding an application from the gallery [here](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/add-application-portal).

## Step 4: Define who is in scope for provisioning

The Microsoft Entra provisioning service allows you to scope who is provisioned based on assignment to the application, or based on attributes of the user or group. If you choose to scope who is provisioned to your app based on assignment, you can use the [steps to assign users and groups to the application](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/assign-user-or-group-access-portal). If you choose to scope who is provisioned based solely on attributes of the user or group, you can [use a scoping filter](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts).

- Start small. Test with a small set of users and groups before rolling out to everyone. When scope for provisioning is set to assigned users and groups, you can control this by assigning one or two users or groups to the app. When scope is set to all users and groups, you can specify an [attribute based scoping filter](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts).
- If you need extra roles, you can [update the application manifest](https://learn.microsoft.com/en-us/entra/identity-platform/howto-add-app-roles-in-apps) to add new roles.

## Step 5: Configure automatic user provisioning to Freshservice Provisioning

This section guides you through the steps to configure the Microsoft Entra provisioning service to create, update, and disable users in Freshservice Provisioning based on user assignments in Microsoft Entra ID.

### To configure automatic user provisioning for Freshservice Provisioning in Microsoft Entra ID

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps**

   ![Enterprise applications blade](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/enterprise-applications.png)

3. In the applications list, select **Freshservice Provisioning**.

   ![The Freshservice Provisioning link in the Applications list](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/all-applications.png)

4. Select the **Provisioning** tab.

   ![Provisioning tab](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/provisioning.png)

5. Select **+ New configuration**.

   ![Screenshot of Provisioning tab automatic.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/application-provisioning.png)

6. In the **Tenant URL** field, enter your Freshservice Provisioning Tenant URL and Secret Token. Select **Test Connection** to ensure Microsoft Entra ID can connect to Freshservice Provisioning. If the connection fails, ensure your Freshservice Provisioning account has the required admin permissions and try again.

   ![Screenshot of Provisioning test connection.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/provisioning-test-connection.png)

7. Select **Create** to create your configuration.
8. Select **Properties** on the **Overview** page.
9. In the **Notification Email** field, enter the email address of a person who should receive the provisioning error notifications and select the **Send an email notification when a failure occurs** check box.

   ![Screenshot of Provisioning properties.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/provisioning-properties.png)

10. Select **Attribute Mapping** in the left panel and select **users**.
11. Review the user attributes that are synchronized from Microsoft Entra ID to Freshservice Provisioning in the **Attribute-Mapping** section. The attributes selected as **Matching** properties are used to match the user accounts in Freshservice Provisioning for update operations. If you choose to change the [matching target attribute](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/customize-application-attributes), you need to ensure that the Freshservice Provisioning API supports filtering users based on that attribute. Select the **Save** button to commit any changes.
    | Attribute | Type | Supported For Filtering |
    | --- | --- | --- |
    | userName | String | ✓ |
    | active | Boolean |  |
    | emails\[type eq "work"\].value | String |  |
    | displayName | String |  |
    | name.givenName | String |  |
    | name.familyName | String |  |
    | phoneNumbers\[type eq "work"\].value | String |  |
    | phoneNumbers\[type eq "mobile"\].value | String |  |
    | addresses\[type eq "work"\].formatted | String |  |
    | locale | String |  |
    | title | String |  |
    | timezone | String |  |
    | externalId | String |  |
    | urn:ietf:params:scim:schemas:extension:enterprise:2.0:User:department | String |  |
    | urn:ietf:params:scim:schemas:extension:enterprise:2.0:User:manager | Reference |  |
    | urn:ietf:params:scim:schemas:extension:freshservice:2.0:User:isAgent | String |  |

Note

Custom extension attributes can be added to your schema to meet your application's needs by following the below steps:

- Under Mappings, select **Provision Microsoft Entra users**.
- At the bottom of the page, select **Show advanced options**.
- Select **Edit attribute list for Freshservice**.
- At the bottom of the attribute list, enter information about the custom attribute in the fields provided. The custom attribute urn namespace must follow the pattern as shown in the below example. The **CustomAttribute** can be customized per your application's requirements, for example: urn:ietf:params:scim:schemas:extension:freshservice:2.0:User:**isAgent**.
- The appropriate data type has to be selected for the custom attribute and select **Save**.
- Navigate back to the default mappings screen and select **Add New Mapping**. The custom attributes will show up in the **Target Attribute** list dropdown.

1. To configure scoping filters, refer to the instructions provided in the [Scoping filter article](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts).
2. Use [on-demand provisioning](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/provision-on-demand) to validate sync with a small number of users before deploying more broadly in your organization.
3. When you're ready to provision, select **Start Provisioning** from the **Overview** page.

## Step 6: Monitor your deployment

Once you configure provisioning, use the following resources to monitor your deployment:

1. Use the [provisioning logs](https://learn.microsoft.com/en-us/entra/identity/monitoring-health/concept-provisioning-logs) to determine which users are provisioned successfully or unsuccessfully
2. Check the [progress bar](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/application-provisioning-when-will-provisioning-finish-specific-user) to see the status of the provisioning cycle and how close it's to completion
3. If the provisioning configuration seems to be in an unhealthy state, the application goes into quarantine. Learn more about quarantine states the [application provisioning quarantine status](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/application-provisioning-quarantine-status) article.

## Additional resources

- [Managing user account provisioning for Enterprise Apps](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/configure-automatic-user-provisioning-portal)
- [What is application access and single sign-on with Microsoft Entra ID?](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/what-is-single-sign-on)

## Related content

- [Learn how to review logs and get reports on provisioning activity](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/check-status-user-account-provisioning)
