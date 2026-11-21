<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/baseline-security-mode/require-second-admin-approve-sensitive-actions?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2026-11-17 -->

# Require a second admin to approve sensitive actions

Requiring a second administrator to approve sensitive actions adds an essential safeguard against unauthorized or high impact changes in Intune. Without dual approval, a single compromised or misconfigured admin account could perform harmful actions- such as wiping devices, modifying RBAC roles, deploying scripts, or altering app configurations- without detection. Enforcing this setting introduces oversight into high-risk operations, reducing the likelihood of privilege abuse, insider threats, or attacker driven configuration changes. This approval workflow helps ensure that sensitive administrative tasks receive proper review before execution, strengthening the overall security and integrity of your Intune environment.

For more information, see [Enable multiadmin approval](https://learn.microsoft.com/en-us/entra/identity/conditional-access/policy-all-users-device-compliance).

You need to be a member of the [Global administrator role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference) and [Intune administrator role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#intune-administrator) to be able to configure this setting.

## Why this setting matters

Intune administrators have the ability to make changes that can immediately impact devices, users, and security posture across the tenant. When a single admin can perform sensitive actions without review, organizations face increased risk from both external attackers and internal misuse.

This setting helps mitigate those risks by:

- **Preventing single admin misuse or compromise**  
  If an admin account is compromised, attackers can't immediately execute high impact actions without approval from a second administrator.
- **Reducing insider threat and configuration errors**  
  Dual approval introduces checks and balances that help catch mistakes or unauthorized changes before they're applied.
- **Adding accountability to high-risk operations**  
  Sensitive actions such as app creation, device wipe or retirement, RBAC changes, and script deployments require explicit review, improving governance and auditability.
- **Aligning with Microsoft’s recommended security posture**  
  This setting is marked **Recommended** and **At risk** because allowing single admin execution of sensitive actions significantly increases the likelihood of undetected harmful changes.

## How this setting works

When this setting is enabled:

- **Sensitive Intune actions require approval from a second administrator** before they're executed.
- **High impact activities are surfaced for review**, including actions such as app creation, device wipe or deletion, RBAC changes, and script deployments to Windows devices.
- **Admins can review recent sensitive actions** directly in the admin center to understand current activity and risk.
- **A detailed CSV report is available for download**, helping administrators audit actions taken and assess enforcement impact.
- **Unauthorized or accidental changes are blocked** until proper approval is granted.

This approach introduces deliberate friction for high-risk actions, helping ensure that powerful administrative capabilities are exercised safely and intentionally.
