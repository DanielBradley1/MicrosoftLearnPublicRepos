<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/knowbe4-security-awareness-training-provisioning-tutorial -->
<!-- Sitemap-Last-Modified: 2026-04-21 -->

# Configure KnowBe4 Security Awareness Training for automatic user provisioning with Microsoft Entra ID

This article describes the steps you need to perform in both KnowBe4 Security Awareness Training and Microsoft Entra ID to configure automatic user provisioning. When configured, Microsoft Entra ID automatically provisions and de-provisions users and groups to [KnowBe4 Security Awareness Training](https://www.knowbe4.com/) using the Microsoft Entra provisioning service. For important details on what this service does, how it works, and frequently asked questions, see [Automate user provisioning and deprovisioning to SaaS applications with Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/user-provisioning).

## Capabilities supported

- Create users in KnowBe4 Security Awareness Training.
- Remove users in KnowBe4 Security Awareness Training when they don't require access anymore.
- Keep user attributes synchronized between Microsoft Entra ID and KnowBe4 Security Awareness Training.
- Provision groups and group memberships in KnowBe4 Security Awareness Training.
- [Single sign-on](https://learn.microsoft.com/en-us/entra/identity/saas-apps/knowbe4-tutorial) to KnowBe4 Security Awareness Training \(recommended\).
- Long lived bearer token authentication supported.

## Prerequisites

The scenario outlined in this article assumes that you already have the following prerequisites:

- [A Microsoft Entra tenant](https://learn.microsoft.com/en-us/entra/identity-platform/quickstart-create-new-tenant).
- One of the following roles: [Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#application-administrator), [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator), or [Application Owner](https://learn.microsoft.com/en-us/entra/fundamentals/users-default-permissions#owned-enterprise-applications).
- A user account in KnowBe4 Security Awareness Training with Admin permissions.

## Step 1: Plan your provisioning deployment

1. Learn about [how the provisioning service works](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/user-provisioning).
2. Determine who's in [scope for provisioning](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts).
3. Determine what data to [map between Microsoft Entra ID and KnowBe4 Security Awareness Training](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/customize-application-attributes).

## Step 2: Configure KnowBe4 Security Awareness Training to support provisioning with Microsoft Entra ID

Follow the steps below to configure your SCIM settings in the console.

Note

If you're switching from ADI to SCIM, please note that if you're using alias email addresses, our integration with SCIM doesn't support that connection, so this information is removed once you disable **Test Mode** and a sync runs.

1. From your KnowBe4 console, select your email address in the top right corner and select **Account Settings**.
2. Navigate to the **User Management > User Provisioning** section of your settings.
3. Select **Enable User Provisioning \(User Syncing\)** to display more provisioning settings.

   ![Screenshot of User Provisioning \(User Syncing\).](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/knowbe4-security-awareness-training-provisioning-tutorial/user-sync.png)

4. By default, the toggle is set to **ADI**. Select the **SCIM** toggle to begin setting up.
5. Expand your SCIM settings by selecting **+ SCIM Settings**.

   ![Screenshot of the SCIM tenant URL configuration settings.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/knowbe4-security-awareness-training-provisioning-tutorial/tenant-url.png)

6. Select **Generate SCIM Token**. This will open a new window with your token ID. Copy this ID and save it to a place that you can easily access later. It's important that you save this token because once you close this window, you can't view the token again. Once you’ve saved the information, select **OK** to close the window.

   Note

   Once your SCIM token is generated, this button will change to the **Regenerate SCIM Token** button. See the **Troubleshooting Tips** section of this article for more information.

   Note

   Your identity provider will need the token \(step 5\) and the tenant ID \(step 6\) in order to establish a connection with KnowBe4. Make sure that you save this information so it's readily available when you're ready to set up the connection with your identity provider.
7. Copy the Tenant URL and save it to a place that you can easily access later.
8. Make sure that the Test Mode option is selected.

   ![Screenshot of the SCIM test mode configuration option.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/knowbe4-security-awareness-training-provisioning-tutorial/test-mode.png)


   Note


   We recommend keeping **Test Mode** enabled until you’ve configured the connection between KnowBe4 and your identity provider and have run a successful sync. Test Mode is used to generate a report of what will happen when SCIM is enabled. This means no changes are made to your console so you can configure your setup without worrying about changes to your console. When you're ready, you can disable **Test Mode** from your **Account Settings** to enable syncing. If you're switching from ADI to SCIM, **Test Mode** is enabled automatically after you save your **Account Settings**.

9. Scroll down to the bottom of the **Account Settings** page and select **Save Changes**. Now that you have enabled SCIM in your KnowBe4 account, you're ready to finalize the connection with your identity provider. See one of the articles below to find instructions on configuring SCIM for the identity provider that you're using.

## Step 3: Add KnowBe4 Security Awareness Training from the Microsoft Entra application gallery

Add KnowBe4 Security Awareness Training from the Microsoft Entra application gallery to start managing provisioning to KnowBe4 Security Awareness Training. If you have previously setup KnowBe4 Security Awareness Training for SSO you can use the same application. However, we recommend that you create a separate app when testing out the integration initially. Learn more about adding an application from the gallery [here](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/add-application-portal).

## Step 4: Define who is in scope for provisioning

The Microsoft Entra provisioning service allows you to scope who is provisioned based on assignment to the application, or based on attributes of the user or group. If you choose to scope who is provisioned to your app based on assignment, you can use the [steps to assign users and groups to the application](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/assign-user-or-group-access-portal). If you choose to scope who is provisioned based solely on attributes of the user or group, you can [use a scoping filter](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts).

- Start small. Test with a small set of users and groups before rolling out to everyone. When scope for provisioning is set to assigned users and groups, you can control this by assigning one or two users or groups to the app. When scope is set to all users and groups, you can specify an [attribute based scoping filter](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts).
- If you need extra roles, you can [update the application manifest](https://learn.microsoft.com/en-us/entra/identity-platform/howto-add-app-roles-in-apps) to add new roles.

## Step 5: Configure automatic user provisioning to KnowBe4 Security Awareness Training

This section guides you through the steps to configure the Microsoft Entra provisioning service to create, update, and disable users and/or groups in KnowBe4 Security Awareness Training based on user and/or group assignments in Microsoft Entra ID.

### To configure automatic user provisioning for KnowBe4 Security Awareness Training in Microsoft Entra ID:

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps**

   ![Screenshot of Enterprise applications blade.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/enterprise-applications.png)

3. In the applications list, select **KnowBe4 Security Awareness Training**.

   ![Screenshot of the KnowBe4 Security Awareness Training link in the Applications list.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/all-applications.png)

4. Select the **Provisioning** tab.

   ![Screenshot of the Provisioning tab in the application settings.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/provisioning.png)

5. Select **+ New configuration**.

   ![Screenshot of Provisioning tab automatic.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/application-provisioning.png)

6. In the **Tenant URL** field, enter your KnowBe4 Security Awareness Training Tenant URL and Secret Token. Select **Test Connection** to ensure Microsoft Entra ID can connect to KnowBe4 Security Awareness Training. If the connection fails, ensure your KnowBe4 Security Awareness Training account has the required admin permissions and try again.

   ![Screenshot of Provisioning test connection.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/provisioning-test-connection.png)

7. Select **Create** to create your configuration.
8. Select **Properties** on the **Overview** page.
9. Select the **Edit** icon to edit the properties. Enable notification emails and provide an email to receive quarantine notifications. Enable **Accidental deletions prevention**. Select **Apply** to save the changes.
10. In the **Notification Email** field, enter the email address of a person who should receive the provisioning error notifications and select the **Send an email notification when a failure occurs** check box.

    ![Screenshot of the Provisioning properties page.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/provisioning-properties.png)

11. Select **Attribute Mapping** in the left panel and select **users**.
12. Review the user attributes that are synchronized from Microsoft Entra ID to KnowBe4 Security Awareness Training in the **Attribute-Mapping** section. The attributes selected as **Matching** properties are used to match the user accounts in KnowBe4 Security Awareness Training for update operations. If you choose to change the [matching target attribute](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/customize-application-attributes), you need to ensure that the KnowBe4 Security Awareness Training API supports filtering users based on that attribute. Select the **Save** button to commit any changes.

Note

Attribute list editing is now enabled, allowing the set of target attributes to be modified so that customers can create new KnowBe4 target attributes as needed.

| Attribute | Type | Supported for filtering | Required by KnowBe4 Security Awareness Training |
| --- | --- | --- | --- |
| userName | String | ✓ | ✓ |
| urn:ietf:params:scim:schemas:extension:enterprise:2.0:User:manager.value | Reference |  |  |
| active | Boolean |  |  |
| title | String |  |  |
| name.givenName | String |  |  |
| name.familyName | String |  |  |
| externalId | String |  |  |
| displayName | String |  |  |
| addresses\[type eq "work"\].formatted | String |  |  |
| phoneNumbers\[type eq "work"\].value | String |  |  |
| phoneNumbers\[type eq "mobile"\].value | String |  |  |
| userType | String |  |  |
| urn:ietf:params:scim:schemas:extension:enterprise:2.0:User:employeeNumber | String |  |  |
| urn:ietf:params:scim:schemas:extension:enterprise:2.0:User:department | String |  |  |
| urn:ietf:params:scim:schemas:extension:enterprise:2.0:User:division | String |  |  |
| urn:ietf:params:scim:schemas:extension:enterprise:2.0:User:organization | String |  |  |
| urn:ietf:params:scim:schemas:extension:knowbe4:kmsat:2.0:User:customDate1 | DateTime |  |  |
| urn:ietf:params:scim:schemas:extension:knowbe4:kmsat:2.0:User:customDate2 | DateTime |  |  |
| urn:ietf:params:scim:schemas:extension:knowbe4:kmsat:2.0:User:customField1 | String |  |  |
| urn:ietf:params:scim:schemas:extension:knowbe4:kmsat:2.0:User:customField2 | String |  |  |
| urn:ietf:params:scim:schemas:extension:knowbe4:kmsat:2.0:User:customField3 | String |  |  |
| urn:ietf:params:scim:schemas:extension:knowbe4:kmsat:2.0:User:customField4 | String |  |  |
| urn:ietf:params:scim:schemas:extension:knowbe4:kmsat:2.0:User:outOfOfficeEnd | DateTime |  |  |
| urn:ietf:params:scim:schemas:extension:knowbe4:kmsat:2.0:User:phishingLanguage | String |  |  |
| urn:ietf:params:scim:schemas:extension:knowbe4:kmsat:2.0:User:trainingLanguage | String |  |  |
| urn:ietf:params:scim:schemas:extension:knowbe4:kmsat:2.0:User:userRole | String |  |  |
| urn:ietf:params:scim:schemas:extension:knowbe4:kmsat:2.0:User:hostname | String |  |  |
| urn:ietf:params:scim:schemas:extension:knowbe4:kmsat:2.0:User:companyName | String |  |  |
| urn:ietf:params:scim:schemas:extension:knowbe4:kmsat:2.0:User:country | String |  |  |
| urn:ietf:params:scim:schemas:extension:knowbe4:kmsat:2.0:User:mailNickName | String |  |  |
| urn:ietf:params:scim:schemas:extension:knowbe4:kmsat:2.0:User:onPremisesSamAccountName | String |  |  |
| urn:ietf:params:scim:schemas:extension:knowbe4:kmsat:2.0:User:onPremisesSecurityIdentifier | String |  |  |
| urn:ietf:params:scim:schemas:extension:knowbe4:kmsat:2.0:User:userPrincipalName | String |  |  |
| urn:ietf:params:scim:schemas:extension:knowbe4:kmsat:2.0:User:lastPasswordChangeDateTime | DateTime |  |  |
|  |  |  |  |

1. Select **Attribute Mapping** in the left panel and select **groups**.
2. Review the group attributes that are synchronized from Microsoft Entra ID to KnowBe4 Security Awareness Training in the **Attribute-Mapping** section. The attributes selected as **Matching** properties are used to match the groups in KnowBe4 Security Awareness Training for update operations. Select the **Save** button to commit any changes.
   | Attribute | Type | Supported for filtering | Required by KnowBe4 Security Awareness Training |
   | --- | --- | --- | --- |
   | displayName | String | ✓ | ✓ |
   | members | Reference |  |  |
   | externalId | String |  |  |
3. To configure scoping filters, refer to the instructions provided in the [Scoping filter article](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts).
4. Use [on-demand provisioning](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/provision-on-demand) to validate sync with a small number of users before deploying more broadly in your organization.
5. When you're ready to provision, select **Start Provisioning** from the **Overview** page.

## Step 6: Monitor your deployment

Once you configure provisioning, use the following resources to monitor your deployment:

1. Use the [provisioning logs](https://learn.microsoft.com/en-us/entra/identity/monitoring-health/concept-provisioning-logs) to determine which users are provisioned successfully or unsuccessfully
2. Check the [progress bar](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/application-provisioning-when-will-provisioning-finish-specific-user) to see the status of the provisioning cycle and how close it's to completion
3. If the provisioning configuration seems to be in an unhealthy state, the application goes into quarantine. Learn more about quarantine states the [application provisioning quarantine status](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/application-provisioning-quarantine-status) article.

## Step 7: Troubleshooting Tips

- Once SCIM has been enabled, you see three buttons in the SCIM section of your Account Settings that can be used for troubleshooting purposes. For more information on these options, see the list below.

  ![Screenshot of the SCIM troubleshooting tips and buttons.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/knowbe4-security-awareness-training-provisioning-tutorial/troubleshoot.png)


  - **Regenerate SCIM token**: Use this button to generate a new SCIM token. This token can only be viewed once, so make sure you save this information before closing the window. The link between your identity providers and your KnowBe4 console is disabled until you provide the new SCIM token.
  - **Revoke SCIM token**: Use this button to disable your current SCIM token. Identity providers currently using this token will no longer be linked to your KnowBe4 console.
  - **Force Sync Now**: Use this button to manually force a SCIM sync at any time, without requiring a change from your identity provider.

## More resources

- [Managing user account provisioning for Enterprise Apps](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/configure-automatic-user-provisioning-portal)
- [What is application access and single sign-on with Microsoft Entra ID?](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/what-is-single-sign-on)

## Related content

- [Learn how to review logs and get reports on provisioning activity](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/check-status-user-account-provisioning)
