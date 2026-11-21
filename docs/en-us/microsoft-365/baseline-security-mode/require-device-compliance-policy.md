<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/baseline-security-mode/require-device-compliance-policy?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2026-11-17 -->

# Require a device compliance policy

Requiring a device compliance policy ensures that every enrolled device meets your organization's minimum security standards before accessing corporate apps or data. Without this requirement, devices with no compliance policy are treated as compliant by default, which means unmanaged, outdated, or misconfigured devices can still connect to sensitive resources. Enforcing this setting marks such devices as noncompliant and blocks them until a valid compliance policy is applied. This setting helps prevent data exposure, reduces unauthorized access risk, and ensures device level security controls \(such as encryption, OS version checks, or threat protection baselines\) are consistently enforced across your environment.

For more information, see [Devices without a device compliance policy are considered noncompliant](https://learn.microsoft.com/en-us/intune/intune-service/enrollment/create-device-platform-restrictions#create-a-device-platform-restriction).

You need to be a member of the [Global administrator role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference) and [Intune administrator role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#intune-administrator) to be able to configure this setting.

## Why this setting matters

Device compliance policies are a foundational control for protecting corporate data. When devices are allowed to access resources without being evaluated against compliance requirements, organizations lose visibility and control over their security posture.

This setting helps reduce those risks by:

- **Preventing unmanaged or misconfigured devices from accessing data**  
  Devices without a compliance policy may lack encryption, run unsupported OS versions, or miss required security protections.
- **Enforcing conditional access correctly**  
  Compliance policies are often used as signals for Conditional Access. Without this setting, Conditional Access may incorrectly allow access to nonevaluated devices.
- **Reducing the risk of data breaches**  
  Blocking noncompliant devices helps prevent access from devices that don't meet organizational security standards.
- **Aligning with Microsoft’s recommended security baseline**  
  This setting is marked **Recommended** and **At risk** because treating devices without compliance policies as compliant significantly weakens device-based access controls.

## How this setting works

When this setting is enabled:

- **All enrolled devices must have a compliance policy** to be considered compliant.
- **Devices without a compliance policy are marked as noncompliant** and blocked from accessing organizational resources.
- **Admins can review devices without compliance policies** directly in the admin center to understand the impact of enforcement.
- **A detailed CSV report is available for download**, listing devices that currently lack a compliance policy.
- **Access is restored automatically** once a valid compliance policy is assigned and the device meets its requirements.

This approach ensures that device access decisions are always based on evaluated, enforceable security criteria rather than default trust.
