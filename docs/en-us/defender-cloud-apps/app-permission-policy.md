<!-- Source: https://learn.microsoft.com/en-us/defender-cloud-apps/app-permission-policy -->
<!-- Sitemap-Last-Modified: 2026-08-11 -->

# Create policies to control OAuth apps

In Microsoft Defender for Cloud Apps, you can create app permission policies to monitor and control OAuth app behavior. Use these policies to get automated notifications when apps meet specific criteria, investigate requested permissions, and mark permissions as approved or banned.

## Create OAuth app policies

Set permission policies so that you get automated notifications when an OAuth app meets certain criteria. For example, you can automatically be alerted when there are apps that require a high permission level and are authorized by more than 50 users. For more information about investigating OAuth apps, see [Manage app permissions](https://learn.microsoft.com/en-us/defender-cloud-apps/manage-app-permissions).

OAuth app policies enable you to investigate which permissions each app requested and which users authorized them for Microsoft 365, Google Workspace, and Salesforce. You're also able to mark these permissions as approved or banned. Marking an app permission as banned disables the enterprise application associated with that OAuth app.

Along with a built-in set of capabilities to detect anomalous app behavior and generate alerts based on machine learning algorithms, app policies in app governance are a way for you to:

- Specify conditions by which app governance can alert you to app behavior for automatic or manual remediation.
- Implement the app compliance policies for your organization.

Note

If you have enabled App governance for your organization, you can also specify conditions for app governance alerts and implement app compliance policies for your organization. For more information, see [Create app policies in app governance](https://learn.microsoft.com/en-us/defender-cloud-apps/app-governance-app-policies-create).

## Create a new OAuth app policy

You can create a new OAuth app policy from **Policy management** or from **App governance**.

If you have [Microsoft Defender preview features](https://learn.microsoft.com/en-us/microsoft-365/security/defender/preview) and [app governance enabled \(get started with app governance\)](https://learn.microsoft.com/en-us/defender-cloud-apps/app-governance-get-started), create the policy from the **App governance** page rather than from **Policy management**.

Note

OAuth apps policies will trigger alerts only on policies that were authorized by users in the tenant.

To create a new OAuth app policy:

1. In the Microsoft Defender Portal, under **Cloud Apps**, select **Policies** and then select **Policy management**.
2. Select the **Threat detection** tab and then select **Create policy** followed by **OAuth app policy**.

   [![Screenshot that shows how to create an OAUth app policy in the Microsoft Defender portal.](https://learn.microsoft.com/en-us/defender-cloud-apps/create-oauth-app-policies/create-oauth-policy.png)](https://learn.microsoft.com/en-us/defender-cloud-apps/create-oauth-app-policies/create-oauth-policy.png#lightbox)
3. In the **Create OAuth app policy** page, enter a name and description for the policy.

   [![Screenshot that shows where to enter the details for your new Oauth app policy.](https://learn.microsoft.com/en-us/defender-cloud-apps/create-oauth-app-policies/oauth-app-policy.png)](https://learn.microsoft.com/en-us/defender-cloud-apps/create-oauth-app-policies/oauth-app-policy.png#lightbox)
4. Filter the apps according to your needs. For example, you can view all apps that request **Permission** to **Modify calendars in your mailbox**.
5. You can use the **Community use** filter to determine whether granting permission to a selected app is common, uncommon, or rare. The **Community use** filter can be helpful if an app has a rare community-use classification and requests a high-severity permission or has been granted permission by many users.
6. Select the **New policy from search** button.
7. You can set the policy based on the group memberships of the users who authorized the apps. For example, an admin can decide to set a policy that revokes uncommon apps if they ask for high permissions, only if the user who authorized the permissions is a member of the **Administrators** group.

Note

OAuth apps policies will trigger alerts only on policies that were authorized by users in the tenant.

## OAuth app anomaly detection policies

In addition to OAuth app policies you can create, there are the following out-of-the-box anomaly detection policies that profile metadata of OAuth apps to identify ones that are potentially malicious:

| Policy name | Policy description |
| --- | --- |
| Misleading OAuth app name | Scans OAuth apps connected to your environment and triggers an alert when an app with a misleading name is detected. Misleading names, such as foreign letters that resemble Latin letters, could indicate an attempt to disguise a malicious app as a known and trusted app. |
| Misleading publisher name for an OAuth app | Scans OAuth apps connected to your environment and triggers an alert when an app with a misleading publisher name is detected. Misleading publisher names, such as foreign letters that resemble Latin letters, could indicate an attempt to disguise a malicious app as an app coming from a known and trusted publisher. |
| Malicious OAuth app consent | Scans OAuth apps connected to your environment and triggers an alert when a potentially malicious app is authorized. Malicious OAuth apps may be used as part of a phishing campaign in an attempt to compromise users. This detection uses Microsoft security research and threat intelligence expertise to identify malicious apps. |
| Suspicious OAuth app file download activities | See [Anomaly detection policies](https://learn.microsoft.com/en-us/defender-cloud-apps/anomaly-detection-policy#suspicious-oauth-app-file-download-activities) |

Note

- Anomaly detection policies are only available for OAuth apps that are authorized in your Microsoft Entra ID.
- The severity of OAuth app anomaly detection policies cannot be modified.

## Next steps

- [Data protection policies](https://learn.microsoft.com/en-us/defender-cloud-apps/data-protection-policies)
