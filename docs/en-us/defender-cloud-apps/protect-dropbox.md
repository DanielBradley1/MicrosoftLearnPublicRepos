<!-- Source: https://learn.microsoft.com/en-us/defender-cloud-apps/protect-dropbox -->
<!-- Sitemap-Last-Modified: 2026-08-08 -->

# How Defender for Cloud Apps helps protect your Dropbox environment

Dropbox is a cloud storage and collaboration tool that lets users share documents across your organization and with partners. However, Dropbox can expose sensitive data to external collaborators or make it publicly available through a shared link. Malicious actors or unaware employees can cause these incidents.

Connecting Dropbox to Defender for Cloud Apps gives you better insight into your users' activities. It provides threat detection through machine learning anomaly detections and information protection detections, such as detecting external information sharing. You can also enable automated remediation controls.

Note

Dropbox changed the way shared folders are stored, moving them to Team Spaces. The Defender for Cloud Apps file scan will be updated in due course to include Team Spaces.

## Main threats

Dropbox environments face the following main threats:

- Compromised accounts and insider threats
- Data leakage
- Insufficient security awareness
- Malware
- Ransomware
- Unmanaged bring your own device \(BYOD\)

## How Defender for Cloud Apps helps to protect your environment

Use the following best practices to protect your Dropbox environment with Defender for Cloud Apps:

