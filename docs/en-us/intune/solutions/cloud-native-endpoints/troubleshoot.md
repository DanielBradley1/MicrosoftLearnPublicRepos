<!-- Source: https://learn.microsoft.com/en-us/intune/solutions/cloud-native-endpoints/troubleshoot -->
<!-- Sitemap-Last-Modified: 2026-04-20 -->

# Known issues and limitations with cloud-native endpoints

Tip

When reading about cloud native endpoints, you see the following terms:

- **Endpoint**: An endpoint is a device, like a mobile phone, tablet, laptop, or desktop computer. "Endpoints" and "devices" are used interchangeably.
- **Managed endpoints**: Endpoints that receive policies from the organization using an MDM solution or Group Policy Objects. These devices are typically organization owned, but can also be BYOD or personally owned devices.
- **Cloud native endpoints**: Endpoints that are joined to Microsoft Entra. They aren't joined to on-premises AD.
- **Workload**: Any program, service, or process.

When using or moving on-premises device management to cloud-native endpoints, there are some scenarios you need to know. This article lists and describes some changed behaviors, limitations, and resolutions.

Cloud-native endpoints are devices that are joined to Microsoft Entra. In many cases, they don't require a direct connection to any on-premises resources for usability or management. For more specific information, go to [What are cloud-native endpoints](https://learn.microsoft.com/en-us/intune/solutions/cloud-native-endpoints/overview).

This feature applies to:

- Windows cloud-native endpoints

In this article, **Computer accounts** and **machine accounts** are used interchangeably.

## Don't use machine authentication

When a Windows endpoint, like a Windows device, joins an on-premises Active Directory \(AD\) domain, a computer account is automatically created. The computer/machine account can be used to authenticate.

Machine authentication happens when:

- On-premises resources, like file shares, printers, applications, and web sites, are accessed using on-premises AD computer accounts instead of user accounts.
- Administrators or application developers configure on-premises resource access using machine accounts instead of users or user groups.

Cloud-native endpoints are joined to Microsoft Entra, and don't exist in on-premises AD. Cloud-native endpoints don't support on-premises AD machine authentication. Configuring access to on-premises file shares, applications, or services using only on-premises AD machine accounts will fail on cloud-native endpoints.

### Switch to user-based authentication

- When creating new projects, don't use machine authentication. Using machine authentication isn't common and isn't a recommended practice. But it's something you need to know and be aware. Instead, use user-based authentication.
- Review your environment and identify any applications and services that currently use machine authentication. Then, change the access to user-based authentication or service account-based authentication.

Important

The Microsoft Entra Connect device writeback feature tracks devices that are registered in Microsoft Entra. These devices are shown in on-premises AD as registered devices.

Microsoft Entra Connect device writeback doesn't create identical on-premises AD computer accounts in the on-premises AD domain. These writeback devices don't support on-premises machine authentication.

