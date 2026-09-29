<!-- Source: https://learn.microsoft.com/en-us/defender-cloud-apps/protect-onelogin -->
<!-- Sitemap-Last-Modified: 2026-07-03 -->

# How Defender for Cloud Apps helps protect your OneLogin environment

As an identity and access management solution, OneLogin holds the keys to your organizations most business critical services. OneLogin manages the authentication and authorization processes for your users. Any abuse of OneLogin by a malicious actor or any human error might expose your most critical assets and services to potential attacks.

Connecting OneLogin to Defender for Cloud Apps gives you improved insights into your OneLogin admin activities and managed users sign-ins and provides threat detection for anomalous behavior.

## Main threats to your OneLogin environment

The main threats to consider in a OneLogin environment include:

- Compromised accounts and insider threats
- Data leakage
- Insufficient security awareness
- Unmanaged bring your own device \(BYOD\)

## How Defender for Cloud Apps helps to protect your environment

Defender for Cloud Apps helps you protect your OneLogin environment in the following ways:

- [Detect cloud threats, compromised accounts, and malicious insiders](https://learn.microsoft.com/en-us/defender-cloud-apps/best-practices#detect-cloud-threats-compromised-accounts-malicious-insiders-and-ransomware)
- [Use the audit trail of activities for forensic investigations](https://learn.microsoft.com/en-us/defender-cloud-apps/best-practices#use-the-audit-trail-of-activities-for-forensic-investigations)

## Control OneLogin with policies

The following table lists the policy types and detections you can use to monitor and control OneLogin activity:

| **Type** | **Name** |
| --- | --- |
| Built-in anomaly detection policy | [Activity from anonymous IP addresses](https://learn.microsoft.com/en-us/defender-cloud-apps/anomaly-detection-policy#activity-from-anonymous-ip-addresses)  <br>[Activity from infrequent country](https://learn.microsoft.com/en-us/defender-cloud-apps/anomaly-detection-policy#activity-from-infrequent-country)  <br>[Activity from suspicious IP addresses](https://learn.microsoft.com/en-us/defender-cloud-apps/anomaly-detection-policy#activity-from-suspicious-ip-addresses)  <br>[Impossible travel](https://learn.microsoft.com/en-us/defender-cloud-apps/anomaly-detection-policy#impossible-travel)  <br>[Activity performed by terminated user](https://learn.microsoft.com/en-us/defender-cloud-apps/anomaly-detection-policy#activity-performed-by-terminated-user) \(requires Microsoft Entra ID as IdP\)  <br>[Multiple failed login attempts](https://learn.microsoft.com/en-us/defender-cloud-apps/anomaly-detection-policy#multiple-failed-login-attempts)  <br>[Unusual administrative activities](https://learn.microsoft.com/en-us/defender-cloud-apps/anomaly-detection-policy#unusual-activities-by-user)  <br>[Unusual impersonated activities](https://learn.microsoft.com/en-us/defender-cloud-apps/anomaly-detection-policy#unusual-activities-by-user) |
| Activity policy | Built a customized policy by the [OneLogin activities](https://developers.onelogin.com/api-docs/1/events/event-resource) |

For more information about creating policies, see [Create a policy](https://learn.microsoft.com/en-us/defender-cloud-apps/control-cloud-apps-with-policies#create-a-policy).

## Automate governance controls

Besides monitoring for potential threats, you can apply and automate the following OneLogin governance actions to fix detected threats:

| **Type** | **Action** |
| --- | --- |
| User governance | Notify user on alert \(via Microsoft Entra ID\)  <br>Require user to sign in again \(via Microsoft Entra ID\)  <br>Suspend user \(via Microsoft Entra ID\) |

For more information about remediating threats from apps, see [Governing connected apps](https://learn.microsoft.com/en-us/defender-cloud-apps/governance-actions).

## Protect OneLogin in real time

Review our best practices for [securing and collaborating with external users](https://learn.microsoft.com/en-us/defender-cloud-apps/best-practices#secure-collaboration-with-external-users-by-enforcing-real-time-session-controls) and [blocking and protecting the download of sensitive data to unmanaged or risky devices](https://learn.microsoft.com/en-us/defender-cloud-apps/best-practices#block-and-protect-download-of-sensitive-data-to-unmanaged-or-risky-devices).

## Connect OneLogin to Microsoft Defender for Cloud Apps

The following instructions explain how to connect Microsoft Defender for Cloud Apps to your existing OneLogin app using the App Connector APIs. This connection gives you visibility into and control over your organization's OneLogin use.

### Prerequisites

Before you begin, make sure you meet the following prerequisite:

- The OneLogin account used for logging into OneLogin must be a Super User. For more information, see [OneLogin administrative privileges](https://onelogin.service-now.com/kb_view_customer.do?sysparm_article=KB0010391).

### Configure OneLogin

Perform the following steps in OneLogin to create the credentials required for the connector:

1. Sign-in to the OneLogin admin portal.
2. Select **New Credential**.
3. Name the application **Microsoft Defender for Cloud Apps**, and assign **Read all** permissions.
4. Copy the **Client ID** and the **Client Secret**. You'll enter them when you configure the OneLogin connector in Defender for Cloud Apps.

### Configure Defender for Cloud Apps

Perform the following steps in Defender for Cloud Apps to create the OneLogin connector:

1. In the Microsoft Defender Portal, select **Settings**. Then choose **Cloud Apps**. Under **Connected apps**, select **App Connectors**.
2. In the **App connectors** page, select **+Connect an app**, followed by **OneLogin**.
3. In the next window, give the connector a descriptive name, and select **Next**.

   [![Screenshot that shows where to add the instance name when connecting OneLogin in the Defender portal.](https://learn.microsoft.com/en-us/defender-cloud-apps/media/connect-onelogin.png)](https://learn.microsoft.com/en-us/defender-cloud-apps/media/connect-onelogin.png#lightbox)
4. In the **Enter details** window, enter the **Client ID** and the **Client Secret** that you copied and select **Submit**.
5. In the Microsoft Defender Portal, select **Settings**. Then choose **Cloud Apps**. Under **Connected apps**, select **App Connectors**. Make sure the status of the connected App Connector is **Connected**.
6. The first connection can take up to 4 hours to get all users and their activities after the connector was established.
7. After the connector's **Status** is marked as **Connected**, the connector is live and working.

## Related content

- [Control cloud apps with policies](https://learn.microsoft.com/en-us/defender-cloud-apps/control-cloud-apps-with-policies)
