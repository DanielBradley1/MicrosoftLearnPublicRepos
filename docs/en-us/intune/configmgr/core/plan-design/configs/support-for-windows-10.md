<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/core/plan-design/configs/support-for-windows-10 -->
<!-- Sitemap-Last-Modified: 2026-05-14 -->

# Support for Windows 10 in Configuration Manager

*Applies to: Configuration Manager \(current branch\)*

Learn about the Windows 10 versions that Configuration Manager supports as a client. For more information about support for later versions of Windows, see [Support for Windows 11](https://learn.microsoft.com/en-us/intune/configmgr/core/plan-design/configs/support-for-windows-11).

For more information about support for the Windows Assessment and Deployment Kit \(ADK\) for Windows 10, see [Support for the Windows ADK](https://learn.microsoft.com/en-us/intune/configmgr/core/plan-design/configs/support-for-windows-adk).

Tip

Windows Server builds as a client are supported the same as the associated Windows 10 version. For example, Windows Server 2016 is the same build version as Windows 10 LTSB 2016, and Windows Server version 1803 is the same build version as Windows 10, version 1803.

For more information on Windows Server as a site system, see [Supported operating systems for Configuration Manager site system servers](https://learn.microsoft.com/en-us/intune/configmgr/core/plan-design/configs/supported-operating-systems-for-site-system-servers).

## Windows 10 versions

Configuration Manager attempts to provide support as a client for each new Windows 10 version as soon as possible after it becomes available. Because the products have separate development and release schedules, the support that Configuration Manager provides depends on when each becomes available.

A Configuration Manager version drops from the matrix after [support for that version](https://learn.microsoft.com/en-us/intune/configmgr/core/servers/manage/current-branch-versions-supported) ends. Similarly, support for Windows 10 versions like the Enterprise 2015 LTSB or 1511 drops from the matrix when they're removed from support.

- The latest version of Configuration Manager current branch receives both security and critical updates, which can include fixes for issues with Windows 10 versions. When Microsoft releases a new version of Configuration Manager current branch, prior versions only receive security updates. For more information, see [Support for Configuration Manager current branch versions](https://learn.microsoft.com/en-us/intune/configmgr/core/servers/manage/current-branch-versions-supported).

  Note

  The best way to stay current with Windows 10 is to stay current with Configuration Manager. For more information, see [Configuration Manager and Windows as a Service](https://learn.microsoft.com/en-us/intune/configmgr/core/understand/configuration-manager-and-windows-as-service).
- This information supplements [Supported operating systems for clients and devices](https://learn.microsoft.com/en-us/intune/configmgr/core/plan-design/configs/supported-operating-systems-for-clients-and-devices).
- If you use the long-term servicing branch of Configuration Manager, see [Supported configurations for the long-term servicing branch](https://learn.microsoft.com/en-us/intune/configmgr/core/understand/supported-configurations-for-ltsb).

The following table lists the versions of Windows 10 that you can use as a client with different versions of Configuration Manager.

| Windows 10 version | ConfigMgr 2503 | ConfigMgr 2509 | ConfigMgr 2603 |
| --- | --- | --- | --- |
| **22H2**  <br>\(10.0.19045\) <sup>[Extended Security Updates](https://learn.microsoft.com/en-us/intune/configmgr/core/plan-design/configs/supported-operating-systems-for-clients-and-devices#bkmk_ESU)</sup> | ✅ | ✅ | ✅ |

All currently supported versions of Configuration Manager current branch support the following Windows 10 LTSB/LTSC editions:

- **Enterprise 2016 LTSB**
- **Enterprise LTSC 2019**
- **Enterprise LTSC 2021**

For more information on Windows lifecycle, see the [Windows lifecycle fact sheet](https://learn.microsoft.com/en-us/lifecycle/faq/windows) and [Windows 10 release information](https://learn.microsoft.com/en-us/windows/release-health/release-information).

| Key |
| --- |
| ✅ = **Supported** |
| ❌ = **Not supported** |

## Support notes

- Support for Windows 10 semi-annual channel versions includes the following editions: Enterprise, Pro, Education, Pro Education, and Pro for Workstation.
- OS deployment media shows the build number from the base version. For example, `10.0.19041`. When Windows is installed, it applies an enablement package, which updates the build number to what's in the preceding table. You can use the revision ID to distinguish the media:
  | Media version | Windows version |
  | --- | --- |
  | `10.0.19045.2130` | Windows 10, version 22H2 |
  | `10.0.19041.1288` | Windows 10, version 21H2 |

## Windows 10 on ARM64

Configuration Manager supports the client on Windows 10 ARM64 devices.

The **All Windows 10 \(ARM64\)** platform is available in the list of supported OS versions on objects with requirement rules or applicability lists.

Note

If you previously selected the top-level **Windows 10** platform, this action automatically selected both **All Windows 10 \(64-bit\)** and **All Windows 10 \(32-bit\)**. If you want to add **All Windows 10 \(ARM64\)**, manually select it in the list.

Starting in version 2403 OS deployment is supported for **Windows 10 22H2 \(ARM64\)**, you can deploy a task sequence with a feature update to a Windows 10 on ARM64 device. For more information, see [Deploy a feature update with a task sequence](https://learn.microsoft.com/en-us/intune/configmgr/core/plan-design/changes/whats-new-in-version-2103#deploy-a-feature-update-with-a-task-sequence).

## Support for Windows Insider

You can [update and service Windows Insider](https://learn.microsoft.com/en-us/intune/configmgr/sum/get-started/configure-classifications-and-products#bkmk_WIfB) builds. This ability is provided as a convenience to our customers. While this functionality should work, the support for it is best effort. Configuration Manager might not issue a hotfix for this functionality if it ceases to function.

To provide feedback on Windows Insider, use the [Feedback Hub](https://learn.microsoft.com/en-us/windows-insider/business/feedback).

## Sysprep and Windows 10, version 20H2

If you manually customize a reference computer that runs Windows 10, version 20H2, and then use [capture media](https://learn.microsoft.com/en-us/intune/configmgr/osd/deploy-use/create-capture-media), Windows Sysprep fails with the following entry in the sysprep.log: `Failed to clean the package repository database: 0x80070005.` This issue happens when you sign in to the device and create a user profile.

To work around this issue, choose one of the following options:

- Use the default image file \(install.wim\) from the installation media. Use the task sequence to apply configurations at run time.
- [Create a task sequence to capture an OS](https://learn.microsoft.com/en-us/intune/configmgr/osd/deploy-use/create-a-task-sequence-to-capture-an-operating-system)
- Remove appx packages for the signed-in user before you use capture media. For more information, see [Sysprep fails after you remove or update Microsoft Store apps that include built-in Windows images](https://learn.microsoft.com/en-us/troubleshoot/windows-client/deployment/sysprep-fails-remove-or-update-store-apps).
- Manually run Sysprep, and then boot to the capture media to capture the image.

## Next steps

[Support for the Windows ADK](https://learn.microsoft.com/en-us/intune/configmgr/core/plan-design/configs/support-for-windows-adk)

[Support for Windows 11](https://learn.microsoft.com/en-us/intune/configmgr/core/plan-design/configs/support-for-windows-11)
