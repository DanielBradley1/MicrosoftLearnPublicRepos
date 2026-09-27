<!-- Source: https://learn.microsoft.com/en-us/intune/device-security/identity-protection/deploy-group-policy -->
<!-- Sitemap-Last-Modified: 2026-04-15 -->

# Use identity protection profiles to manage Windows Hello for Business in Microsoft Intune

Important

In July 2024, the following Intune profiles for identity protection and account protection were deprecated and replaced by a new consolidated profile named *Account protection*. This newer profile is found in the account protection policy node of endpoint security, and is the only profile template that remains available to create new policy instances for identity and account protection. The settings from this new profile are also available through the settings catalog.

Any instances of the following older profiles that you have created remain available to use and edit:

- *Identity protection* – previously available from *Devices* > *Configuration* > *Create* > *New Policy* > *Windows 10 and later* > *Templates* > *Identity Protection*
- *Account protection \(Preview\)* – previously available from *Endpoint Security* > *Account protection* > *Windows 10 and later* > *Account protection \( Preview\)*

Microsoft Intune supports use of *Account protection* profiles to manage Windows Hello for Business on your managed Windows devices. [Windows Hello for Business](https://learn.microsoft.com/en-us/windows/security/identity-protection/hello-for-business/hello-overview) is a method for signing in to Windows devices by replacing passwords, smart cards, and virtual smart cards.

Applies to:

- Windows

When you use Intune Account protection profiles to manage Windows Hello for Business settings, you can:

- Enable Windows Hello for Business for devices and users
- Set device PIN requirements, including a minimum or maximum PIN length
- Allow gestures, such as a fingerprint, that users can \(or can't use\) to sign in to devices

In addition to Account protection profiles, Intune supports the following options to manage settings for Windows Hello for Business:

- [During device enrollment](https://learn.microsoft.com/en-us/intune/device-security/identity-protection/configure-tenant-wide-policy): Configure tenant-wide policy that applies Windows Hello settings to devices at the time the device enrolls with Intune.
- [Security baselines](https://learn.microsoft.com/en-us/intune/device-security/security-baselines/overview): Some settings for Windows Hello can be managed through Intune's security baselines, like the baselines for *Microsoft Defender for Endpoint security* or *Security Baseline for Windows 10 and later*.
- [Settings catalog](https://learn.microsoft.com/en-us/intune/device-configuration/settings-catalog/): The settings from endpoint security Account protection profiles are available in the Intune settings catalog.

Note

For customers looking to configure Windows Holographic for Business, please use [DeviceLock CSP](https://learn.microsoft.com/en-us/windows/client-management/mdm/policy-csp-devicelock)

## Next steps

- [Configure Account protection profiles to manage Windows Hello for Business settings](https://learn.microsoft.com/en-us/intune/device-configuration/endpoint-security/account-protection)
- [Review settings, and what they do](https://learn.microsoft.com/en-us/intune/device-security/identity-protection/ref-settings)
- [Monitor the profile status](https://learn.microsoft.com/en-us/intune/device-configuration/monitor-device-profile)
