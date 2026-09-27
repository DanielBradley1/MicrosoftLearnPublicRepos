<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/comanage/quickstart-paths -->
<!-- Sitemap-Last-Modified: 2023-11-16 -->

# Paths to co-management

There are two primary ways for you to set up co-management. It's important to understand the prerequisites for each path. They each require some combination of Microsoft Entra ID, Configuration Manager, Microsoft Intune, and Windows 10 or later.

1. [Auto-enroll existing Configuration Manager-managed devices into Intune](#bkmk_path1)
2. [Bootstrap the Configuration Manager client with modern provisioning](#bkmk_path2)

Tip

As we talk with our customers that are using Microsoft Intune to deploy, manage, and secure their client devices, we often get questions regarding co-managing devices and Microsoft Entra hybrid joined devices. Many customers confuse these two topics – the first is a management option, while the second is an identity option. See the blog post [Understanding hybrid Microsoft Entra ID and co-management scenarios](https://techcommunity.microsoft.com/t5/microsoft-endpoint-manager-blog/understanding-hybrid-azure-ad-join-and-co-management/ba-p/2221201). This blog aims to clarify Microsoft Entra hybrid join and co-management, how they work together but are not the same thing.

## Path 1: Auto-enroll existing clients

Taking this path can get your existing Configuration Manager-managed devices quickly enrolled into Intune. The management of these devices from Configuration Manager is no different from before you enable co-management. Now you get all the cloud-based benefits. This path is transparent to your users.

Here's what you need to set it up:

- Hybrid Microsoft Entra ID

  - One of the following [Microsoft Entra hybrid identity options](https://learn.microsoft.com/en-us/azure/active-directory/hybrid/plan-connect-user-signin):

    - [Password hash synchronization](https://learn.microsoft.com/en-us/azure/active-directory/hybrid/plan-connect-user-signin#password-hash-synchronization) with [Seamless Single Sign-on \(SSO\)](https://learn.microsoft.com/en-us/azure/active-directory/hybrid/how-to-connect-sso)
    - [Pass-through authentication](https://learn.microsoft.com/en-us/azure/active-directory/hybrid/how-to-connect-pta) with [Seamless Single Sign-on \(SSO\)](https://learn.microsoft.com/en-us/azure/active-directory/hybrid/how-to-connect-sso)
    - [Federated SSO \(with Active Directory Federation Services \(AD FS\)\)](https://learn.microsoft.com/en-us/azure/active-directory/hybrid/plan-connect-user-signin#federation-that-uses-a-new-or-existing-farm-with-ad-fs-in-windows-server-2012-r2)

  - Microsoft Entra Connect
  - Microsoft Entra ID P1 or P2 license
  - Configure Microsoft Entra hybrid join \(choose one option\):

    - For managed domains
    - For federated domains

- Client agent setting for Microsoft Entra hybrid join
- Configure auto-enrollment of devices to Intune
- Enable co-management in Configuration Manager

For a tutorial on this path, see [Tutorial: Enable co-management for existing Configuration Manager clients](https://learn.microsoft.com/en-us/intune/configmgr/comanage/tutorial-co-manage-clients).

## Path 2: Bootstrap with modern provisioning

This path is for those devices that are first enrolled with Intune. They are cloud-first devices and use Intune to install the Configuration Manager client.

Here's what you need to set it up:

1. [Setup enhanced HTTP](https://learn.microsoft.com/en-us/intune/configmgr/core/plan-design/hierarchy/enhanced-http)
2. [Create the cloud services in Azure](https://learn.microsoft.com/en-us/intune/configmgr/core/servers/deploy/configure/azure-services-wizard)
3. [Configure the management point and clients to use the cloud management gateway](https://learn.microsoft.com/en-us/intune/configmgr/core/clients/manage/cmg/setup-cloud-management-gateway)
4. [Use Intune to deploy the Configuration Manager client](https://learn.microsoft.com/en-us/intune/configmgr/comanage/how-to-prepare-win10)

For a tutorial on this path, see [Tutorial: Enable co-management for new internet-based devices](https://learn.microsoft.com/en-us/intune/configmgr/comanage/tutorial-co-manage-new-devices).