- [Detect cloud threats, compromised accounts, and malicious insiders](https://learn.microsoft.com/en-us/defender-cloud-apps/best-practices#detect-cloud-threats-compromised-accounts-malicious-insiders-and-ransomware)
- [Discover, classify, label, and protect regulated and sensitive data stored in the cloud](https://learn.microsoft.com/en-us/defender-cloud-apps/best-practices#discover-classify-label-and-protect-regulated-and-sensitive-data-stored-in-the-cloud)
- [Enforce DLP and compliance policies for data stored in the cloud](https://learn.microsoft.com/en-us/defender-cloud-apps/best-practices#enforce-dlp-and-compliance-policies-for-data-stored-in-the-cloud)
- [Limit exposure of shared data and enforce collaboration policies](https://learn.microsoft.com/en-us/defender-cloud-apps/best-practices#limit-exposure-of-shared-data-and-enforce-collaboration-policies)
- [Use the audit trail of activities for forensic investigations](https://learn.microsoft.com/en-us/defender-cloud-apps/best-practices#use-the-audit-trail-of-activities-for-forensic-investigations)

## Control Dropbox with built-in policies and policy templates

You can use the following built-in policy templates to detect and notify you about potential threats:

Important

File policies retire on January 6, 2027. To maintain file-based data protection for this app, [migrate to Microsoft Purview DLP or auto-labeling policies](https://learn.microsoft.com/en-us/defender-cloud-apps/migrate-file-policies-to-purview).

| Type | Name |
| --- | --- |
| Built-in anomaly detection policy | [Activity from anonymous IP addresses](https://learn.microsoft.com/en-us/defender-cloud-apps/anomaly-detection-policy#activity-from-anonymous-ip-addresses)  <br>[Activity from infrequent country](https://learn.microsoft.com/en-us/defender-cloud-apps/anomaly-detection-policy#activity-from-infrequent-country)  <br>[Activity from suspicious IP addresses](https://learn.microsoft.com/en-us/defender-cloud-apps/anomaly-detection-policy#activity-from-suspicious-ip-addresses)  <br>[Impossible travel](https://learn.microsoft.com/en-us/defender-cloud-apps/anomaly-detection-policy#impossible-travel)  <br>[Activity performed by terminated user](https://learn.microsoft.com/en-us/defender-cloud-apps/anomaly-detection-policy#activity-performed-by-terminated-user) \(requires Microsoft Entra ID as IdP\)  <br>[Malware detection](https://learn.microsoft.com/en-us/defender-cloud-apps/anomaly-detection-policy#malware-detection)  <br>[Multiple failed login attempts](https://learn.microsoft.com/en-us/defender-cloud-apps/anomaly-detection-policy#multiple-failed-login-attempts)  <br>[Ransomware detection](https://learn.microsoft.com/en-us/defender-cloud-apps/anomaly-detection-policy#ransomware-activity)  <br>[Unusual file deletion activities](https://learn.microsoft.com/en-us/defender-cloud-apps/anomaly-detection-policy#unusual-activities-by-user)  <br>[Unusual file share activities](https://learn.microsoft.com/en-us/defender-cloud-apps/anomaly-detection-policy#unusual-activities-by-user)  <br>[Unusual multiple file download activities](https://learn.microsoft.com/en-us/defender-cloud-apps/anomaly-detection-policy#unusual-activities-by-user) |
| Activity policy template | Logon from a risky IP address  <br>Mass download by a single user  <br>Potential ransomware activity |
| File policy template | Detect a file shared with an unauthorized domain  <br>Detect a file shared with personal email addresses  <br>Detect files with PII/PCI/PHI |

For more information about creating policies, see [Create a policy in Defender for Cloud Apps](https://learn.microsoft.com/en-us/defender-cloud-apps/control-cloud-apps-with-policies#create-a-policy).

## Automate governance controls

You can also apply and automate Dropbox governance actions to fix detected threats:

| Type | Action |
| --- | --- |
| Data governance | - Remove direct shared link  <br>- Send DLP violation digest to file owners  <br>- Trash file |
| User governance | - Notify user on alert \(via Microsoft Entra ID\)  <br>- Require user to sign in again \(via Microsoft Entra ID\)  <br>- Suspend user \(via Microsoft Entra ID\) |

To learn more about fixing threats from apps, see [Governing connected apps](https://learn.microsoft.com/en-us/defender-cloud-apps/governance-actions).

## Protect Dropbox in real time

Review our best practices for [securing and collaborating with external users](https://learn.microsoft.com/en-us/defender-cloud-apps/best-practices#secure-collaboration-with-external-users-by-enforcing-real-time-session-controls) and [blocking and protecting the download of sensitive data to unmanaged or risky devices](https://learn.microsoft.com/en-us/defender-cloud-apps/best-practices#block-and-protect-download-of-sensitive-data-to-unmanaged-or-risky-devices).

## SaaS security posture management for Dropbox

[Connect Dropbox](#connect-dropbox-to-microsoft-defender-for-cloud-apps) to automatically get security posture recommendations for Dropbox in Microsoft Secure Score. In Secure Score, select **Recommended actions** and filter by **Product** = **Dropbox**. Dropbox supports security recommendations to *Enable web session timeout for web users*.

For more information, see:

- [Security posture management for SaaS apps](https://learn.microsoft.com/en-us/defender-cloud-apps/security-saas)
- [Microsoft Secure Score](https://learn.microsoft.com/en-us/microsoft-365/security/defender/microsoft-secure-score)

## Connect Dropbox to Microsoft Defender for Cloud Apps

Use the following instructions to connect Microsoft Defender for Cloud Apps to your existing Dropbox account using the connector APIs. Connector APIs let Defender for Cloud Apps connect directly to supported apps for monitoring and governance. This connection gives you visibility into and control over Dropbox use.

Dropbox enables access to files from shared links without signing in. Defender for Cloud Apps registers users who access files without signing in as Unauthenticated users. If you see unauthenticated Dropbox users, it might indicate users who aren't from your organization, or they might be recognized users from within your organization who didn't sign in.

**To connect Dropbox to Defender for Cloud Apps**

1. In the Microsoft Defender Portal, select **Settings**. Then choose **Cloud Apps**. Under **Connected apps**, select **App Connectors**.
2. In the **App connectors** page, select **+Connect an app**, followed by **Dropbox**.

   [![Screenshot that shows how to connect Dropbox in the Microsoft Defender portal.](https://learn.microsoft.com/en-us/defender-cloud-apps/media/connect-dropbox/connect-an-app-drop-box.png)](https://learn.microsoft.com/en-us/defender-cloud-apps/media/connect-dropbox/connect-an-app-drop-box.png#lightbox)
3. In the next window, give the connector a name and select **Next**.
4. In the **Enter details** window, enter the admin account email address.
5. In the **Follow the link** window, select **Connect Dropbox**.

   The Dropbox sign in page opens. Enter your credentials to allow Defender for Cloud Apps access to your team's Dropbox instance.
6. Dropbox asks you if you want to allow Defender for Cloud Apps access to your team information, activity log, and perform activities as a team member. To proceed, select **Allow**.
7. Back in the Defender for Cloud Apps console, you should receive a message that Dropbox was successfully connected.
8. In the Microsoft Defender Portal, select **Settings**. Then choose **Cloud Apps**. Under **Connected apps**, select **App Connectors**. Make sure the status of the connected App Connector is **Connected**.

   After connecting DropBox, you'll receive events for seven days prior to connection.

Note

Any Dropbox events for adding a file are displayed in Defender for Cloud Apps as Upload file to align to all other apps connected to Defender for Cloud Apps.

If you have any problems connecting the app, see [Troubleshooting App Connectors](https://learn.microsoft.com/en-us/defender-cloud-apps/troubleshooting-api-connectors-using-error-messages).

## Related content

- [Control cloud apps with policies](https://learn.microsoft.com/en-us/defender-cloud-apps/control-cloud-apps-with-policies)