For information on scenarios supported with device writeback, go to [Microsoft Entra Connect: Enabling device writeback](https://learn.microsoft.com/en-us/entra/identity/hybrid/connect/how-to-connect-device-writeback).

### Common services that use machine accounts

The following list includes common features and services that might use machine accounts to authenticate. It also includes recommendations if your organization is using these features with machine authentication.

- **Network storage access** fails with machine accounts. Cloud-native endpoints can't access file shares secured using machine accounts. If ACL \(access control list\) permissions are assigned only to machine accounts, or assigned to groups that include only machine accounts, then drive mapping with file shares or network-attached storage \(NAS\) shares will fail.

  **Recommendation**:

  - **Server and workstation file shares**: Update permissions to use user account-based security. When you do, use [Microsoft Entra single sign-on \(SSO\)](https://learn.microsoft.com/en-us/entra/identity/devices/device-sso-to-on-premises-resources) to access resources that use Windows integrated authentication.

    Move file share content to SharePoint Online or OneDrive. For more specific information, go to [Migrate file shares to SharePoint and OneDrive](https://learn.microsoft.com/en-us/sharepointmigration/fileshare-to-odsp-migration-guide).
  - **Network File System \(NFS\) root access**: Direct users to access specific folders, not the root. If you can, move content from an NFS to SharePoint Online or OneDrive.

- **Win32 apps** on Microsoft Entra joined Windows endpoints:

  - Won't work if the apps use machine account authentication.
  - Won't work if the apps access resources that are secured with groups that include only machine accounts.


  **Recommendation**:


  - If your Win32 apps use machine authentication, then update the app to use Microsoft Entra authentication. For more information, go to [Migrate application authentication to Microsoft Entra](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/migrate-adfs-apps-phases-overview).
  - Check the authentication and identities of your applications and kiosk devices. Update the authentication and identities to use user account-based security.


  For more information, go to [Authentication and Win32 apps](https://learn.microsoft.com/en-us/windows/win32/secauthn/authentication-portal).

- **IIS web server** deployments that restrict site access using ACL permissions with only computer accounts, or groups of computer accounts, will fail. Authentication strategies that limit access to only computer accounts or groups of computer accounts will also fail.

  **Recommendation**:

  - On your web sites, enable Negotiate authentication.
  - Update your web server apps to use Microsoft Entra authentication. For more information, go to [Migrate application authentication to Microsoft Entra](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/migrate-adfs-apps-phases-overview).


  More resources:


  - [IIS Authentication `<windowsAuthentication>`](https://learn.microsoft.com/en-us/iis/configuration/system.webserver/security/authentication/windowsauthentication/)
  - [IIS Security Authorization `<authorization>`](https://learn.microsoft.com/en-us/iis/configuration/system.webserver/security/authorization/)

- Standard **print management and discovery** depends on machine authentication. On Microsoft Entra joined Windows endpoints, users can't print using standard print.

  **Recommendation**: Use Universal Print. For more specific information, go to [What is Universal Print](https://learn.microsoft.com/en-us/universal-print/fundamentals/universal-print-whatis).
- **Windows scheduled tasks** that run in the machine-context on cloud-native endpoints can't access resources on remote servers and workstations. The cloud-native endpoint doesn't have an account in on-premises AD, and therefore can't authenticate.

  **Recommendation**: Configure your scheduled tasks to use **logged in user**, or another form of account-based authentication.
- **Active Directory login scripts** are assigned in the on-premises AD user's properties or deployed using a Group Policy Object \(GPO\). These scripts aren't available for cloud-native endpoints.

  **Recommendation**: Review your scripts. If there's a modern equivalent, then use it instead. For example, if your script sets the user's home drive, then you can move a user's home drive to OneDrive instead. If your script stores shared folder content, then migrate the shared folder content to SharePoint Online instead.

  If there isn't a modern equivalent, then you can deploy Windows PowerShell scripts using Microsoft Intune.

  For more information, go to:

  - [Add PowerShell scripts to Windows devices in Microsoft Intune](https://learn.microsoft.com/en-us/intune/device-management/tools/management-extension-windows)
  - [Introduction to OneDrive in Microsoft 365](https://learn.microsoft.com/en-us/training/modules/m365-onedrive-collaboration-use/)

## Group Policy Objects might not apply

It's possible some of your older policies aren't available, or don't apply to cloud-native endpoints.

**Resolution**:

- Using [Group Policy analytics](https://learn.microsoft.com/en-us/intune/device-configuration/import-group-policy-analytics) in Intune, you can evaluate your existing Group Policy Objects \(GPO\). The analysis shows the policies that are available, and policies that aren't available.
- In endpoint management, policies are deployed to users and groups. They aren't applied in LSDOU order. This behavior is a mind shift, so make sure your users and groups are in order.

  For more specific information and guidance on policy assignment in Microsoft Intune, go to [Assign user and device profiles in Microsoft Intune](https://learn.microsoft.com/en-us/intune/device-configuration/assign-device-profile).
- Inventory your policies, and determine what they do. You may find categories or groupings, such as policies that focus on security, policies that focus on the OS, and so on.

  You can create an Intune policy that includes the settings from your categories or groupings. The [Settings Catalog](https://learn.microsoft.com/en-us/intune/device-configuration/settings-catalog/) is a good resource.
- Be prepared to create new policies. The built-in features of modern endpoint management, like Microsoft Intune, may have better options to create and deploy policies.

  The [High level planning guide to move to cloud-native endpoints](https://learn.microsoft.com/en-us/intune/solutions/cloud-native-endpoints/planning-guide#move-from-group-policy-objects-gpos) is a good resource.
- Don't migrate all your policies. Remember, your old policies might not make sense with cloud-native endpoints.

  Instead of doing what you've always done, focus on what you actually want to achieve.

## Synchronized user accounts can't complete first sign-in

Synchronized user accounts are on-premises AD domain users that are synchronized to Microsoft Entra using Microsoft Entra Connect.

Currently, synchronized user accounts with passwords that have **User must change password at next logon** configured can't complete a first-time sign-in to a cloud-native endpoint.

**Resolution**:

Use Password Hash Sync and Microsoft Entra connect, which forces the **force password change at logon** attribute to sync.

For more specific information, go to [Implement password hash synchronization with Microsoft Entra Connect sync](https://learn.microsoft.com/en-us/entra/identity/hybrid/connect/how-to-connect-password-hash-synchronization#synchronizing-temporary-passwords-and-force-password-change-on-next-logon).

## Follow the cloud-native endpoints guidance

1. [Overview: What are cloud-native endpoints?](https://learn.microsoft.com/en-us/intune/solutions/cloud-native-endpoints/overview)
2. [Tutorial: Set up cloud-native Windows endpoints with Microsoft Intune](https://learn.microsoft.com/en-us/intune/solutions/cloud-native-endpoints/tutorial-cloud-native-setup)
3. [Concept: Microsoft Entra joined vs. Hybrid Microsoft Entra joined](https://learn.microsoft.com/en-us/intune/solutions/cloud-native-endpoints/entra-join-types)
4. [Concept: Cloud-native endpoints and on-premises resources](https://learn.microsoft.com/en-us/intune/solutions/cloud-native-endpoints/on-premises-resources)
5. [High level planning guide](https://learn.microsoft.com/en-us/intune/solutions/cloud-native-endpoints/planning-guide)
6. 🡺 **Known issues and important information** \(*You are here*\)
