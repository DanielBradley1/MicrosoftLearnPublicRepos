<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/vonage-provisioning-tutorial -->
<!-- Sitemap-Last-Modified: 2026-04-10 -->

# Configure Vonage for automatic user provisioning with Microsoft Entra ID

This article describes the steps you need to perform in both Vonage and Microsoft Entra ID to configure automatic user provisioning. When configured, Microsoft Entra ID automatically provisions and de-provisions users and groups to [Vonage](https://www.vonage.com/) using the Microsoft Entra provisioning service. For important details on what this service does, how it works, and frequently asked questions, see [Automate user provisioning and deprovisioning to SaaS applications with Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/user-provisioning).

Important

To improve the security posture of application provisioning, Microsoft is retiring the **OAuth 2.0 Authorization Code Grant** for this application.

**Migrate affected provisioning jobs to OAuth2 Client Credentials Grant by March 31, 2027**, to avoid disruption to provisioning. After this date, provisioning jobs that continue to use Authorization Code Grant might stop working and could eventually be removed from the service.

**This change doesn't affect SSO.** Existing provisioned users can continue signing in, but new users won't be provisioned and changes to existing users and groups won't be synchronized while provisioning isn't functioning.

Follow the [Vonage SCIM migration guide](https://businesssupport.vonage.com/articles/Answer/SCIM-Migration-Microsoft) to migrate to OAuth2 Client Credentials Grant.

## Capabilities Supported

- Create users in Vonage.
- Deactivate users in Vonage when they don't require access anymore.
- Keep user attributes synchronized between Microsoft Entra ID and Vonage.
- [Single sign-on](https://learn.microsoft.com/en-us/entra/identity/saas-apps/vonage-tutorial) to Vonage \(recommended\).
- OAuth 2.0 Authorization Code Grant authentication is supported until April 1, 2027. After this date, only OAuth 2.0 Client Credentials authentication is supported.

## Prerequisites

The scenario outlined in this article assumes that you already have the following prerequisites:

- [A Microsoft Entra tenant](https://learn.microsoft.com/en-us/entra/identity-platform/quickstart-create-new-tenant).
- One of the following roles: [Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#application-administrator), [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator), or [Application Owner](https://learn.microsoft.com/en-us/entra/fundamentals/users-default-permissions#owned-enterprise-applications).
- A [Vonage](https://www.vonage.com/) tenant.
- A user account in Vonage with Admin permissions.

## Step 1: Plan your provisioning deployment

1. Learn about [how the provisioning service works](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/user-provisioning).
2. Determine who's in [scope for provisioning](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts).
3. Determine what data to [map between Microsoft Entra ID and Vonage](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/customize-application-attributes).

## Step 2: Configure Vonage to support provisioning with Microsoft Entra ID

1. Log in to [Vonage admin portal](http://admin.vonage.com) with an admin user.
2. In the left navigation, select **Account** > **User Provisioning**. The **Cross-Domain Identity Management \(SCIM\)** settings page opens.
3. In the **Authentication Settings and Service Credentials** section, select **Microsoft Entra** as the identity provider. The **Authentication Method** dropdown is prepopulated with **OAuth 2.0 Client Credentials**.

   Note

   When you change the credentials in Vonage, an existing provisioning job in Microsoft Entra ID may briefly continue using its current access token. These tokens typically expire one hour after they're issued and can't be refreshed after the credentials change in Vonage, which can cause temporary provisioning failures. Once you update the credentials in Microsoft Entra ID, subsequent sync cycles use the new credentials and retry failed provisioning operations. No additional action is needed for those failures.
4. In the **Ready to Generate Service Credentials** dialog, select **Continue**.
5. Enter one or more identity provider administrator email addresses, and select **Generate Credentials**.
6. Copy the following values from the dialog and save them in a secure location, such as a password manager. Each value has an individual copy icon.
   | Field | Description |
   | --- | --- |
   | **Token Endpoint** | The token endpoint provided by Vonage. |
   | **Tenant URL** | The tenant URL provided by Vonage. |
   | **Client ID** | The automatically generated client ID. |
   | **Client Secret ID** | The automatically generated client secret, which is visible only once. |
7. After you copy all four values, select **Done** to close the dialog.

   Warning

   The **Client Secret ID** is permanently masked after you select **Done**. If you lose it, select **Regenerate** to generate a new secret.

## Step 3: Add Vonage from the Microsoft Entra application gallery

Add Vonage from the Microsoft Entra application gallery to start managing provisioning to Vonage. If you have previously setup Vonage for SSO you can use the same application. However, we recommend that you create a separate app when testing out the integration initially. Learn more about adding an application from the gallery [here](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/add-application-portal).

## Step 4: Define who is in scope for provisioning

The Microsoft Entra provisioning service allows you to scope who is provisioned based on assignment to the application, or based on attributes of the user or group. If you choose to scope who is provisioned to your app based on assignment, you can use the [steps to assign users and groups to the application](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/assign-user-or-group-access-portal). If you choose to scope who is provisioned based solely on attributes of the user or group, you can [use a scoping filter](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts).

- Start small. Test with a small set of users and groups before rolling out to everyone. When scope for provisioning is set to assigned users and groups, you can control this by assigning one or two users or groups to the app. When scope is set to all users and groups, you can specify an [attribute based scoping filter](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts).
- If you need extra roles, you can [update the application manifest](https://learn.microsoft.com/en-us/entra/identity-platform/howto-add-app-roles-in-apps) to add new roles.

## Step 5: Configure automatic user provisioning to Vonage

Note

Any user that's added to Vonage must have first name, last name and email. Otherwise the integration will fail.

This section guides you through the steps to configure the Microsoft Entra provisioning service to create, update, and disable users and/or groups in Vonage based on user and/or group assignments in Microsoft Entra ID.

### Configure automatic user provisioning for Vonage in Microsoft Entra ID

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps**

   ![Screenshot of Enterprise applications blade.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/enterprise-applications.png)

3. In the applications list, select **Vonage**.

   ![Screenshot of Vonage link in the Applications list.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/all-applications.png)

4. Select the **Provisioning** tab.

   ![Screenshot of Provisioning tab.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/provisioning.png)

5. For a new configuration, select **Overview** > **+ New configuration**.

   ![Screenshot of New configuration.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/application-provisioning.png)


   To update an existing configuration, select **Connectivity**.


   ![Screenshot of Vonage provisioning connectivity settings.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/vonage-provisioning-tutorial/connectivity.png)

6. In **New configuration** or **Connectivity**, use the **Select authentication method** dropdown to change the authentication method. **OAuth2 client credentials grant** is selected by default for new configurations.

   Note

   For existing configurations, **OAuth 2.0 Authorization Code Grant** remains available as a fallback until April 1, 2027. After this date, the option will be removed. Migrate to **OAuth2 Client Credentials Grant** by March 31, 2027, to avoid provisioning disruption.
7. **Instructions for setting up OAuth2 Client Credentials Grant:** In **Tenant URL**, enter your Vonage tenant URL. Enter the client ID, client secret, and token endpoint retrieved from the Vonage portal in **Client identifier**, **Client secret**, and **OAuth token endpoint**, respectively. Select **Test connection** to validate the credentials.

   ![Screenshot of the OAuth2 client credentials grant fields and Test connection button for Vonage provisioning.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/vonage-provisioning-tutorial/client-credentials.png)

8. Select **Create** for a new configuration or **Save** when updating the authentication configuration.
9. Select **Properties** on the **Overview** page.
10. Select the **Edit** icon to edit the properties. Enable notification emails and provide an email to receive quarantine notifications. Enable **Accidental deletions prevention**. Select **Apply** to save the changes.

    ![Screenshot of Provisioning properties.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/provisioning-properties.png)

11. Vonage uses preset attribute mappings for user provisioning. You can view these mappings by selecting **Attribute Mapping** in the left panel and then selecting **users**. To learn whether additional attributes are supported, see the Vonage documentation.
12. To configure scoping filters, refer to the instructions provided in the [Scoping filter article](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts).
13. Use [on-demand provisioning](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/provision-on-demand) to validate sync with a small number of users before deploying more broadly in your organization.
14. When you're ready to provision, select **Start Provisioning** from the **Overview** page.

## Step 6: Monitor your deployment

Once you configure provisioning, use the following resources to monitor your deployment:

1. Use the [provisioning logs](https://learn.microsoft.com/en-us/entra/identity/monitoring-health/concept-provisioning-logs) to determine which users are provisioned successfully or unsuccessfully.
2. Check the [progress bar](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/application-provisioning-when-will-provisioning-finish-specific-user) to see the status of the provisioning cycle and how close it's to completion.
3. If the provisioning configuration seems to be in an unhealthy state, the application goes into quarantine. Learn more about quarantine states in the [application provisioning quarantine status](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/application-provisioning-quarantine-status) article.

## More resources

- [Managing user account provisioning for Enterprise Apps](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/configure-automatic-user-provisioning-portal)
- [What is application access and single sign-on with Microsoft Entra ID?](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/what-is-single-sign-on)

## Related content

- [Learn how to review logs and get reports on provisioning activity](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/check-status-user-account-provisioning)
