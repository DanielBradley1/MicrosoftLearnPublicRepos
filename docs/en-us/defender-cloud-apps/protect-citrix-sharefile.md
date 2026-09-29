<!-- Source: https://learn.microsoft.com/en-us/defender-cloud-apps/protect-citrix-sharefile -->
<!-- Sitemap-Last-Modified: 2026-08-08 -->

# Connect Citrix ShareFile to Microsoft Defender for Cloud Apps

Citrix ShareFile is a secure content collaboration, file sharing and sync solution that supports all the document-centric tasks and workflow needs of small and large businesses. Citrix ShareFile holds critical data of your organization, and that critical role makes it a target for malicious actors.

Connecting Citrix ShareFile to Defender for Cloud Apps gives you improved insights into your users' activities and provides threat detection using machine learning based anomaly detections. Before you start, make sure you meet the [prerequisites](#prerequisites) described later in this article.

Use this app connector to access SaaS Security Posture Management \(SSPM\) features, via security controls reflected in Microsoft Secure Score. [Learn more](https://learn.microsoft.com/en-us/microsoft-365/security/defender/microsoft-secure-score).

## Main threats to your Citrix ShareFile environment

Connecting Citrix ShareFile to Defender for Cloud Apps helps you address the following threats:

- Compromised accounts and insider threats
- Data leakage
- Insufficient security awareness
- Unmanaged bring your own device \(BYOD\)

## How Defender for Cloud Apps helps to protect your environment

Defender for Cloud Apps can help protect your Citrix ShareFile environment in the following ways:

- [Detect cloud threats, compromised accounts, and malicious insiders](https://learn.microsoft.com/en-us/defender-cloud-apps/best-practices#detect-cloud-threats-compromised-accounts-malicious-insiders-and-ransomware)
- [Use the audit trail of activities for forensic investigations](https://learn.microsoft.com/en-us/defender-cloud-apps/best-practices#use-the-audit-trail-of-activities-for-forensic-investigations)

## SaaS security posture management for Citrix ShareFile

To see security posture recommendations for Citrix Share File in Microsoft Secure Score, create an API connector via the **Connectors** tab, with **Owner** and **Enterprise** permissions. In Secure Score, select **Recommended actions** and filter by **Product** = **CitrixSF**.

For example, recommendations for Citrix Share File include:

- *Enable multi-factor authentication \(MFA\)*
- *Enable single sign on \(SSO\)*
- *Enable session timeout for web users*

If a connector already exists and you don't see Citrix Share File recommendations yet, refresh the connection by disconnecting the API connector, and then reconnecting the API connector with the *Access Company account* permissions.

For more information, see:

- [Security posture management for SaaS apps](https://learn.microsoft.com/en-us/defender-cloud-apps/security-saas)
- [Microsoft Secure Score](https://learn.microsoft.com/en-us/microsoft-365/security/defender/microsoft-secure-score)

## Connect Citrix ShareFile to Defender for Cloud Apps

Complete the following prerequisites and steps to connect Citrix ShareFile to Microsoft Defender for Cloud Apps.

### Prerequisites

The Citrix Share file user used for logging into Citrix Share file must have Access Company account permissions.

### Create API keys

Perform the following steps to create the API keys required for the connector:

1. Go to [ShareFile API Documentation](https://api.sharefile.com/), and sign in to your organization account.

   ![Screenshot of the Citrix ShareFile sign-in page for API access.](https://learn.microsoft.com/en-us/defender-cloud-apps/media/connect-citrix-sharefile-login.png "Screenshot of the Citrix ShareFile sign-in page for API access")

2. Select **Get an API Key**.

   ![Screenshot of the Citrix ShareFile Get an API Key option.](https://learn.microsoft.com/en-us/defender-cloud-apps/media/connect-citrix-sharefile-api-key.png "Screenshot of the Citrix ShareFile Get an API Key option")

3. To generate API keys \(*Client ID* and *Client Secret*\), go to **Create New**.

   ![Screenshot of the Citrix ShareFile API portal Create New key option.](https://learn.microsoft.com/en-us/defender-cloud-apps/media/connect-citrix-sharefile-create-new.png "Screenshot of the Citrix ShareFile API portal Create New key option")

4. Fill out the following fields:

   - **Application name**: Microsoft Defender for Cloud Apps \(you can also choose another name\).
   - **Redirect URL**: `https://portal.cloudappsecurity.com/api/oauth/saga`.

     For US Government GCC customers, enter `https://portal.cloudappsecuritygov.com/api/oauth/saga` as the redirect URL.

     For US Government GCC High customers, enter `https://portal.cloudappsecurity.us/api/oauth/saga` as the redirect URL.

5. Select **Generate API Key**.
6. Copy the *Client ID* and *Client Secret*.

### Configure Defender for Cloud Apps

Use the following steps to configure the Citrix ShareFile connector in Defender for Cloud Apps:

1. In the Microsoft Defender Portal, select **Settings**. Then choose **Cloud Apps**. Under **Connected apps**, select **App Connectors**.
2. In the **App connectors** page, select **+Connect an app**, followed by **Citrix ShareFile**.

   ![Screenshot of the App connectors page with the Connect Citrix ShareFile option.](https://learn.microsoft.com/en-us/defender-cloud-apps/media/connect-citrix-sharefile-app-connectors.png "Screenshot of the App connectors page with the Connect Citrix ShareFile option")

3. In the pop-up, give the connector a descriptive name, and select **Connect Citrix ShareFile**.

   ![Screenshot of the Citrix ShareFile connector dialog with instance name field.](https://learn.microsoft.com/en-us/defender-cloud-apps/media/connect-citrix-sharefile-instance-name.png "Screenshot of the Citrix ShareFile connector dialog with instance name field")

4. In the Citrix ShareFile connector details screen, enter the following fields:

   - The **Client ID** and **Client Secret** that you created in the Citrix ShareFile API portal.
   - **Client Subdomain**: Enter your account's subdomain. For example, if your account's URL is "mycompany.sharefile.com", you would enter "mycompany".

5. Select **Connect** in Citrix ShareFile.
6. In the Microsoft Defender Portal, select **Settings**. Then choose **Cloud Apps**. Under **Connected apps**, select **App Connectors**. Make sure the status of the connected App Connector is **Connected**.

## Rate limits

The default rate limit is 420 requests per minute.

## Next steps

[Control cloud apps with policies](https://learn.microsoft.com/en-us/defender-cloud-apps/control-cloud-apps-with-policies)

If you run into any problems, we're here to help. To get assistance or support for your product issue, please [open a support ticket](https://learn.microsoft.com/en-us/defender-xdr/contact-defender-support).
