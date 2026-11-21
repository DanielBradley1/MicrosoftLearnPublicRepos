<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/baseline-security-mode/enforce-device-compliance-intune-portal-access?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2026-11-17 -->

# Require device compliance for Intune portal access

Requiring device compliance for accessing the Intune admin portal ensures that only trusted, properly managed devices can interact with sensitive administrative controls. Allowing noncompliant or unmanaged devices to reach the Intune portal increases the risk of unauthorized actions, especially if credentials are compromised. Attackers could use an untrusted device to change policies, elevate privileges, or perform remote actions without detection. Enforcing this setting strengthens access security by ensuring that admin operations originate only from devices that meet your organization's security requirements, such as encryption, OS health, threat protection, and configuration baselines.

For more information, see [Enforce device compliance for admin console access](https://learn.microsoft.com/en-us/intune/intune-service/protect/device-compliance-get-started#compliance-policy-settings).

You need to be a member of the [Global administrator role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference) and [Intune administrator role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#intune-administrator) to be able to configure this setting.

## Why this setting matters

The Intune admin portal provides direct access to high impact device and security controls. If administrators can sign in from devices that haven't been evaluated for compliance, organizations lose a critical layer of assurance about the security of the access path itself.

This setting helps mitigate those risks by:

- **Blocking admin access from untrusted devices**  
  Devices that are unmanaged, outdated, or misconfigured are more susceptible to malware and credential theft. Enforcing compliance ensures these devices can't be used to manage Intune.
- **Reducing the impact of credential compromise**  
  Even if an attacker obtains valid admin credentials, they can't access the Intune portal unless they're using a compliant device.
- **Strengthening Zero Trust access controls**  
  This setting enforces both *who* can sign in and *from what device*, aligning Intune admin access with Zero Trust principles.
- **Aligning with Microsoft's recommended security baseline**  
  This control is marked **Recommended** and **At risk** because allowing portal access from noncompliant devices significantly increases the likelihood of unauthorized administrative changes.

## How this setting works

When this setting is enabled:

- **Admins must use compliant devices** to access the Intune admin portal.
- **Devices without a compliance policy, or that fail compliance checks, are blocked** from admin console access.
- **Admins can review devices without compliance policies** directly in the admin center to understand enforcement impact.
- **A detailed CSV report is available for download**, listing devices that would be blocked by this requirement.
- **Access is automatically restored** once the device meets compliance requirements.

This approach ensures that Intune administration is performed only from secure, evaluated devices, reducing the risk of attacker controlled or unmanaged endpoints influencing your environment.
