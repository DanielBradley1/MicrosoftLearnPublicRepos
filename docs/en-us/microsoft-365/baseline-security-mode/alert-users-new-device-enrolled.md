<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/baseline-security-mode/alert-users-new-device-enrolled?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2026-11-17 -->

# Alert users when a new device is enrolled

Unauthorized device enrollments can give attackers a long-term foothold in an organization, especially if compromised credentials are used to silently register rogue devices. Enabling this setting ensures that users receive notifications whenever a new device is enrolled with their account, helping them quickly identify suspicious activity and report unexpected enrollments. This reduces the risk of persistent access, data theft, and attacker-controlled devices operating unnoticed within the environment. Enforcing this requirement strengthens overall tenant security by providing additional enrollment notification channels for awareness.

For more information, see [Enable enrollment notifications for new device enrollment](https://learn.microsoft.com/en-us/intune/intune-service/enrollment/enrollment-notifications).

## Why this setting matters

Attackers who obtain valid user credentials can enroll devices without triggering immediate security warnings. Without user notifications, these unauthorized enrollments may go unnoticed, allowing attackers to maintain persistent access to corporate resources.

This setting helps mitigate those risks by:

- **Detecting unauthorized device enrollment early**  
  Notifications alert users as soon as a device is enrolled with their account, enabling faster identification of suspicious or unexpected activity.
- **Reducing long term attacker persistence**  
  Rogue devices enrolled silently can be used for data access, lateral movement, or long-term surveillance. Alerts help disrupt these scenarios.
- **Sharing responsibility between users and IT**  
  Users act as an additional detection layer by confirming whether a device enrollment is legitimate or should be investigated.
- **Aligning with Microsoft’s recommended security posture**  
  This setting is marked **Recommended** because missing enrollment notifications significantly increases the likelihood of undetected device compromise.

## How this setting works

When this setting is enabled:

- **Users receive notifications** whenever a new device is enrolled using their account.
- **Unexpected enrollments can be quickly reported**, allowing IT administrators to investigate and remediate potential compromise.
- **The Intune admin center highlights users who are not receiving enrollment notifications**, helping administrators understand the impact of enabling this recommendation.
- **Administrators can download a detailed CSV report** showing affected users, making it easier to plan communication and enforcement.

This approach improves visibility into device enrollment activity and helps prevent unauthorized devices from operating unnoticed in the environment.
