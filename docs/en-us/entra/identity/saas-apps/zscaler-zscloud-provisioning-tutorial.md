<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/zscaler-zscloud-provisioning-tutorial -->
<!-- Sitemap-Last-Modified: 2026-06-11 -->

# Configure Zscaler ZSCloud for automatic user provisioning with Microsoft Entra ID

In this article, you learn how to configure Microsoft Entra ID to automatically provision and deprovision users and/or groups to Zscaler ZSCloud.

Note

This article describes a connector that's built on the Microsoft Entra user provisioning service. For important details on what this service does and how it works, and answers to frequently asked questions, see [Automate user provisioning and deprovisioning to SaaS applications with Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/user-provisioning).

Zscaler ZSCloud is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government | China operated by 21Vianet |
| :---: | :---: | :---: |
| ✅ |  | ✅ |

## Prerequisites

To complete the steps outlined in this article, you need the following:

- A Microsoft Entra user account with an active subscription. If you don't already have one, you can [Create an account for free](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn). - One of the following roles: - [Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#application-administrator) - [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator) - [Application Owner](https://learn.microsoft.com/en-us/entra/fundamentals/users-default-permissions#owned-enterprise-applications)..

- A Zscaler ZSCloud tenant.
- A user account in Zscaler ZSCloud with admin permissions.

Note

The Microsoft Entra provisioning integration relies on the Zscaler ZSCloud SCIM API, which is available for Enterprise accounts.

## Step 1: Add Zscaler ZSCloud from the gallery

Before you configure Zscaler ZSCloud for automatic user provisioning with Microsoft Entra ID, you need to add Zscaler ZSCloud from the Microsoft Entra application gallery to your list of managed SaaS applications.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **New application**.

   ![Screenshot of Enterprise applications.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/enterprise-applications.png)

3. In the search box, enter **Zscaler ZSCloud**.
4. Select **Zscaler ZSCloud** in the results and then select **Add**.

   ![Screenshot of Results list.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/search-new-app.png)

## Step 2: Assign users to Zscaler ZSCloud

Microsoft Entra users need to be assigned access to selected apps before they can use them. In the context of automatic user provisioning, only the users or groups that are assigned to an application in Microsoft Entra ID are synchronized.

Before you configure and enable automatic user provisioning, you should decide which users and/or groups in Microsoft Entra ID need access to Zscaler ZSCloud. After you decide that, you can assign these users and groups to Zscaler ZSCloud by following the instructions in [Assign a user or group to an enterprise app](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/assign-user-or-group-access-portal).

### Important tips for assigning users to Zscaler ZSCloud

- We recommend that you first assign a single Microsoft Entra user to Zscaler ZSCloud to test the automatic user provisioning configuration. You can assign more users and groups later.
- When you assign a user to Zscaler ZSCloud, you need to select any valid application-specific role \(if available\) in the assignment dialog box. Users with the **Default Access** role are excluded from provisioning.

## Step 3: Set up automatic user provisioning

This section guides you through the steps for configuring the Microsoft Entra provisioning service to create, update, and disable users and groups in Zscaler ZSCloud based on user and group assignments in Microsoft Entra ID.

Tip

