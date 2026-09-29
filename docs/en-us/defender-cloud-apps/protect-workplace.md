<!-- Source: https://learn.microsoft.com/en-us/defender-cloud-apps/protect-workplace -->
<!-- Sitemap-Last-Modified: 2026-08-11 -->

# How Defender for Cloud Apps helps protect your Workplace environment \(Preview\)

Workplace by Meta is a collaboration tool built by Meta. It brings group work, instant messaging, video calls, and news sharing into one place. Cloud collaboration has many benefits, but it can also expose critical assets to threats. These assets include messages, posts, and files that might contain sensitive data or partnership details. You need continuous monitoring to stop malicious actors or careless insiders from leaking this data.

Connect Workplace by Meta to Defender for Cloud Apps to get better insights into user activity and detect unusual behavior.

## Main threats to Workplace by Meta

The main threats to Workplace by Meta include the following:

- Compromised accounts and insider threats
- Insufficient security awareness
- Unmanaged bring your own device \(BYOD\)

## How Defender for Cloud Apps helps to protect your environment

Defender for Cloud Apps helps protect your Workplace by Meta environment in the following ways:

- [Detect cloud threats, compromised accounts, and malicious insiders](https://learn.microsoft.com/en-us/defender-cloud-apps/best-practices#detect-cloud-threats-compromised-accounts-malicious-insiders-and-ransomware)
- [Use the audit trail of activities for forensic investigations](https://learn.microsoft.com/en-us/defender-cloud-apps/best-practices#use-the-audit-trail-of-activities-for-forensic-investigations)

## Control Workplace by Meta with policies

The following table lists the policy types available for controlling Workplace by Meta:

| Type | Name |
| --- | --- |
| Built-in anomaly detection policy | [Activity from anonymous IP addresses](https://learn.microsoft.com/en-us/defender-cloud-apps/anomaly-detection-policy#activity-from-anonymous-ip-addresses) [Activity from infrequent country/region](https://learn.microsoft.com/en-us/defender-cloud-apps/anomaly-detection-policy#activity-from-infrequent-country) [Activity from suspicious IP addresses](https://learn.microsoft.com/en-us/defender-cloud-apps/anomaly-detection-policy#activity-from-suspicious-ip-addresses) [Impossible travel](https://learn.microsoft.com/en-us/defender-cloud-apps/anomaly-detection-policy#impossible-travel) [Activity performed by terminated user](https://learn.microsoft.com/en-us/defender-cloud-apps/anomaly-detection-policy#activity-performed-by-terminated-user) \(requires Microsoft Entra ID as the identity provider \(IdP\)\) [Multiple failed login attempts](https://learn.microsoft.com/en-us/defender-cloud-apps/anomaly-detection-policy#multiple-failed-login-attempts) [Unusual administrative activities](https://learn.microsoft.com/en-us/defender-cloud-apps/anomaly-detection-policy#unusual-activities-by-user) [Unusual impersonated activities](https://learn.microsoft.com/en-us/defender-cloud-apps/anomaly-detection-policy#unusual-activities-by-user) |
| Activity policy | Built a customized policy by the Workplace by Meta activities |

For more information about creating policies, see [Create a policy](https://learn.microsoft.com/en-us/defender-cloud-apps/control-cloud-apps-with-policies#create-a-policy).

## Automate governance controls

Beyond monitoring for threats, you can also automate Workplace governance actions to fix detected issues:

| Type | Action |
| --- | --- |
| User governance | Notify user on alert \(via Microsoft Entra ID\) Require user to sign in again \(via Microsoft Entra ID\) Suspend user \(via Microsoft Entra ID\) |

For more information about remediating threats from apps, see [Governing connected apps](https://learn.microsoft.com/en-us/defender-cloud-apps/governance-actions).

## Protect Workplace by Meta in real time

Review our best practices for [securing and collaborating with external users](https://learn.microsoft.com/en-us/defender-cloud-apps/best-practices#secure-collaboration-with-external-users-by-enforcing-real-time-session-controls) and [blocking and protecting the download of sensitive data to unmanaged or risky devices](https://learn.microsoft.com/en-us/defender-cloud-apps/best-practices#block-and-protect-download-of-sensitive-data-to-unmanaged-or-risky-devices).

## SaaS security posture management for Workplace by Meta \(Preview\)

When you connect Workplace by Meta to Defender for Cloud Apps using the API connector, you automatically get security posture recommendations for Workplace in Microsoft Secure Score. In Secure Score, select **Recommended actions** and filter by **Product** = **Workplace**. Workplace supports security recommendations to *Adopt SSO \(Single sign on\) in Workplace by Meta*.

For more information, see:

- [Security posture management for SaaS apps](https://learn.microsoft.com/en-us/defender-cloud-apps/security-saas)
- [Microsoft Secure Score](https://learn.microsoft.com/en-us/microsoft-365/security/defender/microsoft-secure-score)

## Connect Workplace by Meta to Microsoft Defender for Cloud Apps

The following information describes the current support status for connecting Workplace by Meta to Defender for Cloud Apps using the API connector.

Note

Due to the [Workplace from Meta planned deprecation notice](https://www.workplace.com/help/work/1167689491269151) by Meta of Workplace from Meta, we no longer support new connections to the Workplace from Meta API connector. If you have an existing Workplace from Meta connection, it will continue to work as expected.

## Next steps

[Control cloud apps with policies](https://learn.microsoft.com/en-us/defender-cloud-apps/control-cloud-apps-with-policies)

If you run into any problems, we're here to help. To get assistance or support for your product issue, please [open a support ticket](https://learn.microsoft.com/en-us/defender-xdr/contact-defender-support).
