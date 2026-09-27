<!-- Source: https://learn.microsoft.com/en-us/intune/device-configuration/endpoint-security/disk-encryption -->
<!-- Sitemap-Last-Modified: 2026-04-15 -->

# Disk encryption policy for endpoint security in Intune

Endpoint security Disk encryption profiles focus on only the settings that are relevant for a devices built-in encryption method, like FileVault, BitLocker, and Personal Data Encryption \(for Windows\). This focus makes it easy for security admins to manage disk encryption settings without having to navigate a host of unrelated settings.

While you can configure the same device settings by using *Endpoint Protection* profiles for device configuration, the device configuration profiles include other categories of settings. These other settings are unrelated to disk encryption and can complicate the task of configuring only disk encryption.

Find the endpoint security policies for disk encryption under *Manage* in the **Endpoint security** node of the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).

## Prerequisites for disk encryption policy

- **macOS** - macOS 10.13 or later
- **Windows** - Windows

## Role-based access controls \(RBAC\)

For guidance on assigning the right level of permissions and rights to manage Intune Disk encryption policy, see [Role-based access control for endpoint security](https://learn.microsoft.com/en-us/intune/device-configuration/endpoint-security/manage-policies#role-based-access-control-for-endpoint-security).

## Disk encryption profiles

**macOS profiles**:

- **FileVault** - FileVault provides built-in Full Disk Encryption for macOS devices.

  Manage [FileVault settings](https://learn.microsoft.com/en-us/intune/device-configuration/endpoint-security/ref-disk-encryption-settings#filevault) for macOS.

  To create a FileVault profile, see [Use FileVault disk encryption for macOS](https://learn.microsoft.com/en-us/intune/device-configuration/endpoint-security/encrypt-filevault-macos).

**Windows profiles**:

- **BitLocker** - BitLocker Drive Encryption is a data protection feature that integrates with the operating system and addresses the threats of data theft or exposure from lost, stolen, or inappropriately decommissioned computers.

  Note

  Beginning on June 19, 2023, the BitLocker profile for Windows was updated to use the settings format as found in the Settings Catalog. The new profile format includes the same settings as the older profile. With this change you can no longer create new versions of the old profiles. Your existing instances of the old profile remain available to use and edit.

  With the new profile format, we no longer publish a dedicated list of settings as found in the profile. Instead, use the *Learn more* link in the UI while viewing information for a setting, to open [BitLocker CSP](https://learn.microsoft.com/en-us/windows/client-management/mdm/bitlocker-csp) in the Windows documentation, where the setting is detailed in full.

  You can continue to find a list of settings in the original BitLocker profiles created before June 19, 2023, at [BitLocker settings](https://learn.microsoft.com/en-us/intune/device-configuration/endpoint-security/ref-disk-encryption-settings#bitlocker) in the Intune documentation.
- **Personal Data Encryption** - Personal Data Encryption \(PDE\) encrypts data at the folder level and is available for devices that run Windows 11 version 22H2 or later. PDE differs from BitLocker in that it encrypts files instead of whole volumes and disks. PDE occurs in addition to other encryption methods such as BitLocker. Unlike BitLocker that releases data encryption keys at boot, PDE doesn't release data encryption keys until a user signs in using Windows Hello for Business. PDE uses the [PDE CSP](https://learn.microsoft.com/en-us/windows/client-management/mdm/personaldataencryption-csp).

  For more information about PDE, including prerequisites, related requirements, and recommendations, see the following articles in the Windows security documentation:

  - [PDE overview](https://learn.microsoft.com/en-us/windows/security/operating-system-security/data-protection/personal-data-encryption)
  - [Configure PDE](https://learn.microsoft.com/en-us/windows/security/operating-system-security/data-protection/personal-data-encryption/configure)
  - [PDE frequently asked questions \(FAQ\)](https://learn.microsoft.com/en-us/windows/security/operating-system-security/data-protection/personal-data-encryption/faq)

To create a BitLocker or Personal Data Encryption profile, see [Use disk encryption for Windows](https://learn.microsoft.com/en-us/intune/device-configuration/endpoint-security/encrypt-bitlocker-windows).

## Manage device encryption

After you deploy policy to encrypt a device disk, see the following articles for information on managing encryption:

- [Manage encryption on Windows](https://learn.microsoft.com/en-us/intune/device-configuration/endpoint-security/encrypt-bitlocker-windows)
- [Manage encryption on macOS](https://learn.microsoft.com/en-us/intune/device-configuration/endpoint-security/encrypt-filevault-macos#monitor-and-manage-filevault)
- [Monitor device encryption](https://learn.microsoft.com/en-us/intune/device-management/monitor-encryption)

## Next steps

- [To create a macOS encryption profile](https://learn.microsoft.com/en-us/intune/device-configuration/endpoint-security/encrypt-filevault-macos#create-endpoint-security-policy)
- [To create a Windows encryption profile](https://learn.microsoft.com/en-us/intune/device-configuration/endpoint-security/encrypt-bitlocker-windows#create-endpoint-security-policy)
