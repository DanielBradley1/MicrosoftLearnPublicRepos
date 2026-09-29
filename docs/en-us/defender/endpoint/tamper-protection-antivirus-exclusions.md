<!-- Source: https://learn.microsoft.com/en-us/defender-endpoint/tamper-protection-antivirus-exclusions -->
<!-- Sitemap-Last-Modified: 2026-09-08 -->

# Protect Microsoft Defender Antivirus exclusions with tamper protection

On Windows devices, tamper protection can prevent unauthorized changes to organization-managed [Microsoft Defender Antivirus exclusions](https://learn.microsoft.com/en-us/defender-endpoint/microsoft-defender-antivirus-exclusions-configure). Review the requirements for protecting exclusions, and use Registry Editor to verify that protection is active. For an overview of how tamper protection exclusions differ between Windows and macOS, see [Tamper protection exclusions](https://learn.microsoft.com/en-us/defender-endpoint/tamper-protection-overview#tamper-protection-exclusions).

## Requirements for protecting antivirus exclusions

Meet the following requirements:

- **Microsoft Defender platform**: Devices run platform version `4.18.2211.5` \(November 2022\) or later. See [Monthly platform and engine versions](https://learn.microsoft.com/en-us/defender-endpoint/microsoft-defender-antivirus-updates#platform-and-engine-releases).
- **`DisableLocalAdminMerge` setting**: Enable `DisableLocalAdminMerge` to prevent locally configured settings from merging with organization policies. See [DisableLocalAdminMerge](https://learn.microsoft.com/en-us/windows/client-management/mdm/defender-csp#configurationdisablelocaladminmerge).
- **Device management**: Devices are managed only by Intune or only by Configuration Manager, and the Microsoft Defender for Endpoint sensor \(Sense\) is enabled.
- **Antivirus exclusions**: Exclusions are managed in Intune or Configuration Manager. See [Microsoft Defender Antivirus policy settings for Windows devices](https://learn.microsoft.com/en-us/intune/intune-service/protect/antivirus-microsoft-defender-settings-windows). The exclusion protection feature is enabled on devices. See [Verify that antivirus exclusions are tamper protected](#how-to-determine-whether-antivirus-exclusions-are-tamper-protected-on-a-windows-device).

Note

If Configuration Manager is the only tool that manages exclusions and all requirements are met, the exclusions are tamper protected. You don't also need to deploy exclusions through Intune.

You don't need to disable tamper protection to apply new exclusion policy settings from Intune or Configuration Manager.

For more information about antivirus exclusions, see [Microsoft Defender for Endpoint and Microsoft Defender Antivirus exclusions](https://learn.microsoft.com/en-us/defender-endpoint/defender-endpoint-exclusions-overview).

## Verify that antivirus exclusions are tamper protected

Use Registry Editor to verify whether Microsoft Defender Antivirus exclusions are tamper protected.

Caution

Don't change the registry values. Use this procedure to view the values only.

1. Open Registry Editor on a Windows device.
2. To verify that only Intune or only Configuration Manager manages the device and that the Defender for Endpoint sensor is enabled, check the following registry values:

   - `ManagedDefenderProductType` in `Computer\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows Defender` or `HKLM\SOFTWARE\Microsoft\Windows Defender`.
   - `EnrollmentStatus` in `Computer\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SenseCM` or `HKLM\SOFTWARE\Microsoft\SenseCM`.


   Use the following table to interpret the values:

   | ManagedDefenderProductType | EnrollmentStatus | Description |
   | --- | --- | --- |
   | `6` | Any value | The device is managed only with Intune and meets the device-management requirement. |
   | `7` | `4` | The device is managed with Configuration Manager and meets the device-management requirement. |
   | `7` | `3` | The device is co-managed with Configuration Manager and Intune. This configuration isn't supported for tamper-protected exclusions. |
   | A value other than `6` or `7` | Any value | The device isn't managed only with Intune or only with Configuration Manager. Exclusions aren't tamper protected. |
3. To confirm that tamper protection is deployed and exclusions are tamper protected, check the `TPExclusions` value in `Computer\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows Defender\Features` or `HKLM\SOFTWARE\Microsoft\Windows Defender\Features`.

   Use the following table to interpret the value:

   | TPExclusions | Description |
   | --- | --- |
   | `1` | The requirements are met, and exclusions are tamper protected. |
   | `0` | Tamper protection isn't protecting exclusions. If all requirements are met and this state seems incorrect, contact support. |

## Related content

- [Configure tamper protection on Windows devices](https://learn.microsoft.com/en-us/defender-endpoint/tamper-protection-windows-configure)
- [Tamper protection overview](https://learn.microsoft.com/en-us/defender-endpoint/tamper-protection-overview)
- [Frequently asked questions on tamper protection](https://learn.microsoft.com/en-us/defender-endpoint/tamper-protection-faq)
- [Troubleshoot problems with tamper protection](https://learn.microsoft.com/en-us/defender-endpoint/tamper-protection-troubleshoot)
