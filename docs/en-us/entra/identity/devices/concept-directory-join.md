<!-- Source: https://learn.microsoft.com/en-us/entra/identity/devices/concept-directory-join -->
<!-- Sitemap-Last-Modified: 2026-04-28 -->

# Microsoft Entra joined devices

Any organization can deploy Microsoft Entra joined devices no matter the size or industry. Microsoft Entra join works even in hybrid environments, enabling access to both cloud and on-premises apps and resources.

| Microsoft Entra join | Description |
| --- | --- |
| **Definition** | - Joined only to Microsoft Entra ID requiring organizational account to sign in to the device |
| **Primary audience** | - Suitable for both cloud-only and hybrid organizations.<br>- Applicable to all users in an organization |
| **Device ownership** | - Organization |
| **Operating Systems** | - All Windows 11 and Windows 10 devices except Home editions<br>- [Windows Enterprise multi-session Virtual Machines running in Azure](https://learn.microsoft.com/en-us/azure/virtual-desktop/windows-multisession-faq#can-windows-enterprise-multi-session-be-microsoft-entra-joined)<br>- [Windows Server 2019 and newer Virtual Machines running in Azure](https://learn.microsoft.com/en-us/entra/identity/devices/howto-vm-sign-in-azure-ad-windows) \(Server core isn't supported\)<br>- Apple devices running macOS 13 or newer<br>- Linux editions:<br><br>  - Ubuntu 22.04/24.04/26.04 LTS<br>  - Red Hat Enterprise Linux 9/10 LTS |
| **Provisioning** | - Self-service: Windows Out of Box Experience \(OOBE\) or Settings<br>- Bulk enrollment<br>- Windows Autopilot<br>- \(Public preview\) Apple Automated Device Enrollment \(applies to Apple devices only\) |
| **Device management** | - Mobile Device Management \(example: Microsoft Intune\)<br>- [Configuration Manager standalone or co-management with Microsoft Intune](https://learn.microsoft.com/en-us/mem/configmgr/comanage/overview) |
| **Key capabilities** | - single sign-on \(SSO\) to both cloud and on-premises resources<br>- Conditional Access<br>- [Self-service Password Reset and Windows Hello PIN reset on lock screen](https://learn.microsoft.com/en-us/entra/identity/authentication/howto-sspr-windows) |
|  |  |

## **Device sign in options**

The following are the supported sign-in options for Microsoft Entra joined devices. The availability of these options depends on the device's operating system and configuration. For example, Windows Hello for Business requires additional setup and may not be available on all devices.

| Platform | Password | SmartCard | Microsoft Authenticator  <br>phone sign-in | [Windows Hello for Business](https://learn.microsoft.com/en-us/windows/security/identity-protection/hello-for-business/hello-planning-guide) /  <br>[Platform Credentials](https://learn.microsoft.com/en-us/entra/identity/devices/macos-psso) | Web Sign-In | FIDO2 |
| --- | --- | --- | --- | --- | --- | --- |
| Windows 10/11 | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ |
| macOS 13+ | ✅ | ✅ |  | ✅ |  |  |
| Ubuntu 22.04/24.04/26.04 LTS | ✅ | ✅ | ✅ |  |  |  |
| RHEL 9/10 | ✅ | ⚠️ Preview | ✅ |  |  |  |

You sign in to Microsoft Entra joined devices using a Microsoft Entra account. Access to resources can be controlled based on your account and [Conditional Access policies](https://learn.microsoft.com/en-us/entra/identity/conditional-access/policy-alt-all-users-compliant-hybrid-or-mfa) applied to the device.

Administrators can secure and further control Microsoft Entra joined devices using Mobile Device Management \(MDM\) tools like Microsoft Intune or in co-management scenarios using Microsoft Configuration Manager. These tools provide a means to enforce organization-required configurations like:

- Requiring storage to be encrypted
- Password complexity
- Software installation
- Software updates

Administrators can make organization applications available to Microsoft Entra joined devices using Configuration Manager to [Manage apps from the Microsoft Store for Business and Education](https://learn.microsoft.com/en-us/mem/configmgr/apps/deploy-use/manage-apps-from-the-windows-store-for-business).

Microsoft Entra join can be accomplished using self-service options like the Out of Box Experience \(OOBE\), bulk enrollment, [Apple Automated Device Enrollment \(public preview\)](https://learn.microsoft.com/en-us/mem/intune/enrollment/device-enrollment-program-enroll-macos), or [Windows Autopilot](https://learn.microsoft.com/en-us/autopilot/enrollment-autopilot).

Microsoft Entra joined devices can still maintain single sign-on access to on-premises resources when they are on the organization's network. Devices that are Microsoft Entra joined can still authenticate to on-premises servers like file, print, and other applications.

## Scenarios

Microsoft Entra join can be used in various scenarios like:

- You want to transition to cloud-based infrastructure using Microsoft Entra ID and MDM like Intune.
- You can't use an on-premises domain join, for example, if you need to get mobile devices such as tablets and phones under control.
- Your users primarily need to access Microsoft 365 or other software as a service \(SaaS\) apps integrated with Microsoft Entra ID.
- You want to manage a group of users in Microsoft Entra ID instead of in Active Directory. This scenario can apply, for example, to seasonal workers, contractors, or students.
- You want to provide joining capabilities to workers who work from home or are in remote branch offices with limited on-premises infrastructure.

You can configure Microsoft Entra join for all Windows 11 and Windows 10 devices except for Home editions.

The goal of Microsoft Entra joined devices is to simplify:

- Windows and macOS deployments of work-owned devices
- Access to organizational apps and resources from any Windows or macOS device
- Cloud-based management of work-owned devices
- Users to sign in to their devices with their Microsoft Entra ID or synced Active Directory work or school accounts.

![A diagram showing Microsoft Entra joined devices interacting with an on-premises domain.](https://learn.microsoft.com/en-us/entra/identity/devices/media/concept-directory-join/azure-ad-joined-device.png)

Microsoft Entra join can be deployed by using any of the following methods:

- [Windows Autopilot](https://learn.microsoft.com/en-us/autopilot/windows-autopilot)
- [Bulk deployment](https://learn.microsoft.com/en-us/mem/intune/enrollment/windows-bulk-enroll)
- [Self-service experience](https://learn.microsoft.com/en-us/entra/identity/devices/device-join-out-of-box)
- [Apple Automated Device Enrollment \(public preview\)](https://learn.microsoft.com/en-us/mem/intune/enrollment/device-enrollment-program-enroll-macos)

## Related content

- [Plan your Microsoft Entra join implementation](https://learn.microsoft.com/en-us/entra/identity/devices/device-join-plan)
- [Co-management using Configuration Manager and Microsoft Intune](https://learn.microsoft.com/en-us/mem/configmgr/comanage/overview)
- [How to manage the local administrators group on Microsoft Entra joined devices](https://learn.microsoft.com/en-us/entra/identity/devices/assign-local-admin)
- [Manage device identities](https://learn.microsoft.com/en-us/entra/identity/devices/manage-device-identities)
- [Manage stale devices in Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/identity/devices/manage-stale-devices)
- [macOS Platform Single Sign-on \(preview\)](https://learn.microsoft.com/en-us/entra/identity/devices/macos-psso)
