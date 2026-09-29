<!-- Source: https://learn.microsoft.com/en-us/defender-xdr/troubleshoot -->
<!-- Sitemap-Last-Modified: 2026-08-11 -->

# Troubleshoot Microsoft Defender XDR service issues

Issues might arise as you use the Microsoft Defender XDR service. The following sections provide solutions and workarounds. Before you begin, verify that your environment meets the [prerequisites](https://learn.microsoft.com/en-us/defender-xdr/prerequisites). If you encounter a problem that isn't addressed here, [contact Microsoft Support](https://support.microsoft.com/contactus).

## I don't see Microsoft Defender content

If you don't see capabilities on the navigation pane such as the Incidents, Action center, or Hunting in your portal, verify that your tenant has the appropriate licenses.

For more information, see [Microsoft Defender XDR prerequisites](https://learn.microsoft.com/en-us/defender-xdr/prerequisites).

## Microsoft Defender for Identity alerts are not showing up in the Microsoft Defender incidents

If you deployed Microsoft Defender for Identity but don't see its alerts in Microsoft Defender incidents, check that the Defender for Cloud Apps and Defender for Identity integration is turned on.

For more information, see [Microsoft Defender for Identity integration](https://learn.microsoft.com/en-us/cloud-app-security/mdi-integration).

## My legitimate file/URL is being detected as malicious

A false positive is a file or URL that is detected as malicious but isn't a threat. You can create indicators and define exclusions to unblock and allow certain files/URLs. See [Address false positives/negatives in Defender for Endpoint](https://learn.microsoft.com/en-us/defender-endpoint/defender-endpoint-false-positives-negatives).

## My ServiceNow tickets are no longer available in the Microsoft Defender portal

The ServiceNow connector is no longer in the Microsoft Defender portal. To connect Microsoft Defender XDR with ServiceNow, use the Microsoft Graph Security API instead. For details, see [Security solution integrations using the Microsoft Graph Security API](https://learn.microsoft.com/en-us/graph/security-integration).

The ServiceNow connector was offered in the portal as a preview. It let you create ServiceNow incidents from Microsoft Defender XDR incidents.

## I can't submit files

In some instances, an administrator block might cause submission issues when you try to submit a potentially infected file to the [Microsoft Security intelligence website](https://www.microsoft.com/wdsi) for analysis. The following process shows how to resolve this problem.

### Review your settings

Open your Azure [Enterprise application user consent settings](https://portal.azure.com/#view/Microsoft_AAD_IAM/ConsentPoliciesMenuBlade/%7E/UserSettings). Under **Consent and permissions** > **User consent settings**, check which option is selected under **User consent for applications**.

- If **Do not allow user consent** is selected, a Microsoft Entra administrator for the customer tenant needs to provide consent for the organization. Depending on the configuration with Microsoft Entra ID, users might be able to submit a request right from the same dialog box. If there's no option to ask for admin consent, users need to request for these permissions to be added to their Microsoft Entra admin. For more information, see [Implement required Enterprise Application permissions](#implement-required-enterprise-application-permissions).
- If **Allow user consent for apps from verified publishers, for selected permissions** or **Let Microsoft manage your consent settings** is selected, verify that the Windows Defender Security Intelligence enterprise application is enabled for sign-in. This setting is on the app **Properties** page, not under **User consent settings**.

  - To verify: In the [Azure portal](https://portal.azure.com/), go to **Microsoft Entra ID** > **Manage** > **Enterprise applications** > **All applications**, search for and open **Windows Defender Security Intelligence**. Under **Manage**, open **Properties**. Confirm that **Enabled for users to sign in?** is set to **Yes**. If it's set to **No**, request that a Microsoft Entra administrator enable it.

### Implement required Enterprise Application permissions

This process requires an Application Administrator or higher in the tenant.

1. Sign in to the [Azure portal](https://portal.azure.com/).
2. Go to **Microsoft Entra ID** > **Manage** > **Enterprise applications** > **All applications**.
3. Search for and select **Windows Defender Security Intelligence**.
4. In the navigation menu, go to **Security** > **Permissions**.
5. Select **Grant admin consent for <your organization>**, and confirm. If you're able to do so, review the API permissions required for this application, as the following image shows. Provide consent for the tenant.

   [![Screenshot of the admin consent dialog showing API permissions for Windows Defender Security Intelligence.](https://learn.microsoft.com/en-us/defender-xdr/media/troubleshoot/msi-grant-admin-consent.jpg)](https://learn.microsoft.com/en-us/defender-xdr/media/troubleshoot/msi-grant-admin-consent.jpg#lightbox)
6. If the administrator receives an error while attempting to provide consent manually, try either [Approve enterprise application permissions by user request](#option-1-approve-enterprise-application-permissions-by-user-request) or [Provide admin consent by authenticating the application as an admin](#option-2-provide-admin-consent-by-authenticating-the-application-as-an-admin) as possible workarounds.

#### Option 1: Approve enterprise application permissions by user request

Microsoft Entra administrators need to allow users to request admin consent to apps.

1. Sign in to the [Azure portal](https://portal.azure.com).
2. Go to **Microsoft Entra ID** > **Enterprise applications** > **Security** > **Consent and permissions** > **Admin consent settings**.
3. Under **Admin consent requests**, verify that **Users can request admin consent to apps they are unable to consent to** is set to **Yes**.

If you're redirected to **Enterprise applications** > **User settings** and see a message that settings moved, open **Consent and permissions** and then select **Admin consent settings**.

More information is available in [Configure Admin consent workflow](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/configure-admin-consent-workflow).

Once this setting is verified, users can go through the enterprise customer sign-in at [Microsoft security intelligence](https://www.microsoft.com/wdsi/filesubmission), and submit a request for admin consent, including justification.

[![Screenshot of the approval request dialog during enterprise sign-in.](https://learn.microsoft.com/en-us/defender-xdr/media/troubleshoot/msi-contoso-approval-required.png)](https://learn.microsoft.com/en-us/defender-xdr/media/troubleshoot/msi-contoso-approval-required.png#lightbox)

Administrators can review and approve the application permissions [Azure admin consent requests](https://portal.azure.com/#blade/Microsoft_AAD_IAM/StartboardApplicationsMenuBlade/AccessRequests/menuId/).

After providing consent, all users in the tenant will be able to use the application.

#### Option 2: Provide admin consent by authenticating the application as an admin

This process requires that a Global Administrator go through the Enterprise customer sign-in flow at [Microsoft security intelligence](https://www.microsoft.com/wdsi/filesubmission).

[![Screenshot of the Microsoft permissions request dialog for organization consent.](https://learn.microsoft.com/en-us/defender-xdr/media/troubleshoot/msi-microsoft-permission-required.jpg)](https://learn.microsoft.com/en-us/defender-xdr/media/troubleshoot/msi-microsoft-permission-required.jpg#lightbox)

Then, admins review the permissions and make sure to select **Consent on behalf of your organization**, and then select **Accept**.

All users in the tenant can now use this application.

#### Option 3: Delete and re-add app permissions

If neither [Option 1: Approve enterprise application permissions by user request](#option-1-approve-enterprise-application-permissions-by-user-request) nor [Option 2: Provide admin consent by authenticating the application as an admin](#option-2-provide-admin-consent-by-authenticating-the-application-as-an-admin) resolves the issue, try the following steps \(as an admin\):

Warning

Removing the existing application configuration temporarily prevents all users in your tenant from submitting files until you complete the remaining steps and reconsent. Review your current permissions before you proceed.

1. Remove previous configurations for the application. Go to the [Enterprise applications page in the Azure portal](https://portal.azure.com/#view/Microsoft_AAD_IAM/StartboardApplicationsMenuBlade/%7E/AppAppsPreview).
2. Search for and select **Windows Defender Security Intelligence**.
3. In the navigation menu, go to **Manage** > **Properties**.
4. Select **delete**.

   [![Screenshot of the enterprise application properties page with the delete option.](https://learn.microsoft.com/en-us/defender-xdr/media/troubleshoot/msi-properties.png)](https://learn.microsoft.com/en-us/defender-xdr/media/troubleshoot/msi-properties.png#lightbox)
5. Capture `TenantID` from the [Microsoft Entra ID Properties page](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ActiveDirectoryMenuBlade/Properties).
6. Replace `{tenant-id}` with the specific tenant that needs to grant consent to this application in the URL below. Copy the following URL into browser: `https://login.microsoftonline.com/{tenant-id}/v2.0/adminconsent?client_id=f0cf43e5-8a9b-451c-b2d5-7285c785684d&state=12345&redirect_uri=https%3a%2f%2fwww.microsoft.com%2fwdsi%2ffilesubmission&scope=openid+profile+email+offline_access`

   The URL already includes the required `client_id`, `state`, `redirect_uri`, and `scope` parameters.

   [![Screenshot of the permissions requested dialog for the organization.](https://learn.microsoft.com/en-us/defender-xdr/media/troubleshoot/msi-microsoft-permission-requested-your-organization.png)](https://learn.microsoft.com/en-us/defender-xdr/media/troubleshoot/msi-microsoft-permission-requested-your-organization.png#lightbox)
7. Review the permissions required by the application, and then select **Accept**.
8. Confirm the permissions are applied in the [Azure portal](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ManagedAppMenuBlade/Permissions/appId/f0cf43e5-8a9b-451c-b2d5-7285c785684d/objectId/ce60a464-5fca-4819-8423-bcb46796b051).

   [![Screenshot of the permissions page confirming granted permissions.](https://learn.microsoft.com/en-us/defender-xdr/media/troubleshoot/msi-permissions.jpg)](https://learn.microsoft.com/en-us/defender-xdr/media/troubleshoot/msi-permissions.jpg#lightbox)
9. Sign in to [Microsoft security intelligence](https://www.microsoft.com/wdsi/filesubmission) as an enterprise user with a non-admin account to see if you have access.

If the warning isn't resolved after following these troubleshooting steps, call Microsoft support.

Tip

Do you want to learn more? Engage with the Microsoft Security community in our Tech Community: [Microsoft Defender XDR Tech Community](https://techcommunity.microsoft.com/t5/microsoft-365-defender/bd-p/MicrosoftThreatProtection).
