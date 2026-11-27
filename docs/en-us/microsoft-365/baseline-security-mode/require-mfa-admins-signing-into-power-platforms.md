<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/baseline-security-mode/require-mfa-admins-signing-into-power-platforms?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2026-11-17 -->

# Require multifactor authentication for admins signing into Power Platforms

Requiring multifactor authentication \(MFA\) ensures that only strongly verified administrators can access Power Platform and Dynamics 365 administrative portals. MFA provides an additional identity check, beyond just a password, to protect admin accounts from credential theft, phishing, and brute force attacks. When enabled, administrators must enroll and use MFA before signing in to the Power Platform admin center, Dynamics 365 admin center, or Maker portals, ensuring that sensitive administrative controls can't be accessed using stolen or replayed credentials.

This configuration aligns with Microsoft's guidance that MFA significantly reduces the likelihood of unauthorized access by enforcing a second authentication factor and preventing attackers from exploiting compromised passwords to gain high privilege access.

Global administrators can use multifactor authentication through Entra ID, whereas local administrators must use multifactor authentication provided by Power Platform.

For more information, see [Microsoft Entra multifactor authentication](https://learn.microsoft.com/en-us/entra/identity/authentication/concept-mfa-howitworks).

You need to be a member of the [Global administrator role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#global-administrator), [Dynamics 365 administrator role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#dynamics-365-administrator), or [Power Platform Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#power-platform-administrator) to be able to configure this setting.

## Why this setting matters

Administrator accounts represent one of the highest value targets for attackers. Without MFA, a single stolen or guessed password can grant full control over environments, data access, and security configuration. This setting helps mitigate those risks by:

- **Protecting admin accounts from credential theft** MFA blocks attackers who obtain passwords through phishing, malware, or brute force attacks from signing in to administrative portals.
- **Preventing full tenant compromise** The admin center explicitly warns that without MFA, compromised admin accounts can lead to full tenant compromise and data breaches.
- **Ensuring strong verification for sensitive operations** Administrative actions that affect environments, security settings, and data access require proof of identity beyond a password.
- **Aligning with Microsoft's recommended security baseline** This setting is marked **Recommended** and **At risk**, reinforcing that password only admin access is a critical security gap.

## How this setting works

When this setting is enabled:

- **Admin accounts are required to set up MFA** the next time they sign in.
- MFA is enforced for access to:
- Power Platform admin center
- Dynamics 365 admin center
- Power Platform Maker portals
- **Password only sign in is blocked** for administrative access.
- **Authentication is enforced by Microsoft Entra**, ensuring consistent MFA protection across all supported admin entry points.

This configuration ensures that administrative access can't be gained using stolen or replayed credentials alone.

## Additional considerations

The admin center experience provides clear guidance and context for enforcement:

- This setting is labeled **At risk**, highlighting that environments without MFA protected admin access are exposed to credential based attacks.
- The UI emphasizes that **admins will be required to enroll in and use MFA at next sign in**, helping organizations plan rollout and communication.
- Enforcing MFA for admins is a **foundational Zero Trust control**, ensuring that high privilege access is always strongly verified.
- This setting complements **Conditional Access policies**, but ensures MFA protection even when Conditional Access isn't explicitly configured.

Below is an example of a sample csv file to check audit logging to enable ip cookies binding setting. The following fields are not fixed and could change over time.

[![Screenshot of a sample csv for mfa for admin users signing into power platforms setting.](https://learn.microsoft.com/en-us/microsoft-365/baseline-security-mode/media/mfa-for-admin-users.jpg?view=o365-worldwide)](https://learn.microsoft.com/en-us/microsoft-365/baseline-security-mode/media/mfa-for-admin-users.jpg?view=o365-worldwide#lightbox)
