<!-- Source: https://learn.microsoft.com/en-us/defender-cloud-apps/protect-slack -->
<!-- Sitemap-Last-Modified: 2026-06-23 -->

# How Defender for Cloud Apps helps protect your Slack Enterprise environment

Slack is a cloud service that helps organizations collaborate and communicate in one place. Along with the benefits of effective collaboration in the cloud, your organization's most critical assets might be exposed to threats. Exposed assets include messages, channels, and files with potentially sensitive information, collaboration, and partnership details, and more. Preventing exposure of this data requires continuous monitoring to prevent any malicious actors or security-unaware insiders from exfiltrating sensitive information.

Connecting Slack Enterprise to Defender for Cloud Apps gives you improved insights into your users' activities and provides threat detection for anomalous behavior.

## Main threats to your Slack Enterprise environment

- Compromised accounts and insider threats
- Data leakage
- Insufficient security awareness
- Unmanaged bring your own device \(BYOD\)

## How Defender for Cloud Apps helps to protect your environment

Defender for Cloud Apps helps you protect your Slack Enterprise environment with the following best practices:

- [Detect cloud threats, compromised accounts, and malicious insiders](https://learn.microsoft.com/en-us/defender-cloud-apps/best-practices#detect-cloud-threats-compromised-accounts-malicious-insiders-and-ransomware)
- [Use the audit trail of activities for forensic investigations](https://learn.microsoft.com/en-us/defender-cloud-apps/best-practices#use-the-audit-trail-of-activities-for-forensic-investigations)

## Control Slack with policies

The following table lists the policy types you can use to monitor and control Slack activities:

| **Type** | **Name** |
| --- | --- |
| Built-in anomaly detection policy | [Activity from anonymous IP addresses](https://learn.microsoft.com/en-us/defender-cloud-apps/anomaly-detection-policy#activity-from-anonymous-ip-addresses)  <br>[Activity from infrequent country](https://learn.microsoft.com/en-us/defender-cloud-apps/anomaly-detection-policy#activity-from-infrequent-country)  <br>[Activity from suspicious IP addresses](https://learn.microsoft.com/en-us/defender-cloud-apps/anomaly-detection-policy#activity-from-suspicious-ip-addresses)  <br>[Impossible travel](https://learn.microsoft.com/en-us/defender-cloud-apps/anomaly-detection-policy#impossible-travel)  <br>[Activity performed by terminated user](https://learn.microsoft.com/en-us/defender-cloud-apps/anomaly-detection-policy#activity-performed-by-terminated-user) \(requires Microsoft Entra ID as IdP\)  <br>[Multiple failed login attempts](https://learn.microsoft.com/en-us/defender-cloud-apps/anomaly-detection-policy#multiple-failed-login-attempts)  <br>[Unusual administrative activities](https://learn.microsoft.com/en-us/defender-cloud-apps/anomaly-detection-policy#unusual-activities-by-user)  <br>[Unusual impersonated activities](https://learn.microsoft.com/en-us/defender-cloud-apps/anomaly-detection-policy#unusual-activities-by-user) |
| Activity policy | Built a customized policy by the [Slack Audit Log](https://api.slack.com/admins/audit-logs#audit_logs_actions) activities |

For more information about creating policies, see [Create a policy](https://learn.microsoft.com/en-us/defender-cloud-apps/control-cloud-apps-with-policies#create-a-policy).

## Automate governance controls

In addition to monitoring for potential threats, you can apply and automate the following Slack governance actions to remediate detected threats:

| **Type** | **Action** |
| --- | --- |
| User governance | Notify user on alert \(via Microsoft Entra ID\)  <br>Require user to sign in again \(via Microsoft Entra ID\)  <br>Suspend user \(via Microsoft Entra ID\) |

For more information about remediating threats from apps, see [Governing connected apps](https://learn.microsoft.com/en-us/defender-cloud-apps/governance-actions).

## Protect Slack in real time

Review our best practices for [securing and collaborating with guests](https://learn.microsoft.com/en-us/defender-cloud-apps/best-practices#secure-collaboration-with-external-users-by-enforcing-real-time-session-controls) and [blocking and protecting the download of sensitive data to unmanaged or risky devices](https://learn.microsoft.com/en-us/defender-cloud-apps/best-practices#block-and-protect-download-of-sensitive-data-to-unmanaged-or-risky-devices).

## Connect Slack to Microsoft Defender for Cloud Apps

The following instructions explain how to connect Microsoft Defender for Cloud Apps to your existing Slack using the App Connector APIs. This connection gives you visibility into and control over your organization's Slack use.

### Prerequisites

- Your Slack tenant must meet the following requirements:

  - Your Slack tenant must have an **Enterprise** license. Defender for Cloud Apps doesn't support non-enterprise licenses.
  - Your Slack tenant should have **Discovery API** enabled. To enable **Discovery API** for your Slack tenant, contact Slack support.

- The org Owner needs to be logged into their Slack organization within their browser before installing the connector.

### Connect Slack to Defender for Cloud Apps

1. In the Microsoft Defender Portal, select **Settings**. Then choose **Cloud Apps**. Under **Connected apps**, select **App Connectors**.
2. In the **App connectors** page, select **+Connect an app**, followed by **Slack**.
3. In the next window, give the connector a descriptive name, and select **Next**.

   ![Screenshot that shows where to enter the instance name in the Defender portal.](https://learn.microsoft.com/en-us/defender-cloud-apps/media/connect-slack.png)
4. In the **External Link** page, select **Connect Slack**.

   ![Screenshot that shows where to enter the external link and connect to Slack.](https://learn.microsoft.com/en-us/defender-cloud-apps/media/connect-in-slack.png)
5. You'll be redirected to the Slack page. Make sure the org Owner is already logged into the Slack organization.
6. In the Slack Authorization page, make sure to choose the correct organization from the dropdown in the top-right corner.
7. In the Microsoft Defender Portal, select **Settings**. Then choose **Cloud Apps**. Under **Connected apps**, select **App Connectors**. Make sure the status of the connected App Connector is **Connected**.

   Note

   - The first connection can take up to 4 hours to get all users and their activities in the 7 days before the connection.
   - After the connector's **Status** is marked as **Connected**, the connector is live and works.
   - The received activities are from the Slack Audit Log API. You can find them in the [Slack documentation](https://api.slack.com/admins/audit-logs#audit_logs_actions).
   - **Send Slack message** activity is an activity that can be received from [Conditional Access app control](https://learn.microsoft.com/en-us/defender-cloud-apps/proxy-intro-aad), and not from the Slack API connector.

## Next steps

- [Control cloud apps with policies](https://learn.microsoft.com/en-us/defender-cloud-apps/control-cloud-apps-with-policies)