You might also want to enable SAML-based single sign-on for Zscaler ZSCloud. If you do, follow the instructions in the [Zscaler ZSCloud single sign-on article](https://learn.microsoft.com/en-us/entra/identity/saas-apps/zscaler-zscloud-tutorial). Single sign-on can be configured independently of automatic user provisioning, but the two features complement each other.

Note

When users and groups are provisioned or de-provisioned we recommend to periodically restart provisioning to ensure that group memberships are properly updated. Doing a restart will force our service to re-evaluate all the groups and update the memberships.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **Zscaler ZSCloud**.
3. Select the **Provisioning** tab:

   ![Screenshot of Zscaler ZSCloud Provisioning.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/zscaler-zscloud-provisioning-tutorial/provisioningtab.png)

4. Select **+ New configuration**.

   ![Screenshot of new configuration.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/application-provisioning.png)

5. In the **Admin Credentials** section, enter the **Tenant URL** and **Secret Token** of your Zscaler ZSCloud account, as described in the next step.
6. To get the **Tenant URL** and **Secret Token**, go to **Administration** > **Authentication Settings** in the Zscaler ZSCloud portal and select **SAML** under **Authentication Type**:

   ![Screenshot of Zscaler ZSCloud Authentication Settings.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/zscaler-zscloud-provisioning-tutorial/secrettoken1.png)

7. Select **Configure SAML** to open the **Configure SAML** window:

   ![Screenshot of Configure SAML window.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/zscaler-zscloud-provisioning-tutorial/secrettoken2.png)

8. Select **Enable SCIM-Based Provisioning** and copy the **Base URL** and **Bearer Token**, and then save the settings. In the Azure portal, paste the **Base URL** into the **Tenant URL** box and the **Bearer Token** into the **Secret Token** box.
9. After you enter the values in the **Tenant URL** and **Secret Token** boxes, select **Test Connection** to make sure Microsoft Entra ID can connect to Zscaler ZSCloud. If the connection fails, make sure your Zscaler ZSCloud account has admin permissions and try again.

   ![Screenshot of Token.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/provisioning-testconnection-tenanturltoken.png)

10. Select **Create** to create your configuration.
11. Select **Properties** on the **Overview** page.
12. Select the **Edit** icon to edit the properties. Enable notification emails and provide an email to receive quarantine notifications. Enable **Accidental deletions prevention**. Select **Apply** to save the changes.

    ![Screenshot of Provisioning properties.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/provisioning-properties.png)

13. Select **Attribute Mapping** in the left panel and select **users**.
14. Review the user attributes that are synchronized from Microsoft Entra ID to Zscaler ZSCloud in the **Attribute Mappings** section. The attributes selected as **Matching** properties are used to match the user accounts in Zscaler ZSCloud for update operations. Select **Save** to commit any changes.
    | Attribute | Type | Supported for filtering | Required by Zscaler ZSCloud |
    | --- | --- | --- | --- |
    | userName | String | ✓ | ✓ |
    | externalId | String |  | ✓ |
    | active | Boolean |  | ✓ |
    | name.givenName | String |  |  |
    | name.familyName | String |  |  |
    | displayName | String |  | ✓ |
    | urn:ietf:params:scim:schemas:extension:enterprise:2.0:User:department | String |  | ✓ |
15. Select **Groups**.
16. Review the group attributes that are synchronized from Microsoft Entra ID to Zscaler ZSCloud in the **Attribute Mappings** section. The attributes selected as **Matching** properties are used to match the groups in Zscaler ZSCloud for update operations. Select **Save** to commit any changes.
    | Attribute | Type | Supported for filtering | Required by Zscaler ZSCloud |
    | --- | --- | --- | --- |
    | displayName | String | ✓ | ✓ |
    | members | Reference |  |  |
    | externalId | String |  | ✓\) |
17. To configure scoping filters, refer to the instructions provided in the [Scoping filter article](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts).
18. Use [on-demand provisioning](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/provision-on-demand) to validate sync with a small number of users before deploying more broadly in your organization.
19. When you're ready to provision, select **Start Provisioning** from the **Overview** page.

## Step 4: Monitor your deployment

Once you configure provisioning, use the following resources to monitor your deployment:

1. Use the [provisioning logs](https://learn.microsoft.com/en-us/entra/identity/monitoring-health/concept-provisioning-logs) to determine which users are provisioned successfully or unsuccessfully
2. Check the [progress bar](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/application-provisioning-when-will-provisioning-finish-specific-user) to see the status of the provisioning cycle and how close it's to completion
3. If the provisioning configuration seems to be in an unhealthy state, the application goes into quarantine. Learn more about quarantine states the [application provisioning quarantine status](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/application-provisioning-quarantine-status) article.

## Additional resources

- [Managing user account provisioning for enterprise apps](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/configure-automatic-user-provisioning-portal)
- [What is application access and single sign-on with Microsoft Entra ID?](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/what-is-single-sign-on)

## Related content

- [Learn how to review logs and get reports on provisioning activity](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/check-status-user-account-provisioning)
