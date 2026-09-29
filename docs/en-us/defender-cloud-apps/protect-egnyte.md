<!-- Source: https://learn.microsoft.com/en-us/defender-cloud-apps/protect-egnyte -->
<!-- Sitemap-Last-Modified: 2026-08-08 -->

# How Defender for Cloud Apps helps protect your Egnyte environment

Egnyte is a cloud platform for file sharing and data governance. Cloud tools like Egnyte help teams work together, but they can also expose critical assets to threats. You need to monitor Egnyte so that bad actors or careless insiders can't leak sensitive data.

Connecting Egnyte to Defender for Cloud Apps gives you improved insights into your users' activities and provides threat detection for anomalous behavior.

## Main threats

Using Egnyte without Defender for Cloud Apps exposes your organization to the following threats:

- Compromised accounts and insider threats
- Insufficient security awareness
- Unmanaged bring your own device \(BYOD\)

## How Defender for Cloud Apps helps to protect your environment

Defender for Cloud Apps helps protect your Egnyte environment in the following ways:

- [Detect cloud threats, compromised accounts, and malicious insiders](https://learn.microsoft.com/en-us/defender-cloud-apps/best-practices#detect-cloud-threats-compromised-accounts-malicious-insiders-and-ransomware)
- [Use the audit trail of activities for forensic investigations](https://learn.microsoft.com/en-us/defender-cloud-apps/best-practices#use-the-audit-trail-of-activities-for-forensic-investigations)

## Control Egnyte with policies

The following table lists the policy types you can use to monitor and control Egnyte activities:

| **Type** | **Name** |
| --- | --- |
| Built-in anomaly detection policy | [Activity from anonymous IP addresses](https://learn.microsoft.com/en-us/defender-cloud-apps/anomaly-detection-policy#activity-from-anonymous-ip-addresses)  <br>[Activity from infrequent countries/regions](https://learn.microsoft.com/en-us/defender-cloud-apps/anomaly-detection-policy#activity-from-infrequent-country)  <br>[Activity from suspicious IP addresses](https://learn.microsoft.com/en-us/defender-cloud-apps/anomaly-detection-policy#activity-from-suspicious-ip-addresses)  <br>[Impossible travel](https://learn.microsoft.com/en-us/defender-cloud-apps/anomaly-detection-policy#impossible-travel)  <br>[Activity performed by terminated user](https://learn.microsoft.com/en-us/defender-cloud-apps/anomaly-detection-policy#activity-performed-by-terminated-user) \(requires Microsoft Entra ID as IdP\)  <br>[Multiple failed login attempts](https://learn.microsoft.com/en-us/defender-cloud-apps/anomaly-detection-policy#multiple-failed-login-attempts) |
| Activity policy | Build a customized policy by the Egnyte activities |

For more information about creating policies, see [Create a policy](https://learn.microsoft.com/en-us/defender-cloud-apps/control-cloud-apps-with-policies#create-a-policy).

## Automate governance controls

You can also automate Egnyte governance actions to respond to detected threats:

| **Type** | **Action** |
| --- | --- |
| User governance | Notify user on alert \(via Microsoft Entra ID\)  <br>Require user to sign in again \(via Microsoft Entra ID\)  <br>Suspend user \(via Microsoft Entra ID\) |

For more information about remediating threats from apps, see [Governing connected apps](https://learn.microsoft.com/en-us/defender-cloud-apps/governance-actions).

## Protect Egnyte in real time

Review our best practices for [securing and collaborating with external users](https://learn.microsoft.com/en-us/defender-cloud-apps/best-practices#secure-collaboration-with-external-users-by-enforcing-real-time-session-controls) and [blocking and protecting the download of sensitive data to unmanaged or risky devices](https://learn.microsoft.com/en-us/defender-cloud-apps/best-practices#block-and-protect-download-of-sensitive-data-to-unmanaged-or-risky-devices).

## Connect Egnyte to Microsoft Defender for Cloud Apps

Use the App Connector APIs to connect Microsoft Defender for Cloud Apps to your existing Egnyte environment. The resulting connection gives you visibility into and control over your organization's use of Egnyte.

### Prerequisites

Make sure you meet the following requirements before you connect Egnyte to Defender for Cloud Apps:

- The authorizing user must be one of the following:

  - Power user with **can run reports** role
  - Administrator

- Audit reporting must be available in Egnyte's plan

**To connect Egnyte to Microsoft Defender for Cloud Apps**:

1. In the Microsoft Defender Portal, select **Settings**. Then choose **Cloud Apps**. Under **Connected apps**, select **App Connectors**.
2. In the **App connectors** page, select **+Connect an app**, and then select **Egnyte**.
3. In the window that appears, give the connector a descriptive name, and then select **Next**.
4. In the **Enter details** page, in **Application URL**, insert your Egnyte URL by using the following format: `https://<domain_name>.egnyte.com`
5. Select **Next**.
6. Select **Connect Egnyte**.
7. In the redirected page, select **Allow**.
8. In the Microsoft Defender Portal, select **Settings**. Then choose **Cloud Apps**. Under **Connected apps**, select **App Connectors**. Make sure the status of the connected App Connector is **Connected**.

Note

- Microsoft recommends using a short lived access token. Egnyte doesn't currently support short lived tokens. We recommend refreshing your access token every 6 months as a security best practice. To refresh the access token, revoke the old token. For more information, see [Revoking an oAuth token](https://developers.egnyte.com/docs/read/Public_API_Authentication#Revoking-an-OAuth-Token). Once the old token is revoked, reconnect the Egnyte connector.
- Microsoft Defender for Cloud Apps intentionally provides a lower rate limit than Egnyte's maximum to avoid exceeding the API constraints. For more information, see the relevant Egnyte documentation [Rate limiting](https://developers.egnyte.com/docs/read/Best_Practices) and [Audit Reporting API v2](https://developers.egnyte.com/docs/read/Audit_Reporting_API_V2).

## Next steps

- [Control cloud apps by using policies](https://learn.microsoft.com/en-us/defender-cloud-apps/control-cloud-apps-with-policies)
