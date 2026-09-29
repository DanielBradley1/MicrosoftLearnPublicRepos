<!-- Source: https://learn.microsoft.com/en-us/defender-cloud-apps/protect-miro -->
<!-- Sitemap-Last-Modified: 2026-08-11 -->

# How Defender for Cloud Apps helps protect your Miro environment

Miro is an online workspace that enables distributed, cross-functional teams organize and collaborate on projects. Miro holds critical data of your organization, which makes Miro a target for malicious actors.

Connecting Miro to Defender for Cloud Apps gives you improved insights into your users' activities and provides threat detection using machine learning based anomaly detections. Before you connect, review the [prerequisites for connecting Miro to Defender for Cloud Apps](#connect-miro-to-microsoft-defender-for-cloud-apps) to ensure your environment is ready.

## Main threats to your Miro environment

The main threats to consider in a Miro environment include the following:

- Compromised accounts and insider threats
- Data leakage
- Insufficient security awareness
- Unmanaged bring your own device \(BYOD\)

## How Defender for Cloud Apps helps to protect your environment

Defender for Cloud Apps helps protect your Miro environment in the following ways:

- [Detect cloud threats, compromised accounts, and malicious insiders](https://learn.microsoft.com/en-us/defender-cloud-apps/best-practices#detect-cloud-threats-compromised-accounts-malicious-insiders-and-ransomware)
- [Use the audit trail of activities for forensic investigations](https://learn.microsoft.com/en-us/defender-cloud-apps/best-practices#use-the-audit-trail-of-activities-for-forensic-investigations)

## Control Miro with policies

The following table lists the detection policies available for Miro in Defender for Cloud Apps.

| **Type** | **Name** |
| --- | --- |
| Built-in anomaly detection policy | [Activity from anonymous IP addresses](https://learn.microsoft.com/en-us/defender-cloud-apps/anomaly-detection-policy#activity-from-anonymous-ip-addresses)  <br>[Activity from infrequent country](https://learn.microsoft.com/en-us/defender-cloud-apps/anomaly-detection-policy#activity-from-infrequent-country)  <br>[Activity from suspicious IP addresses](https://learn.microsoft.com/en-us/defender-cloud-apps/anomaly-detection-policy#activity-from-suspicious-ip-addresses)  <br>[Impossible travel](https://learn.microsoft.com/en-us/defender-cloud-apps/anomaly-detection-policy#impossible-travel)  <br>[Activity performed by terminated user](https://learn.microsoft.com/en-us/defender-cloud-apps/anomaly-detection-policy#activity-performed-by-terminated-user) \(requires Microsoft Entra ID as IdP\)  <br>[Multiple failed login attempts](https://learn.microsoft.com/en-us/defender-cloud-apps/anomaly-detection-policy#multiple-failed-login-attempts)  <br> |
| Activity policy | Built a customized policy by using the [Miro Audit Log](https://help.miro.com/hc/en-us/articles/360017571434-Audit-logs) activities |

For more information about creating policies, see [Create a policy](https://learn.microsoft.com/en-us/defender-cloud-apps/control-cloud-apps-with-policies#create-a-policy).

## Automate governance controls

In addition to monitoring for potential threats, you can apply and automate the following Miro governance actions to remediate detected threats.

### Supported governance actions

The following table lists the governance actions supported for Miro.

| **Type** | **Action** |
| --- | --- |
| User governance | Notify user on alert \(via Microsoft Entra ID\)  <br>Require user to sign in again \(via Microsoft Entra ID\)  <br>Suspend user \(via Microsoft Entra ID\) |

For more information about remediating threats from apps, see [Governing connected apps](https://learn.microsoft.com/en-us/defender-cloud-apps/governance-actions).

## Connect Miro to Microsoft Defender for Cloud Apps

This section provides instructions for connecting Microsoft Defender for Cloud Apps to your existing Miro account using the App Connector APIs. This connection gives you visibility into and control over Miro usage.

**Prerequisites**:

- You must have a Miro account with an enterprise plan.

### Configure Miro

Perform the following steps in Miro to create the app registration needed for the connector:

1. Sign into [Miro](https://miro.com/app/dashboard/) portal with a company admin account.
2. Create a developer team with default permissions.
3. Create a new application in the developer team and ensure the “Expire user authentication token” setting is checked.
4. Copy the **Client ID** and **Client secret**. You'll need them later.
5. Configure 'OAuth2.0' by setting the redirect URL to 'https://portal.cloudappsecurity.com/api/oauth/saga'.
6. Grant these required permissions, and then select **Install app and get OAuth token**.

- ‘auditlogs:read’
- ‘organization:read’

### Connect Microsoft Defender for Cloud Apps

After you configure Miro, complete the connection in Defender for Cloud Apps by following these steps:

1. In the [Defender for Cloud Apps](https://portal.cloudAppSecurity.com) portal, navigate to Investigate > Connected apps.
2. In the **App connectors** page, select **Connect an app**, and choose **Miro**.
3. In the connection wizard, enter a name for Miro connection, and select **Connect Miro**.
4. Enter the **Client ID, Client secret** and select **Connect in Miro**.
5. Select the Miro team that you want to connect with Defender for Cloud Apps and select **Add** again. Note that this Miro team is different from the developer team in which you created the app.
6. Select **Test now** to make sure the connection succeeded. Audit events start flowing into Defender for Cloud apps from the time the connection is successfully established.

## Next steps

- If you have any problems connecting the app, see [Troubleshooting App Connectors](https://learn.microsoft.com/en-us/defender-cloud-apps/troubleshooting-api-connectors-using-error-messages).
- [Control cloud apps with policies](https://learn.microsoft.com/en-us/defender-cloud-apps/control-cloud-apps-with-policies)
