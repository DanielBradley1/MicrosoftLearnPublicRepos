<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/baseline-security-mode/enable-continuous-access-evaluation?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2026-11-17 -->

# Enable continuous access evaluation

Enabling Continuous Access Evaluation \(CAE\) provides real time enforcement of authentication and authorization policies across Dynamics 365 and Power Platform services. CAE continuously monitors for critical security events, such as password resets, account disablement, session revocation, or Conditional Access policy changes, and immediately invalidates active sessions when these events occur. This invalidation prevents attackers from continuing to use stolen or replayed tokens after credentials are changed or access is revoked.

By enforcing access at the moment conditions change rather than waiting for traditional token expiration, CAE ensures user sessions remain aligned with your organization's latest security posture. It also improves resilience by allowing the use of long lived tokens while still enabling near real time revocation when risk is detected.

You need to be a member of the [Global administrator role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#global-administrator), [Dynamics 365 administrator role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#dynamics-365-administrator), or [Power Platform Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#power-platform-administrator) to be able to configure this setting.

Note

Continuous Access Evaluation \(CAE\) is turned ON by default.

For more information, see [Continuous Access Evaluation.](https://learn.microsoft.com/en-us/power-platform/admin/continuous-access-evaluation)

## Why this setting matters

Without Continuous Access Evaluation, active sessions can remain valid even after critical security changes occur. This behavior creates a window of exposure where attackers may continue to access resources using previously issued tokens.

This setting helps mitigate those risks by:

- **Closing the token expiration security gap** CAE enforces policy changes in near real time instead of waiting for access tokens to expire, which can otherwise take up to an hour.
- **Preventing continued access after credential or account changes** If a password is reset or an account is disabled, CAE immediately revokes active sessions to prevent unauthorized use.
- **Reducing the impact of stolen or replayed tokens** Attackers can't rely on long lived tokens to maintain access once risk or policy conditions change.
- **Aligning with Microsoft's recommended security posture** This setting is marked Recommended and At risk, indicating that environments without CAE remain exposed to unauthorized access after critical changes.

## How this setting works

When this setting is enabled:

- **Active sessions are continuously evaluated** against user critical events and policy changes.
- **Sessions are revoked or reauthentication is required immediately** when events such as the following occur:

  - Password changes or resets
  - Account disablement or deletion
  - Explicit session revocation

- **Conditional Access changes are enforced in near real time**, ensuring access reflects current policy state.
- **Long lived tokens remain usable** for normal operations, improving service resiliency while still allowing rapid revocation when required.

This configuration ensures that access decisions always reflect the most current security conditions.

## Additional considerations

The admin center experience highlights both risk and impact to help guide enforcement:

- This setting is explicitly labeled **At risk** and **Recommended**, reinforcing that delayed session revocation is a high impact security gap.
- The admin center warns that without CAE, active sessions remain valid even after password resets or account disablement, increasing exposure to unauthorized access.
- CAE enforcement is **near real time**, but the first request immediately after enabling the setting may not be evaluated instantly.
- Continuous Access Evaluation is currently supported for **Dataverse** within Power Platform, with support expanding over time.
- CAE strengthens Zero Trust adoption by continuously validating access rather than relying on implicit trust until token expiration.

Below is an example of a sample csv file to check audit logging for enable continuous access evaluation setting. The following fields are not fixed and could change over time.

[![Screenshot of a sample csv to download for audit logging for continuous access evaluation in dynamics 365.](https://learn.microsoft.com/en-us/microsoft-365/baseline-security-mode/media/enable-continuous-access-evaluation.jpg?view=o365-worldwide)](https://learn.microsoft.com/en-us/microsoft-365/baseline-security-mode/media/enable-continuous-access-evaluation.jpg?view=o365-worldwide#lightbox)
