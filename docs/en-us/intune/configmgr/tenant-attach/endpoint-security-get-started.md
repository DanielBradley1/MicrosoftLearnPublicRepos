<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/tenant-attach/endpoint-security-get-started -->
<!-- Sitemap-Last-Modified: 2023-02-22 -->

# Get started: Create and deploy endpoint security policies from the admin center

*Applies to: Configuration Manager \(current branch\)*

The Microsoft Intune family of products is an integrated solution for managing all of your devices. Microsoft brings together Configuration Manager and Intune into a single console called **Microsoft Intune admin center**.

## Prerequisites

- Access to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
- An environment that's [tenant attached with uploaded devices](https://learn.microsoft.com/en-us/intune/configmgr/tenant-attach/device-sync-actions).
- A supported version of Configuration Manager and the corresponding version of the console installed.

  - Upgrade the target devices to the latest version of the Configuration Manager client.

- At least one Configuration Manager collection that's [available for assigning Endpoint security policies](https://learn.microsoft.com/en-us/intune/configmgr/tenant-attach/endpoint-security-get-started#bkmk_collections)
- Windows Devices that [support this profile for tenant attached devices](https://learn.microsoft.com/en-us/intune/configmgr/tenant-attach/endpoint-security-get-started#bkmk_supportedprofiles)

## Supported endpoint security profiles for tenant attached devices

| Platform | Endpoint security policy | Profile | Endpoint Protection \(Configuration Manager\) | Endpoint Security \(Tenant Attach\) |
| --- | --- | --- | --- | --- |
| Windows 10, Windows 11, and Windows Server | Antivirus | Antivirus | ![Supported](https://learn.microsoft.com/en-us/intune/configmgr/tenant-attach/media/green-check.png) | ![Supported](https://learn.microsoft.com/en-us/intune/configmgr/tenant-attach/media/green-check.png) |
| Windows 10, Windows 11, and Windows Server | Antivirus | Antivirus Exclusions | ![Supported](https://learn.microsoft.com/en-us/intune/configmgr/tenant-attach/media/green-check.png) | ![Supported](https://learn.microsoft.com/en-us/intune/configmgr/tenant-attach/media/green-check.png) |
| Windows 10, Windows 11, and Windows Server | Antivirus | Tamper Protection | ![Not Supported](https://learn.microsoft.com/en-us/intune/configmgr/tenant-attach/media/red-wrong.png) | ![Supported](https://learn.microsoft.com/en-us/intune/configmgr/tenant-attach/media/green-check.png) |
| Windows 10, Windows 11, and Windows Server | Attack Surface Reduction | Attack Surface Reduction Rules | ![Supported](https://learn.microsoft.com/en-us/intune/configmgr/tenant-attach/media/green-check.png) | ![Supported](https://learn.microsoft.com/en-us/intune/configmgr/tenant-attach/media/green-check.png) |
| Windows 10, Windows 11 | Attack Surface Reduction | Application Guard Settings | ![Supported](https://learn.microsoft.com/en-us/intune/configmgr/tenant-attach/media/green-check.png) | ![Supported](https://learn.microsoft.com/en-us/intune/configmgr/tenant-attach/media/green-check.png) |
| Windows 10, Windows 11, and Windows Server | Attack Surface Reduction | Exploit protection | ![Supported](https://learn.microsoft.com/en-us/intune/configmgr/tenant-attach/media/green-check.png) | ![Supported](https://learn.microsoft.com/en-us/intune/configmgr/tenant-attach/media/green-check.png) |
| Windows 10, Windows 11, and Windows Server | Endpoint detection and response | Endpoint detection and response | ![Supported](https://learn.microsoft.com/en-us/intune/configmgr/tenant-attach/media/green-check.png) | ![Supported](https://learn.microsoft.com/en-us/intune/configmgr/tenant-attach/media/green-check.png) |
| Windows 10, Windows 11, and Windows Server | Firewall | Firewall | ![Supported](https://learn.microsoft.com/en-us/intune/configmgr/tenant-attach/media/green-check.png) | ![Supported](https://learn.microsoft.com/en-us/intune/configmgr/tenant-attach/media/green-check.png) |
| Windows 10, Windows 11, and Windows Server | Firewall | Firewall Rules | ![Not Supported](https://learn.microsoft.com/en-us/intune/configmgr/tenant-attach/media/red-wrong.png) | ![Supported](https://learn.microsoft.com/en-us/intune/configmgr/tenant-attach/media/green-check.png) |

The following profiles are supported for devices you manage with Configuration Manager current branch, through the tenant attach scenario:

- Platform: **Windows 10, Windows 11, and Windows Server \(ConfigMgr\)**

  - Profile: **Microsoft Defender Antivirus** - Manage [Antivirus policy settings for Configuration Manager devices](https://learn.microsoft.com/en-us/intune/device-configuration/endpoint-security/ref-antivirus-defender-settings-windows-tenant-attach?toc=/mem/configmgr/tenant-attach/toc.json&bc=/mem/configmgr/tenant-attach/breadcrumb/toc.json), when you use tenant attach.

    This profile is supported with devices that are tenant attached and run the following platforms:

    - Windows 10 and later \(x86, x64, ARM64\)
    - Windows Server 2019 and later \(x64\)
    - Windows Server 2016 \(x64\)
    - Windows 8.1 \(x86, x64\)
    - Windows Server 2012 R2 \(x64\)

  - Profile: **Windows Security experience \(ConfigMgr\)** - Manage [Windows Security app settings for Configuration Manager devices](https://learn.microsoft.com/en-us/intune/device-configuration/endpoint-security/ref-windows-security-settings-tenant-attach?toc=/mem/configmgr/tenant-attach/toc.json&bc=/mem/configmgr/tenant-attach/breadcrumb/toc.json), when you use tenant attach.

    This profile is supported with devices that are tenant attached and run the following platforms:

    - Windows 10 and later \(x86, x64, ARM64\)
    - Windows Server 2019 and later \(x64\)


  Important


  To support managing tamper protection your environment must additionally meet the [prerequisites for managing tamper protection with Intune](https://learn.microsoft.com/en-us/windows/security/threat-protection/microsoft-defender-antivirus/prevent-changes-to-security-settings-with-tamper-protection#turn-tamper-protection-on-or-off-for-your-organization-using-intune) as detailed in the Windows documentation.


  - Profile: **Endpoint detection and response \(ConfigMgr\)** - Manage [Endpoint detection and response policy settings](https://learn.microsoft.com/en-us/intune/device-configuration/endpoint-security/ref-edr-settings?toc=/mem/configmgr/tenant-attach/toc.json&bc=/mem/configmgr/tenant-attach/breadcrumb/toc.json), when you use tenant attach.

    This profile is supported with devices that are tenant attached and run the following platforms:

    - Windows 10 and later \(x86, x64, ARM64\)
    - Windows 8.1 \(x84, x64\)
    - Windows Server 2019 and later \(x64\)
    - Windows Server 2016 \(x64\)
    - Windows Server 2012 R2 \(x64\)
    - Profile: **Attack Surface Reduction Rules \(ConfigMgr\)** - Manage Attack Surface Reduction Rules for Configuration Manager devices as part of Attack surface reduction policy, when you use tenant attach.


    This profile is supported with devices that are tenant attached and run the following platforms:


    - Windows 10 and later \(x86, x64, ARM64\)
    - Windows Server 2019 and later \(x64\)
    - Windows Server 2016 \(x64\)
    - Windows Server 2012 R2 \(x64\)


    Note


    Attack Surface Reduction rules may not be available on Windows Server 2012 R2 and Windows Server 2016. For more information please refer to [Attack Surface Reduction rules documentation](https://learn.microsoft.com/en-us/microsoft-365/security/defender-endpoint/attack-surface-reduction-rules-reference#supported-operating-systems).

- Platform: **Windows 10 and later**

  - Profile: **Microsoft Defender Firewall \(ConfigMgr\)** - Manage [firewall policy settings for Configuration Manager devices](https://learn.microsoft.com/en-us/intune/device-configuration/endpoint-security/ref-firewall-settings-tenant-attach?toc=/mem/configmgr/tenant-attach/toc.json&bc=/mem/configmgr/tenant-attach/breadcrumb/toc.json), when you use tenant attach.

    This profile is supported with devices that are tenant attached and run the following platforms:

    - Windows 10 and later \(x86, x64, ARM64\)


    Important


    A supported version of Configuration manager is required to support firewall policies.

  - Profile: **Exploit Protection \(ConfigMgr\)** - Manage [Exploit Protection settings for Configuration Manager devices](https://learn.microsoft.com/en-us/intune/device-configuration/endpoint-security/ref-attack-surface-reduction-settings?toc=/mem/configmgr/tenant-attach/toc.json&bc=/mem/configmgr/tenant-attach/breadcrumb/toc.json#attack-surface-reduction-configmgr) as part of Attack surface reduction policy, when you use tenant attach.

    This profile is supported with devices that are tenant attached and run the following platforms:

    - Windows 10 and later \(x86, x64, ARM64\)

  - Profile: **Web Protection \(ConfigMgr\)** - Manage [Web Protection settings for Configuration Manager devices](https://learn.microsoft.com/en-us/intune/device-configuration/endpoint-security/ref-attack-surface-reduction-settings?toc=/mem/configmgr/tenant-attach/toc.json&bc=/mem/configmgr/tenant-attach/breadcrumb/toc.json#attack-surface-reduction-configmgr) as part of Attack surface reduction policy, when you use tenant attach.

    This profile is supported with devices that are tenant attached and run the following platforms:

    - Windows 10 and later \(x86, x64, ARM64\)

## Make Configuration Manager collections available to assign Endpoint security policies

When you enable collections of devices to work with endpoint security policies from Intune, you're configuring devices in those collections to onboard with Microsoft Defender for Endpoint.

1. From a Configuration Manager console connected to your top-level site, right-click on a device collection that you synchronize to Microsoft Intune admin center and select **Properties**.
2. On the **Cloud Sync** tab, enable the option to **Make this collection available to assign Endpoint security policies from Microsoft Intune admin center**.

   - You can't select this option if your Configuration Manager hierarchy isn't tenant attached.
   - The collections available for this option are limited by the [collection scope selected for tenant attach upload](https://learn.microsoft.com/en-us/intune/configmgr/tenant-attach/device-sync-actions#bkmk_edit).


   ![Configure cloud sync](https://learn.microsoft.com/en-us/intune/fundamentals/media/tenant-attach/cloud-sync.png)

3. Select **Add** and then select the Microsoft Entra group that you would like to synchronize with **Collect membership results**.
4. Select **OK** to save the configuration.

   Devices in this collection can now onboard with Microsoft Defender for Endpoint, and support use of Intune endpoint security policies.

## Next steps

- [Create and deploy endpoint security Antivirus policy to tenant attached devices](https://learn.microsoft.com/en-us/intune/configmgr/tenant-attach/deploy-antivirus-policy)
- [Create and deploy endpoint security Firewall policy to tenant attached devices](https://learn.microsoft.com/en-us/intune/configmgr/tenant-attach/deploy-firewall-policy)
- [Create and deploy endpoint security Endpoint Detection and Response policy to tenant attached devices](https://learn.microsoft.com/en-us/intune/configmgr/tenant-attach/atp-onboard)
