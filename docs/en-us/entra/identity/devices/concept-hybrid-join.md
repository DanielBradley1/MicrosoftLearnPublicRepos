<!-- Source: https://learn.microsoft.com/en-us/entra/identity/devices/concept-hybrid-join -->
<!-- Sitemap-Last-Modified: 2026-10-06 -->

# Microsoft Entra hybrid joined devices

Organizations with existing Active Directory implementations can benefit from some of the functionality provided by Microsoft Entra ID by implementing Microsoft Entra hybrid joined devices. These devices are joined to your on-premises Active Directory and registered with Microsoft Entra ID.

Microsoft Entra hybrid joined devices require network line of sight to your on-premises domain controllers periodically. Without this connection, devices become unusable. If this requirement is a concern, consider [Microsoft Entra joining](https://learn.microsoft.com/en-us/entra/identity/devices/concept-directory-join) your devices.

| Microsoft Entra hybrid join | Description |
| --- | --- |
| **Definition** | Joined to on-premises Microsoft Windows Server Active Directory and Microsoft Entra ID requiring organizational account to sign in to the device |
| **Primary audience** | Suitable for hybrid organizations with existing on-premises Microsoft Windows Server Active Directory infrastructure |
|  | Applicable to all users in an organization |
| **Device ownership** | Organization |
| **Operating Systems** | Windows 11 or Windows 10 except Home editions |
|  | Windows Server 2016, 2019, and 2022 |
| **Provisioning** | Windows 11, Windows 10, Windows Server 2016/2019/2022 |
|  | Domain join by IT and autojoin via Microsoft Entra Connect or AD FS config |
|  | Domain join by Windows Autopilot and autojoin via Microsoft Entra Connect or AD FS config |
| **Device sign in options** | Organizational accounts using: |
|  | Password |
|  | [Passwordless](https://learn.microsoft.com/en-us/entra/identity/authentication/concept-authentication-passkeys-fido2) options like [Windows Hello for Business](https://learn.microsoft.com/en-us/windows/security/identity-protection/hello-for-business/hello-planning-guide) and FIDO2.0 security keys. |
| **Device management** | [Group Policy](https://learn.microsoft.com/en-us/mem/configmgr/comanage/faq#my-environment-has-too-many-group-policy-objects-and-legacy-authenticated-apps--do-i-have-to-use-hybrid-azure-ad-) |
|  | [Configuration Manager standalone or co-management with Microsoft Intune](https://learn.microsoft.com/en-us/mem/configmgr/comanage/overview) |
| **Key capabilities** | single sign-on \(SSO\) to both cloud and on-premises resources |
|  | Conditional Access through Domain join or through Intune if co-managed |
|  | [Self-service Password Reset and Windows Hello PIN reset on lock screen](https://learn.microsoft.com/en-us/entra/identity/authentication/howto-sspr-windows) |

When enabled, Microsoft Entra Cloud Sync can synchronize Active Directory computer objects to Microsoft Entra ID for Microsoft Entra hybrid join. It doesn't configure AD FS or other federation settings. For configuration steps, see [Configure device sync with Microsoft Entra Cloud Sync](https://learn.microsoft.com/en-us/entra/identity/hybrid/cloud-sync/device-sync).

![Diagram showing Active Directory Domain Services sending device information to Microsoft Entra ID for hybrid join.](https://learn.microsoft.com/en-us/entra/identity/devices/media/concept-hybrid-join/azure-ad-hybrid-joined-device.png)

## Scenarios

Use Microsoft Entra hybrid joined devices if:

- You want to continue to use [Group Policy](https://learn.microsoft.com/en-us/mem/configmgr/comanage/faq#my-environment-has-too-many-group-policy-objects-and-legacy-authenticated-apps--do-i-have-to-use-hybrid-azure-ad-) to manage device configuration.
- You want to continue to use existing imaging solutions to deploy and configure devices.
- You have Win32 apps deployed to these devices that rely on Active Directory machine authentication.

## Related content

- [Plan your Microsoft Entra hybrid join implementation](https://learn.microsoft.com/en-us/entra/identity/devices/hybrid-join-plan)
- [Co-management using Configuration Manager and Microsoft Intune](https://learn.microsoft.com/en-us/mem/configmgr/comanage/overview)
- [Manage device identities](https://learn.microsoft.com/en-us/entra/identity/devices/manage-device-identities)
- [Manage stale devices in Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/identity/devices/manage-stale-devices)
