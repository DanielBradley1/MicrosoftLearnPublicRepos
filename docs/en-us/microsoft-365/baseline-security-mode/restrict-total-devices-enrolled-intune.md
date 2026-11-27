<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/baseline-security-mode/restrict-total-devices-enrolled-intune?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2026-11-17 -->

# Restrict the number of devices a user can enroll in Intune

Limiting the number of devices a user can enroll helps reduce the risk of attackers exploiting compromised credentials to register large numbers of rogue devices in your organization. A high enrollment limit increases exposure because one breached account can be used to onboard many unauthorized devices without detection. Enforcing a lower enrollment cap minimizes the blast radius of leaked credentials, prevents mass enrollment attacks, and strengthens overall device governance by ensuring that users can only enroll a controlled number of trusted devices.

For more information, see [Reduce the number of devices a user can enroll into Intune](https://learn.microsoft.com/en-us/intune/intune-service/enrollment/device-limit-intune-azure).

You need to be a member of the [Global administrator role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference) and [Intune administrator role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#intune-administrator) to be able to configure this setting.

## Why this setting matters

User credentials are a common attack target. If an attacker successfully compromises an account, device enrollment limits determine how much damage that account can do.

This setting helps mitigate those risks by:

- **Preventing mass device enrollment attacks**  
  Without limits, attackers can rapidly enroll many rogue devices using a single compromised account, expanding their foothold across the tenant.
- **Reducing the impact of leaked credentials**  
  A lower device limit constrains how many devices an attacker can register, reducing exposure and simplifying incident response.
- **Improving device hygiene and accountability**  
  Enrollment limits help ensure users enroll only devices they actively use and manage, reducing clutter from stale or unnecessary devices.
- **Aligning with Microsoft’s recommended security posture**  
  This setting is marked **Recommended** and **At risk** because unrestricted device enrollment significantly increases the likelihood of unnoticed compromise.

## How this setting works

When this setting is enforced:

- **Users are limited to a defined number of enrolled devices** in Intune.
- **Additional enrollment attempts are blocked** once the limit is reached, preventing further device registrations.
- **Admins must review or remove existing devices** before allowing additional enrollments, helping maintain accurate device inventories.
- **Attackers cannot silently enroll large numbers of devices**, even if credentials are compromised.

This approach limits abuse, improves visibility into enrolled devices, and strengthens overall device lifecycle governance.
