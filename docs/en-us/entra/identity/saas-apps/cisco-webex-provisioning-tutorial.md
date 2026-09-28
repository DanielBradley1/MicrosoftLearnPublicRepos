<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/cisco-webex-provisioning-tutorial -->
<!-- Sitemap-Last-Modified: 2026-05-26 -->

# Configure Cisco Webex for automatic user provisioning with Microsoft Entra ID

The objective of this article is to demonstrate the steps to be performed in Cisco Webex and Microsoft Entra ID to configure Microsoft Entra ID to automatically provision and deprovision users to Cisco Webex.

Note

This article describes a connector built on top of the Microsoft Entra user provisioning service. For important details on what this service does, how it works, and frequently asked questions, see [Automate user provisioning and deprovisioning to SaaS applications with Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/user-provisioning).

This connector is currently in Preview. For more information about previews, see [Universal License Terms For Online Services](https://www.microsoft.com/licensing/terms/product/ForOnlineServices/all).

Cisco Webex is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government | China operated by 21Vianet |
| :---: | :---: | :---: |
| ✅ | ✅ |  |

## Capabilities supported

- Create users in Cisco Webex.
- Remove users in Cisco Webex when they don't require access anymore.
- Keep user attributes synchronized between Microsoft Entra ID and Cisco Webex.
- Provision groups and group memberships in Cisco Webex.
- [Single sign-on](https://learn.microsoft.com/en-us/entra/identity/saas-apps/cisco-webex-tutorial) to Cisco Webex \(recommended\).
- Long lived bearer token authentication supported.

## Prerequisites

The scenario outlined in this article assumes that you already have the following prerequisites:

- A Microsoft Entra user account with an active subscription. If you don't already have one, you can [Create an account for free](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn). - One of the following roles: - [Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#application-administrator) - [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator) - [Application Owner](https://learn.microsoft.com/en-us/entra/fundamentals/users-default-permissions#owned-enterprise-applications)..

- [A Cisco Webex tenant](https://www.webex.com/pricing/index.html).
- A user account in Cisco Webex with Admin permissions.

## Adding Cisco Webex from the gallery

Before configuring Cisco Webex for automatic user provisioning with Microsoft Entra ID, you need to add Cisco Webex from the Microsoft Entra application gallery to your list of managed SaaS applications.

**To add Cisco Webex from the Microsoft Entra application gallery, perform the following steps:**

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **New application**.
3. In the **Add from the gallery** section, type **Cisco Webex**, select **Cisco Webex** from result panel then select **Add** button to add the application.

   ![Screenshot shows the Cisco Webex in the results list.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/cisco-webex-provisioning-tutorial/search-cisco-app.png)

## Assigning users to Cisco Webex

Microsoft Entra ID uses a concept called "assignments" to determine which users should receive access to selected apps. In the context of automatic user provisioning, only the users and/or groups that have been "assigned" to an application in Microsoft Entra ID are synchronized.

Before configuring and enabling automatic user provisioning, you should decide which users in Microsoft Entra ID need access to Cisco Webex. Once decided, you can assign these users to Cisco Webex by following the instructions here:

- [Assign a user or group to an enterprise app](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/assign-user-or-group-access-portal)

### Important tips for assigning users to Cisco Webex

- It's recommended that a single Microsoft Entra user is assigned to Cisco Webex to test the automatic user provisioning configuration. Additional users may be assigned later.
- When assigning a user to Cisco Webex, you must select any valid application-specific role \(if available\) in the assignment dialog. Users with the **Default Access** role are excluded from provisioning.

## Configuring automatic user provisioning to Cisco Webex

This section guides you through the steps to configure the Microsoft Entra provisioning service to create, update, and disable users in Cisco Webex based on user assignments in Microsoft Entra ID.

### To configure automatic user provisioning for Cisco Webex in Microsoft Entra ID:

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **Cisco Webex**.

   ![Screenshot shows the Enterprise applications blade.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/enterprise-applications.png)

3. In the applications list, select **Cisco Webex**.

   ![Screenshot shows the Cisco Webex link in the Applications list.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/all-applications.png)

4. Select the **Provisioning** tab.

   ![Screenshot of a menu. Under Manage, Provisioning is highlighted.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/provisioning.png)

5. Set **+ New configuration**.

   ![Screenshot of Provisioning tab automatic.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/application-provisioning.png)

6. In the **Tenant URL** field, input your Cisco Webex Tenant URL and Secret Token. Select **Test Connection** to ensure Microsoft Entra ID can connect to Cisco Webex. If the connection fails, ensure your Cisco Webex account has the required admin permissions and try again.

   ![Screenshot of Provisioning test connection.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/provisioning-test-connection.png)

7. In the **Tenant URL** field, enter a value in the form of `https://api.ciscospark.com/v1/scim/[OrgId]`. To obtain `[OrgId]`, sign into your [Cisco Webex Control Hub](https://admin.webex.com/login). Select your organization name on the bottom left and copy the value from **Organization ID**.

   - To obtain the value for **Secret Token**, navigate to this [URL](https://idbroker.webex.com/idb/saml2/jsp/doSSO.jsp?type=login&goto=https%3A%2F%2Fidbroker.webex.com%2Fidb%2Foauth2%2Fv1%2Fauthorize%3Fresponse_type%3Dtoken%26client_id%3DC4ca14fe00b0e51efb414ebd45aa88c1858c3bfb949b2405dba10b0ca4bc37402%26redirect_uri%3Dhttp%253A%2f%2flocalhost%253A3000%2fauth%2fcode%26scope%3Dspark%253Apeople_read%2520spark%253Apeople_write%2520Identity%253ASCIM%26state%3Dthis-should-be-a-random-string-for-security-purpose). From the webex sign in page that appears, sign in with the full Cisco Webex admin account for your organization. An error page appears saying that the site can't be reached, but this is normal.

     ![Screenshot of a webpage displaying an error message. The message says that the site can't be reached and includes a few troubleshooting tips.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/cisco-webex-provisioning-tutorial/test.png)

   - Copy the value of the generated bearer token from the URL as highlighted below. This token is valid for 365 days.

     ![Screenshot showing a long U R L. Part of the address is indecipherable but is highlighted and labeled Bearer token.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/cisco-webex-provisioning-tutorial/test1.png)

8. Select **Create** to create your configuration.
9. Select **Properties** in the **Overview** page.
10. Select the pencil to edit the properties. Enable notification emails and provide an email to receive quarantine emails. Enable accidental deletions prevention. Select **Apply** to save the changes.

    ![Screenshot of Provisioning properties.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/provisioning-properties.png)

11. Select **Attribute Mapping** in the left panel and select **users**.
12. Review the user attributes that are synchronized from Microsoft Entra ID to Cisco Webex in the **Attribute-Mapping** section. The attributes selected as **Matching** properties are used to match the user accounts in Cisco Webex for update operations. If you choose to change the [matching target attribute](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/customize-application-attributes), you need to ensure that the Cisco Webex API supports filtering users based on that attribute. Select the **Save** button to commit any changes.
    | Attribute | Type | Supported for filtering | Required by Cisco Webex |
    | --- | --- | --- | --- |
    | userName | String | ✓ | ✓ |
    | name.givenName | String |  |  |
    | name.familyName | String |  |  |
    | active | Boolean |  |  |
    | displayName | String |  |  |
    | externalId | String |  |  |
13. Select **Groups**.
14. Review the group attributes that are synchronized from Microsoft Entra ID to Cisco Webex in the **Attribute-Mapping** section. The attributes selected as **Matching** properties are used to match the groups in Cisco Webex for update operations. Select the **Save** button to commit any changes.
    | Attribute | Type | Supported for filtering | Required by Cisco Webex |
    | --- | --- | --- | --- |
    | displayName | String | ✓ | ✓ |
    | members | Reference |  |  |
    | externalId | String |  |  |
15. To configure scoping filters, refer to the following instructions provided in the [Scoping filter article](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts).
16. Use [on-demand provisioning](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/provision-on-demand) to validate sync with a small number of users before deploying more broadly in your organization.
17. When you're ready to provision, select **Start Provisioning** from the **Overview** page.

## Connector limitations

- Cisco Webex is currently in Cisco's Early Field Testing \(EFT\) phase. For more information, please contact [Cisco's support team](https://www.webex.co.in/support/support-overview.html).
- For more information on Cisco Webex configuration, refer to the Cisco documentation [here](https://help.webex.com/en-us/aumpbz/Synchronize-Azure-Active-Directory-Users-into-cisco-webex-Control-Hub).

## Change log

- 02/07/2023 - Added support for **Group Provisioning**.

## Additional resources

- [Managing user account provisioning for Enterprise Apps](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/configure-automatic-user-provisioning-portal)
- [What is application access and single sign-on with Microsoft Entra ID?](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/what-is-single-sign-on)

## Related content

- [Learn how to review logs and get reports on provisioning activity](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/check-status-user-account-provisioning)
