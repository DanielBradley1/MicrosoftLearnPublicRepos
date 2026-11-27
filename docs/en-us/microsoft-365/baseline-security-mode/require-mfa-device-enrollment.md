<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/baseline-security-mode/require-mfa-device-enrollment?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2026-11-17 -->

# Require MFA for device enrollment

Requiring multifactor authentication \(MFA\) for device enrollment ensures that only verified users can add new devices to your organization through Intune. Device enrollment based solely on passwords leaves organizations vulnerable, as attackers who obtain stolen or phished credentials can silently onboard rogue devices that gain access to corporate data and services. Enforcing MFA adds a strong identity check during enrollment, reducing the risk of unauthorized device additions, limiting attacker persistence, and strengthening your overall access security posture.

For more information, see [Enforce multifactor authentication \(MFA\) for device enrollment](https://learn.microsoft.com/en-us/intune/intune-service/enrollment/multi-factor-authentication).

You need to be a member of the [Global administrator role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference) and [Intune administrator role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#intune-administrator) to be able to configure this setting.

## Why this setting matters

Device enrollment is a critical entry point into your environment. If attackers can enroll devices using only compromised credentials, those devices can become trusted endpoints with ongoing access to apps, data, and internal resources.

This setting helps mitigate those risks by:

- **Blocking credential only enrollment abuse**  
  MFA significantly reduces the effectiveness of phishing and password theft by requiring an additional verification step during enrollment.
- **Preventing silent onboarding of rogue devices**  
  Without MFA, attackers can enroll devices without triggering immediate suspicion. MFA makes unauthorized enrollment attempts far more difficult.
- **Reducing long term attacker persistence**  
  Enrolled devices can provide durable access even after credentials are reset. Enforcing MFA helps prevent attackers from establishing that foothold in the first place.
- **Aligning with Microsoft’s recommended security posture**  
  This setting is marked **Recommended** and **At risk** because password only device enrollment materially increases the likelihood of unauthorized access and data exposure.

## How this setting works

When this setting is enabled:

- **Users must complete MFA** when enrolling devices with Microsoft Intune.
- **Enrollment attempts that rely only on passwords are blocked**, preventing unauthorized device registration.
- **Only authenticated, verified users can add devices** to the organization.
- **Risk from stolen credentials is reduced**, even if usernames and passwords are compromised.

This control ensures that device trust is established only after strong user authentication, helping protect corporate resources from unauthorized or attacker-controlled devices.
