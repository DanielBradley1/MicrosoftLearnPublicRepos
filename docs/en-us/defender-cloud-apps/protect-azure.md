<!-- Source: https://learn.microsoft.com/en-us/defender-cloud-apps/protect-azure -->
<!-- Sitemap-Last-Modified: 2026-08-08 -->

# How Defender for Cloud Apps helps protect your Azure environment

Azure is a cloud provider that lets your organization host and manage its workloads. Cloud hosting has many benefits, but it can also expose critical assets to threats. These assets include storage with sensitive data, compute resources that run key apps, ports, and virtual private networks.

When you connect Azure to Defender for Cloud Apps, you can secure your assets and spot threats. The service monitors admin and sign-in activity. It alerts you to brute force attacks, misuse of privileged accounts, and unusual VM deletions.

## Main threats

The main threats to your Azure environment include:

- Abuse of cloud resources
- Compromised accounts and insider threats
- Data leakage
- Resource misconfiguration and insufficient access control

## How Defender for Cloud Apps helps to protect your environment

Use the following best practices to protect your Azure environment with Defender for Cloud Apps:

- [Detect cloud threats, compromised accounts, and malicious insiders](https://learn.microsoft.com/en-us/defender-cloud-apps/best-practices#detect-cloud-threats-compromised-accounts-malicious-insiders-and-ransomware)
- [Limit exposure of shared data and enforce collaboration policies](https://learn.microsoft.com/en-us/defender-cloud-apps/best-practices#limit-exposure-of-shared-data-and-enforce-collaboration-policies)
- [Use the audit trail of activities for forensic investigations](https://learn.microsoft.com/en-us/defender-cloud-apps/best-practices#use-the-audit-trail-of-activities-for-forensic-investigations)

## Control Azure with built-in policies and policy templates

You can use the following built-in policy templates to detect and notify you about potential threats:

| Type | Name |
| --- | --- |
| Built-in anomaly detection policy | [Activity from anonymous IP addresses](https://learn.microsoft.com/en-us/defender-cloud-apps/anomaly-detection-policy#activity-from-anonymous-ip-addresses)  <br>[Activity from infrequent country](https://learn.microsoft.com/en-us/defender-cloud-apps/anomaly-detection-policy#activity-from-infrequent-country)  <br>[Activity from suspicious IP addresses](https://learn.microsoft.com/en-us/defender-cloud-apps/anomaly-detection-policy#activity-from-suspicious-ip-addresses)  <br>[Activity performed by terminated user](https://learn.microsoft.com/en-us/defender-cloud-apps/anomaly-detection-policy#activity-performed-by-terminated-user) \(requires Microsoft Entra ID as IdP\)  <br>[Multiple failed login attempts](https://learn.microsoft.com/en-us/defender-cloud-apps/anomaly-detection-policy#multiple-failed-login-attempts)  <br>[Unusual administrative activities](https://learn.microsoft.com/en-us/defender-cloud-apps/anomaly-detection-policy#unusual-activities-by-user) |

For more information about creating policies, see [Create a policy](https://learn.microsoft.com/en-us/defender-cloud-apps/control-cloud-apps-with-policies#create-a-policy).

## Automate governance controls

You can also automate Azure governance actions to fix detected threats. The following table lists the available actions:

| Type | Action |
| --- | --- |
| User governance | - Notify user on alert \(via Microsoft Entra ID\)  <br>- Require user to sign in again \(via Microsoft Entra ID\)  <br>- Suspend user \(via Microsoft Entra ID\) |

For more information about remediating threats from apps, see [Governing connected apps](https://learn.microsoft.com/en-us/defender-cloud-apps/governance-actions).

## Protect Azure in real time

Review best practices for [securing and collaborating with guests](https://learn.microsoft.com/en-us/defender-cloud-apps/best-practices#secure-collaboration-with-external-users-by-enforcing-real-time-session-controls) and [blocking and protecting the download of sensitive data to unmanaged or risky devices](https://learn.microsoft.com/en-us/defender-cloud-apps/best-practices#block-and-protect-download-of-sensitive-data-to-unmanaged-or-risky-devices).

## Connect Azure to Microsoft Defender for Cloud Apps

Use the app connector API to connect your Azure account to Defender for Cloud Apps. This connection gives you visibility into and control over Azure use. To learn how Defender for Cloud Apps protects Azure, see [Protect Azure](https://learn.microsoft.com/en-us/defender-cloud-apps/protect-azure).

### Prerequisites

Before you connect Azure to Microsoft Defender for Cloud Apps, make sure that the user connecting Azure has the **Security administrator** role in Azure Active Directory.

- The user connecting Azure must have a **Security administrator** role in Azure Active Directory.

### Scope and limitations

When you connect Azure to Defender for Cloud Apps, keep in mind the following scope and limitations:

> - Defender for Cloud Apps displays activities from **all** subscriptions.
> - User account information is populated in Defender for Cloud Apps as users perform activities in Azure.
> - Defender for Cloud Apps monitors ARM activities only.

### Connect Azure to Defender for Cloud Apps

To connect Azure to Defender for Cloud Apps, follow these steps:

1. In the Microsoft Defender Portal, select **Settings**. Then choose **Cloud Apps**. Under **Connected apps**, select **App Connectors**.
2. In the **App connectors** page, select **+Connect an app**, followed by **Microsoft Azure**.

   ![Screenshot that shows the Azure connector in the Defender portal.](https://learn.microsoft.com/en-us/defender-cloud-apps/media/connect-azure-menu.png)
3. In the **Connect Microsoft Azure** page, select **Connect Microsoft Azure**.

   ![Screenshot that shows the Connect Microsoft Azure page in the Defender portal.](https://learn.microsoft.com/en-us/defender-cloud-apps/media/connect-azure.png)
4. In the Microsoft Defender Portal, select **Settings**. Then choose **Cloud Apps**. Under **Connected apps**, select **App Connectors**. Make sure the status of the connected App Connector is **Connected**.

Note

After the Azure connection is established, Defender for Cloud Apps pulls data from that point forward.

## Next steps

- If you have any problems connecting the app, see [Troubleshooting App Connectors](https://learn.microsoft.com/en-us/defender-cloud-apps/troubleshooting-api-connectors-using-error-messages).
- To learn how to create and manage policies for connected apps, see [Control cloud apps with policies](https://learn.microsoft.com/en-us/defender-cloud-apps/control-cloud-apps-with-policies).
