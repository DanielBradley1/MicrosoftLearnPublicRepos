<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/core/clients/deploy/prerequisites-for-deploying-clients-to-mobile-devices -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# Prerequisites for deploying clients to mobile devices in Configuration Manager

*Applies to: Configuration Manager \(current branch\)*

Important

On-premises MDM and the Configuration Manager client for macOS are both [deprecated](https://learn.microsoft.com/en-us/intune/configmgr/core/plan-design/changes/deprecated/removed-and-deprecated-cmfeatures).

Migrate management of macOS and mobile devices to Microsoft Intune. For more information, see [Supported clients and devices](https://learn.microsoft.com/en-us/intune/configmgr/core/plan-design/configs/supported-operating-systems-for-clients-and-devices#mac-computers).

Deploying Configuration Manager clients in your environment has the following external dependencies and dependencies within the product.

For more information on the minimum hardware and OS requirements for the Configuration Manager client, see [Supported configurations](https://learn.microsoft.com/en-us/intune/configmgr/core/plan-design/configs/supported-configurations).

Note

The software version numbers shown in this article only list the minimum version numbers required.

When you install the Configuration Manager client on mobile devices and enroll them, use this information to determine the prerequisites.

## Dependencies external to Configuration Manager

- A Microsoft enterprise certification authority \(CA\) with certificate templates to deploy and manage the certificates required for mobile devices.

  The issuing CA must automatically approve certificate requests from the mobile device users during the enrollment process.

  For more information about the certificate requirements, see [Security and privacy for certificate profiles](https://learn.microsoft.com/en-us/intune/configmgr/protect/plan-design/security-and-privacy-for-certificate-profiles).
- A security group that contains the users that can enroll their mobile devices.

  This security group is used to configure the certificate template that is used during mobile device enrollment.
- Optional but recommended: a DNS alias \(CNAME record\) named **ConfigMgrEnroll**. Configure this alias for the server name of the enrollment proxy point.

  This DNS alias is required to support automatic discovery for the enrollment service. If you don't configure this DNS record, users must manually specify the name of the enrollment proxy point as part of the enrollment process.
- Site system role dependencies for the computers that run the enrollment point and the enrollment proxy point.

  For more information, see [Supported operating systems for site system servers](https://learn.microsoft.com/en-us/intune/configmgr/core/plan-design/configs/supported-operating-systems-for-site-system-servers).

## Configuration Manager dependencies

For more information, see [Determine the site system roles for clients](https://learn.microsoft.com/en-us/intune/configmgr/core/clients/deploy/plan/determine-the-site-system-roles-for-clients).

- Management point configurations:

  - HTTPS client connections
  - Enabled for mobile devices
  - An internet FQDN
  - Accept client connections from the internet

- Enrollment point and enrollment proxy point

  An enrollment proxy point manages enrollment requests from mobile devices and the enrollment point completes the enrollment process. The enrollment point must be in the same Active Directory forest as the site server, but the enrollment proxy point can be in another forest.
- Client settings for mobile device enrollment

  Configure client settings to allow users to enroll mobile devices and configure at least one enrollment profile.
- Reporting services point

  The reporting services point is an optional, but recommended site system role. It can display reports related to mobile device enrollment and client management. For more information, see [Introduction to reporting](https://learn.microsoft.com/en-us/intune/configmgr/core/servers/manage/introduction-to-reporting).
- To configure enrollment for mobile devices, your account needs the following security permissions:

  - To add, modify, and delete the enrollment site system roles: **Modify** permission for the **Site** object.
  - To configure client settings for enrollment: Default client settings require **Modify** permission for the **Site** object, and custom client settings require **Client agent** permissions.


  The **Full Administrator** default security role includes the required permissions to configure the enrollment site system roles.

- To manage enrolled mobile devices, your account needs the following security permissions:

  - To wipe or retire a mobile device: **Delete resource** for the **Collection** object.
  - To cancel a wipe or retire command: **Delete resource** for the **Collection** object.
  - To allow and block mobile devices: **Modify resource** for the **Collection** object.
  - To remote lock, or reset the passcode on a mobile device: **Modify** resource for the **Collection** object.


  The **Operations Administrator** default security role includes the required permissions to manage mobile devices.

For more information about how to configure security permissions, see [Fundamentals of role-based administration](https://learn.microsoft.com/en-us/intune/configmgr/core/understand/fundamentals-of-role-based-administration) and [Configure role-based administration](https://learn.microsoft.com/en-us/intune/configmgr/core/servers/deploy/configure/configure-role-based-administration).

## Firewall requirements

Intervening network devices such as routers and firewalls, and Windows Firewall if applicable, must allow the traffic associated with mobile device enrollment.

- Between mobile devices and the enrollment proxy point: HTTPS \(by default, TCP 443\)
- Between the enrollment proxy point and the enrollment point: HTTPS \(by default, TCP 443\)

If you use a proxy web server, configure it for SSL tunneling. SSL bridging isn't supported for mobile devices.

## Next steps

[Windows firewall and port settings for clients](https://learn.microsoft.com/en-us/intune/configmgr/core/clients/deploy/windows-firewall-and-port-settings-for-clients)
