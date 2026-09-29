<!-- Source: https://learn.microsoft.com/en-us/defender-cloud-apps/protect-zendesk -->
<!-- Sitemap-Last-Modified: 2026-07-03 -->

# How Defender for Cloud Apps helps protect your Zendesk environment

As a customer service software solution, Zendesk holds the sensitive information to your organization. Any abuse of Zendesk by a malicious actor or any human error might expose your most critical assets and services to potential attacks.

Connecting Zendesk to Defender for Cloud Apps gives you improved insights into your Zendesk admin activities and provides threat detection for anomalous user and admin activity in Zendesk.

## Main threats to your Zendesk environment

Zendesk usage without proper protection can expose your organization to the following threats:

- Compromised accounts and insider threats
- Data leakage
- Insufficient security awareness
- Unmanaged bring your own device \(BYOD\)

## How Defender for Cloud Apps helps to protect your environment

Use the following Defender for Cloud Apps best practices to help protect your Zendesk environment:

- [Detect cloud threats, compromised accounts, and malicious insiders](https://learn.microsoft.com/en-us/defender-cloud-apps/best-practices#detect-cloud-threats-compromised-accounts-malicious-insiders-and-ransomware)
- [Use the audit trail of activities for forensic investigations](https://learn.microsoft.com/en-us/defender-cloud-apps/best-practices#use-the-audit-trail-of-activities-for-forensic-investigations)

## Control Zendesk with policies

The following table lists the policy types you can use to monitor and control Zendesk activity:

| Type | Name |
| --- | --- |
| Built-in anomaly detection policy | [Activity from anonymous IP addresses](https://learn.microsoft.com/en-us/defender-cloud-apps/anomaly-detection-policy#activity-from-anonymous-ip-addresses)  <br>[Activity from infrequent country](https://learn.microsoft.com/en-us/defender-cloud-apps/anomaly-detection-policy#activity-from-infrequent-country)  <br>[Activity from suspicious IP addresses](https://learn.microsoft.com/en-us/defender-cloud-apps/anomaly-detection-policy#activity-from-suspicious-ip-addresses)  <br>[Impossible travel](https://learn.microsoft.com/en-us/defender-cloud-apps/anomaly-detection-policy#impossible-travel)  <br>[Activity performed by terminated user](https://learn.microsoft.com/en-us/defender-cloud-apps/anomaly-detection-policy#activity-performed-by-terminated-user) \(requires Microsoft Entra ID as IdP\)  <br>[Multiple failed login attempts](https://learn.microsoft.com/en-us/defender-cloud-apps/anomaly-detection-policy#multiple-failed-login-attempts)  <br>[Unusual administrative activities](https://learn.microsoft.com/en-us/defender-cloud-apps/anomaly-detection-policy#unusual-activities-by-user)  <br>[Unusual impersonated activities](https://learn.microsoft.com/en-us/defender-cloud-apps/anomaly-detection-policy#unusual-activities-by-user) |
| Activity policy | Built a customized policy by the Zendesk audit log |

For more information about creating policies, see [Create a policy](https://learn.microsoft.com/en-us/defender-cloud-apps/control-cloud-apps-with-policies#create-a-policy).

## Automate governance controls

In addition to monitoring for potential threats, you can apply and automate the following Zendesk governance actions to remediate detected threats:

| Type | Action |
| --- | --- |
| User governance | Notify user on alert \(via Microsoft Entra ID\)  <br>Require user to sign in again \(via Microsoft Entra ID\)  <br>Suspend user \(via Microsoft Entra ID\) |

For more information about remediating threats from apps, see [Governing connected apps](https://learn.microsoft.com/en-us/defender-cloud-apps/governance-actions).

## Protect Zendesk in real time

Review our best practices for [securing and collaborating with external users](https://learn.microsoft.com/en-us/defender-cloud-apps/best-practices#secure-collaboration-with-external-users-by-enforcing-real-time-session-controls) and [blocking and protecting the download of sensitive data to unmanaged or risky devices](https://learn.microsoft.com/en-us/defender-cloud-apps/best-practices#block-and-protect-download-of-sensitive-data-to-unmanaged-or-risky-devices).

## SaaS security posture management for Zendesk

Software as a Service \(SaaS\) security posture management helps you evaluate and improve the security configuration of your SaaS apps. After you connect Zendesk to Microsoft Defender for Cloud Apps, you automatically get security posture recommendations for Zendesk in Microsoft Secure Score. In Secure Score, select **Recommended actions** and filter by **Product** = **Zendesk**. For example, recommendations for Zendesk include:

- *Enable multifactor authentication \(MFA\)*
- *Enable session timeout for users*
- *Enable IP restrictions*
- *Block admins to set passwords.*

For more information, see:

- [Security posture management for SaaS apps](https://learn.microsoft.com/en-us/defender-cloud-apps/security-saas)
- [Microsoft Secure Score](https://learn.microsoft.com/en-us/microsoft-365/security/defender/microsoft-secure-score)

## Connect Zendesk to Microsoft Defender for Cloud Apps

The following instructions explain how to connect Microsoft Defender for Cloud Apps to your existing Zendesk using the App Connector APIs. This connection gives you visibility into and control over your organization's Zendesk use.

### Prerequisites

- The Zendesk user used for logging into Zendesk must be an admin.
- Supported Zendesk licenses:

  - Enterprise
  - Enterprise Plus

Note

Connecting Zendesk to Defender for Cloud Apps with a Zendesk user that isn't an admin will result in a connection error.

### Configure Zendesk

Perform the following steps in Zendesk to create the OAuth credentials required for the connector:

1. Select **Add OAuth client**.
2. Select **New Credential**. Fill out the following fields:

   - Client name: **Microsoft Defender for Cloud Apps** \(you can also choose another name\).
   - Description: **Microsoft Defender for Cloud Apps API Connector** \(you can also choose another description\).
   - Company: **Microsoft Defender for Cloud Apps** \(you can also choose another company\).
   - Unique identifier: **microsoft\_cloud\_app\_security** \(you can also choose another unique identifier\).
   - Client Kind: **Confidential**
   - Redirect URL: `https://portal.cloudappsecurity.com/api/oauth/saga`

     Note

     - For US Government GCC customers, enter the following value: `https://portal.cloudappsecuritygov.com/api/oauth/saga`
     - For US Government GCC High customers, enter the following value: `https://portal.cloudappsecurity.us/api/oauth/saga`

3. Copy the **Secret** that was generated. You'll need it in the upcoming steps.

### Configure Defender for Cloud Apps

Note

The Zendesk user that's configuring the integration must always remain a Zendesk admin, even after the connector is installed.

1. In the Microsoft Defender Portal, select **Settings**. Then choose **Cloud Apps**. Under **Connected apps**, select **App Connectors**.
2. In the **App connectors** page, select **+Connect an app**, followed by **Zendesk**.
3. In the next window, give the connector a descriptive name, and select **Next**.

   [![Screenshot that shows where to add the instance name in the Defender portal.](https://learn.microsoft.com/en-us/defender-cloud-apps/media/connect-zendesk.png)](https://learn.microsoft.com/en-us/defender-cloud-apps/media/connect-zendesk.png#lightbox)
4. In the **Enter details** page, enter the following fields, and then select **Next**.

   - **Client ID**: the Unique identifier you used when you created the OAuth app in the Zendesk admin portal.
   - **Client Secret**: your saved secret.
   - **Client endpoint**: Zendesk URL. It should be `<account_name>.zendesk.com`.

5. In the **External link** page, select **Connect Zendesk**.
6. In the Microsoft Defender Portal, select **Settings**. Then choose **Cloud Apps**. Under **Connected apps**, select **App Connectors**. Make sure the status of the connected App Connector is **Connected**.
7. The first connection can take up to four hours to get all users and their activities in the seven days before the connection.
8. After the connector's **Status** is marked as **Connected**, the connector is live and works.

Note

- Microsoft recommends using a short lived access token. Zendesk doesn't currently support short lived tokens. We recommend refreshing your token every 6 months as a security best practice. To refresh and revoke an old access token see: [Revoke Token](https://developer.zendesk.com/api-reference/ticketing/oauth/oauth_tokens/#revoke-token). After you revoke the old token, create a new secret and reconnect the Zendesk connector.
- System activities are shown with the **Zendesk** account name.

## Zendesk connector rate limits

The default rate limit is 200 requests per minute. To increase the rate limit, [open a support ticket](https://learn.microsoft.com/en-us/defender-xdr/contact-defender-support).

For more information about the maximum rate limit for every subscription, see: [Zendesk Suite plan limits](https://developer.zendesk.com/api-reference/ticketing/account-configuration/usage_limits/#zendesk-support-plan-limits).

## Next steps

- [Control cloud apps with policies](https://learn.microsoft.com/en-us/defender-cloud-apps/control-cloud-apps-with-policies)
