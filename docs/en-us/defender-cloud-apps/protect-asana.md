<!-- Source: https://learn.microsoft.com/en-us/defender-cloud-apps/protect-asana -->
<!-- Sitemap-Last-Modified: 2026-08-08 -->

# How Defender for Cloud Apps helps protect your Asana environment

Asana is a cloud-based tool for project management. Your users can collaborate on projects and tasks across your organization and with partners. Asana holds critical data, which makes it a target for malicious actors.

Connect Asana to Defender for Cloud Apps to get better insights into user activity. You also get threat detection through machine learning anomaly detections.

This article explains how to connect Asana to Defender for Cloud Apps using the App Connector API, configure policies to monitor Asana activity, and automate governance actions.

Main threats include:

- Compromised accounts and insider threats
- Data leakage
- Insufficient security awareness
- Unmanaged bring your own device \(BYOD\)

## Control Asana with policies

The following table lists the policy types you can use to monitor and control Asana activity.

| **Type** | **Name** |
| --- | --- |
| **Built-in anomaly detection policy** | [Activity from anonymous IP addresses](https://learn.microsoft.com/en-us/defender-cloud-apps/anomaly-detection-policy#activity-from-anonymous-ip-addresses)  <br>[Activity from infrequent country](https://learn.microsoft.com/en-us/defender-cloud-apps/anomaly-detection-policy#activity-from-infrequent-country)  <br>[Activity from suspicious IP addresses](https://learn.microsoft.com/en-us/defender-cloud-apps/anomaly-detection-policy#activity-from-suspicious-ip-addresses)  <br>[Impossible travel](https://learn.microsoft.com/en-us/defender-cloud-apps/anomaly-detection-policy#impossible-travel)  <br>[Activity performed by terminated user](https://learn.microsoft.com/en-us/defender-cloud-apps/anomaly-detection-policy#activity-performed-by-terminated-user) \(requires Microsoft Entra ID as IdP\)  <br>[Multiple failed login attempts](https://learn.microsoft.com/en-us/defender-cloud-apps/anomaly-detection-policy#multiple-failed-login-attempts)  <br> |
| **Activity policy** | Built a customized policy by using the [Asana Audit Log](https://developers.asana.com/docs/audit-log-events) activities |

For more information about creating policies, see [Create a policy](https://learn.microsoft.com/en-us/defender-cloud-apps/control-cloud-apps-with-policies#create-a-policy).

## Automate governance controls

You can also automate Asana governance actions to fix detected threats. The following table lists the available actions:

| **Type** | **Action** |
| --- | --- |
| **User governance** | Notify user on alert \(via Microsoft Entra ID\)  <br>Require user to sign in again \(via Microsoft Entra ID\)  <br>Suspend user \(via Microsoft Entra ID\) |

For more information about remediating threats from apps, see [Governing connected apps](https://learn.microsoft.com/en-us/defender-cloud-apps/governance-actions).

## Connect Asana to Defender for Cloud Apps

Use the App Connector APIs to connect Microsoft Defender for Cloud Apps to your existing Asana account. The connection gives you visibility into and control over your organization's Asana use.

### Prerequisites

Before you connect Asana, make sure you meet the following requirements:

- An Asana enterprise account.
- You must be signed-in as an admin to Asana.

### Connect Asana

Collect the access token and workspace ID from Asana by completing the following steps.

1. Sign in to [Asana](https://app.asana.com/) with an admin account.
2. If you have an existing service account, you might need to select **Reset and generate new token** before continuing. Copy the service account token.
3. Copy the workspace ID from the URL and save it for future reference.

### Configure Defender for Cloud Apps

After you collect the required Asana values, complete the connection in Microsoft Defender for Cloud Apps.

1. In the [Microsoft Defender portal](https://security.microsoft.com), navigate to **Settings > Cloud Apps > Connected apps > App Connectors**.
2. Select **Connect an app** and then select **Asana.**
3. Enter an Instance name, and select **Next.**
4. Enter the copied access token and workspace ID in API Key and workspace ID fields. Once entered select **Submit.**
5. Defender for Cloud Apps will start to fetch Asana audit logs once the connection is successfully established.

## Related content

- If you have any problems connecting the app, see [Troubleshooting App Connectors](https://learn.microsoft.com/en-us/defender-cloud-apps/troubleshooting-api-connectors-using-error-messages).
- [Detect cloud threats, compromised accounts, and malicious insiders](https://learn.microsoft.com/en-us/defender-cloud-apps/best-practices#detect-cloud-threats-compromised-accounts-malicious-insiders-and-ransomware)
- [Use the audit trail of activities for forensic investigations](https://learn.microsoft.com/en-us/defender-cloud-apps/best-practices#use-the-audit-trail-of-activities-for-forensic-investigations)
