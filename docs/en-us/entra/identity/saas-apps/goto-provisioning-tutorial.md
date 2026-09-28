<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/goto-provisioning-tutorial -->
<!-- Sitemap-Last-Modified: 2026-04-10 -->

# Configure GoTo for automatic user provisioning with Microsoft Entra ID

This article describes the steps you need to perform in both GoTo and Microsoft Entra ID to configure automatic user provisioning. When configured, Microsoft Entra ID automatically provisions and de-provisions users and groups to [GoTo](https://www.goto.com/) using the Microsoft Entra provisioning service. For important details on what this service does, how it works, and frequently asked questions, see [Automate user provisioning and deprovisioning to SaaS applications with Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/user-provisioning).

## Capabilities Supported

- Create users in GoTo
- Remove users in GoTo when they don't require access anymore
- Keep user attributes synchronized between Microsoft Entra ID and GoTo
- Provision groups and group memberships in GoTo
- [Single sign-on](https://learn.microsoft.com/en-us/entra/identity/saas-apps/goto-tutorial) to GoTo \(recommended\)
- Code Auth Grant flow authentication supported.

## Prerequisites

The scenario outlined in this article assumes that you already have the following prerequisites:

- 

  - A Microsoft Entra user account with an active subscription. If you don't already have one, you can [Create an account for free](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
  - One of the following roles:

    - [Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#application-administrator)
    - [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator)
    - [Application Owner](https://learn.microsoft.com/en-us/entra/fundamentals/users-default-permissions#owned-enterprise-applications).

- An organization created in the GoTo Organization Center with at least one verified domain
- A user account in the GoTo Organization Center with [permission](https://support.goto.com/meeting/help/manage-organization-users-g2m710102) to configure provisioning \(for example, organization administrator role with Read & Write permissions\) as shown in Step 2.

## Step 1: Plan your provisioning deployment

1. Learn about [how the provisioning service works](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/user-provisioning).
2. Determine who's in [scope for provisioning](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts).
3. Determine what data to [map between Microsoft Entra ID and GoTo](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/customize-application-attributes).

## Step 2: Configure GoTo to support provisioning with Microsoft Entra ID

1. Log in to the [Organization Center](https://organization.logmeininc.com).
2. The domain used in your account's email address is the domain that you're prompted to verify within 10 days.
3. You can verify ownership of your domain using either of the following methods:

   **Method 1: Add a DNS record to your domain zone file.**  
   To use the DNS method, you place a DNS record at the level of the email domain within your DNS zone. Examples using "main.com" as the domain would resemble: `@ IN TXT "goto-verification-code=00aa00aa-bb11-cc22-dd33-44ee44ee44ee"` OR `main.com. IN TXT “goto-verification-code=00aa00aa-bb11-cc22-dd33-44ee44ee44ee”`

   Detailed instructions are as follows:

   1. Sign in to your domain's account at your domain host.
   2. Navigate to the page for updating your domain's DNS records.
   3. Locate the TXT records for your domain, then add a TXT record for the domain and for each subdomain.
   4. Save all changes.
   5. You can verify that the change has taken place by opening a command line and entering one of the following commands below \(based on your operating system, with "main.com" as the domain example\):

      - For Unix and Linux systems: `$ dig TXT main.com`
      - For Windows systems: `c:\ > nslookup -type=TXT main.com`

   6. The response will display on its own line.


   **Method 2: Upload a web server file to the specific website.** Upload a plain-text file to your web server root containing a verification string without any blank spaces or special characters outside of the string.


   - Location: `http://<yourdomain>/goto-verification-code.txt`
   - Contents: `goto-verification-code=00aa00aa-bb11-cc22-dd33-44ee44ee44ee`

4. Once you have added the DNS record or TXT file, return to [Organization Center](https://organization.logmeininc.com) and select **Verify**.
5. You have now created an organization in the Organization Center by verifying your domain, and the account used during this verification process is now the organization admin.

## Step 3: Add GoTo from the Microsoft Entra application gallery

Add GoTo from the Microsoft Entra application gallery to start managing provisioning to GoTo. If you have previously setup GoTo for SSO, you can use the same application. However, we recommend that you create a separate app when testing out the integration initially. Learn more about adding an application from the gallery [here](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/add-application-portal).

## Step 4: Define who is in scope for provisioning

The Microsoft Entra provisioning service allows you to scope who is provisioned based on assignment to the application, or based on attributes of the user or group. If you choose to scope who is provisioned to your app based on assignment, you can use the [steps to assign users and groups to the application](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/assign-user-or-group-access-portal). If you choose to scope who is provisioned based solely on attributes of the user or group, you can [use a scoping filter](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts).

- Start small. Test with a small set of users and groups before rolling out to everyone. When scope for provisioning is set to assigned users and groups, you can control this by assigning one or two users or groups to the app. When scope is set to all users and groups, you can specify an [attribute based scoping filter](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts).
- If you need extra roles, you can [update the application manifest](https://learn.microsoft.com/en-us/entra/identity-platform/howto-add-app-roles-in-apps) to add new roles.

## Step 5: Configure automatic user provisioning to GoTo

This section guides you through the steps to configure the Microsoft Entra provisioning service to create, update, and disable users and/or groups in TestApp based on user and/or group assignments in Microsoft Entra ID.

### To configure automatic user provisioning for GoTo in Microsoft Entra ID:

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps**

   ![Enterprise applications blade](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/enterprise-applications.png)

3. In the applications list, select **GoTo**.

   ![The GoTo link in the Applications list](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/all-applications.png)

4. Select the **Provisioning** tab.

   ![Provisioning tab](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/provisioning.png)

5. Select **+ New configuration**.

   ![Screenshot of Provisioning tab automatic.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/application-provisioning.png)

6. Under the **Admin Credentials** section, select **Authorize**. You're redirected to **GoTo**'s authorization page. Enter your GoTo username and select the **Next** button. Enter your GoTo password and select the **Sign In** button. Select **Test Connection** to ensure Microsoft Entra ID can connect to GoTo. If the connection fails, ensure your GoTo account has Admin permissions and try again.

   ![authorization](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/goto-provisioning-tutorial/admin.png)


   ![login](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/goto-provisioning-tutorial/username.png)


   ![connection](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/goto-provisioning-tutorial/password.png)

7. In the **Notification Email** field, enter the email address of a person who should receive the provisioning error notifications and select the **Send an email notification when a failure occurs** check box.

   ![Screenshot of Provisioning properties.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/provisioning-properties.png)

8. Select **Attribute Mapping** in the left panel and select **users**.
9. Review the user attributes that are synchronized from Microsoft Entra ID to GoTo in the **Attribute-Mapping** section. The attributes selected as **Matching** properties are used to match the user accounts in GoTo for update operations. If you choose to change the [matching target attribute](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/customize-application-attributes), you need to ensure that the GoTo API supports filtering users based on that attribute. Select the **Save** button to commit any changes.
   | Attribute | Type |
   | --- | --- |
   | userName | String |
   | externalId | String |
   | active | Boolean |
   | name.givenName | String |
   | name.familyName | String |
   | urn:ietf:params:scim:schemas:extension:enterprise:2.0:User:department | String |
   | urn:ietf:params:scim:schemas:extension:enterprise:2.0:User:employeeNumber | String |
   | urn:ietf:params:scim:schemas:extension:enterprise:2.0:User:costCenter | String |
   | urn:ietf:params:scim:schemas:extension:enterprise:2.0:User:division | String |
10. Review the group attributes that are synchronized from Microsoft Entra ID to GoTo in the **Attribute-Mapping** section. The attributes selected as **Matching** properties are used to match the groups in GoTo for update operations. Select the **Save** button to commit any changes.
    | Attribute | Type |
    | --- | --- |
    | displayName | String |
    | externalId | String |
    | members | Reference |
11. To configure scoping filters, refer to the instructions provided in the [Scoping filter article](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts).
12. Use [on-demand provisioning](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/provision-on-demand) to validate sync with a small number of users before deploying more broadly in your organization.
13. When you're ready to provision, select **Start Provisioning** from the **Overview** page.

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
