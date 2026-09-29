<!-- Source: https://learn.microsoft.com/en-us/defender-cloud-apps/protect-okta -->
<!-- Sitemap-Last-Modified: 2026-08-11 -->

# How Defender for Cloud Apps helps protect your Okta environment

As an identity and access management solution, Okta holds the keys to your organizations most business critical services. Okta manages the authentication and authorization processes for your users and customers. Any abuse of Okta by a malicious actor or any human error might expose your most critical assets and services to potential attacks.

Connecting Okta to Defender for Cloud Apps gives you improved insights into your Okta admin activities, managed users, and customer sign-ins and provides threat detection for anomalous behavior.

Use this app connector to access SaaS Security Posture Management \(SSPM\) features, via security controls reflected in Microsoft Secure Score. [Learn more](https://learn.microsoft.com/en-us/microsoft-365/security/defender/microsoft-secure-score).

## Main threats to your Okta environment

- Compromised accounts and insider threats

## How Defender for Cloud Apps helps to protect your environment

Defender for Cloud Apps helps you protect your Okta environment with the following best practices:

- [Detect cloud threats, compromised accounts, and malicious insiders](https://learn.microsoft.com/en-us/defender-cloud-apps/best-practices#detect-cloud-threats-compromised-accounts-malicious-insiders-and-ransomware)
- [Use the audit trail of activities for forensic investigations](https://learn.microsoft.com/en-us/defender-cloud-apps/best-practices#use-the-audit-trail-of-activities-for-forensic-investigations)

## SaaS security posture management for Okta

Connect Okta to Microsoft Defender for Cloud Apps using the procedure below to automatically get security recommendations in Microsoft Secure Score.

In Secure Score, select **Recommended actions** and filter by **Product** = **Okta**. For example, recommendations for Okta include:

- *Enable multi-factor authentication*
- *Enable session timeout for web users*
- *Enhance password requirements*

For more information, see:

- [Security posture management for SaaS apps](https://learn.microsoft.com/en-us/defender-cloud-apps/security-saas)
- [Microsoft Secure Score](https://learn.microsoft.com/en-us/microsoft-365/security/defender/microsoft-secure-score)

## Control Okta with built-in policies and policy templates

You can use the following built-in policy templates to detect and notify you about potential threats:

| Type | Name |
| --- | --- |
| Built-in anomaly detection policy | [Activity from anonymous IP addresses](https://learn.microsoft.com/en-us/defender-cloud-apps/anomaly-detection-policy#activity-from-anonymous-ip-addresses)  <br>[Activity from infrequent country](https://learn.microsoft.com/en-us/defender-cloud-apps/anomaly-detection-policy#activity-from-infrequent-country)  <br>[Activity from suspicious IP addresses](https://learn.microsoft.com/en-us/defender-cloud-apps/anomaly-detection-policy#activity-from-suspicious-ip-addresses)  <br>[Impossible travel](https://learn.microsoft.com/en-us/defender-cloud-apps/anomaly-detection-policy#impossible-travel)  <br>[Multiple failed login attempts](https://learn.microsoft.com/en-us/defender-cloud-apps/anomaly-detection-policy#multiple-failed-login-attempts)  <br>[Ransomware detection](https://learn.microsoft.com/en-us/defender-cloud-apps/anomaly-detection-policy#ransomware-activity)  <br>[Unusual administrative activities](https://learn.microsoft.com/en-us/defender-cloud-apps/anomaly-detection-policy#unusual-activities-by-user) |
| Activity policy template | Logon from a risky IP address |

For more information about creating policies, see [Create a policy](https://learn.microsoft.com/en-us/defender-cloud-apps/control-cloud-apps-with-policies#create-a-policy).

## Automate governance controls

Currently, there are no governance controls available for Okta. If you're interested in having governance actions for this connector, you can [contact Microsoft Defender support](https://learn.microsoft.com/en-us/defender-xdr/contact-defender-support) with details of the actions you want.

For more information about remediating threats from apps, see [Governing connected apps](https://learn.microsoft.com/en-us/defender-cloud-apps/governance-actions).

## Protect Okta in real time

Review our best practices for [securing and collaborating with external users](https://learn.microsoft.com/en-us/defender-cloud-apps/best-practices#secure-collaboration-with-external-users-by-enforcing-real-time-session-controls) and [blocking and protecting the download of sensitive data to unmanaged or risky devices](https://learn.microsoft.com/en-us/defender-cloud-apps/best-practices#block-and-protect-download-of-sensitive-data-to-unmanaged-or-risky-devices).

## Prerequisites

To connect Okta to Defender for Cloud Apps:

- Create an Okta admin service account dedicated to Defender for Cloud Apps. You use this account to generate the API token required for the connector.
- Make sure you use an account with Super Admin permissions.
- Make sure your Okta account is verified.

## Connect Okta to Microsoft Defender for Cloud Apps

The following procedure provides instructions for connecting Microsoft Defender for Cloud Apps to your existing Okta account using the connector APIs. This connection gives you visibility into and control over Okta use. For information about how Defender for Cloud Apps protects Okta, see [Protect Okta](https://learn.microsoft.com/en-us/defender-cloud-apps/protect-okta).

Use this app connector to access SaaS Security Posture Management \(SSPM\) features, via security controls reflected in Microsoft Secure Score. [Learn more](https://learn.microsoft.com/en-us/microsoft-365/security/defender/microsoft-secure-score).

### Configure Okta

In the Okta console, create a token for the API. Copy the token value. You will need the token value later.

### Configure Defender for Cloud Apps

Perform the following steps in Defender for Cloud Apps to complete the Okta connection:

1. In the Microsoft Defender Portal, select **Settings** > **Cloud Apps**.
2. Under **Connected apps**, select **App Connectors**.
3. In the **App connectors page**, select **+Connect an app**, and then **Okta**.

   ![Screenshot of the App connectors page with the Connect Okta option.](https://learn.microsoft.com/en-us/defender-cloud-apps/media/connect-okta.png "Connect Okta")

4. In the next window, give your connection a name and select **Next**.
5. In the **Enter details** window, in the **Domain** field, enter your Okta domain and paste your Token into the **Token** field.
6. Select **Submit** to create the token for Okta in Defender for Cloud Apps.
7. In the Microsoft Defender Portal, select **Settings**. Then choose **Cloud Apps**. Under **Connected apps**, select **App Connectors**. Make sure the status of the connected App Connector is **Connected**.

After connecting Okta, you'll receive events for seven days prior to connection.

## Next steps

After you connect Okta, use the following resources to continue:

- If you have any problems connecting the app, see [Troubleshooting App Connectors](https://learn.microsoft.com/en-us/defender-cloud-apps/troubleshooting-api-connectors-using-error-messages).
- [Control cloud apps with policies](https://learn.microsoft.com/en-us/defender-cloud-apps/control-cloud-apps-with-policies)
