<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/core/plan-design/configs/support-for-windows-adk -->
<!-- Sitemap-Last-Modified: 2025-12-09 -->

# Support for the Windows ADK in Configuration Manager

*Applies to: Configuration Manager \(current branch\)*

When you deploy operating systems with Configuration Manager, the Windows Assessment and Deployment Kit \(ADK\) is a required external dependency. For more information, see the following articles:

- [Infrastructure requirements for OS deployment](https://learn.microsoft.com/en-us/mem/configmgr/osd/plan-design/infrastructure-requirements-for-operating-system-deployment#windows-adk)
- [Download the Windows ADK](https://learn.microsoft.com/en-us/windows-hardware/get-started/adk-install)

  Important

  - Windows PE is a separate installer. Make sure to download both the **Windows ADK** and the **Windows PE add-on for the ADK**.
  - **ADK 10.1.26100.X \(May 2024, Dec 2024\)** \(10.1.26100.X\) or newer is required to deploy Windows ARM64 operating systems on Configuration Manager 2403 or newer.

## Windows ADK versions

The following table lists the versions of the Windows ADK that you can use with different versions of Configuration Manager.

| Windows ADK version | ConfigMgr 2503 | ConfigMgr 2509 | ConfigMgr 2603 |
| --- | --- | --- | --- |
| **ADK 10.1.28000.1 \(Updated Nov 2025\)**  <br>\(10.1.28000.1\) | ❌ | ❌ | ❌ |
| **ADK 10.1.26100.2454 \(Updated Dec 2024\)**  <br>\(10.1.26100.X\) | ✅ | ✅ | ✅ |
| **ADK 10.1.26100.1 \(May 2024\)**  <br>\(10.1.26100.1\) | ✅ | ✅ | ✅ |
| **ADK 10.1.25398.1 \(updated September 2023\)**  <br>\(10.1.25398.1\) | ❌ | ❌ | ❌ |
| **ADK for Windows 11, version 22H2**  <br>\(10.1.22621.1\) | ✅ | ✅ | ✅ |
| **ADK for Windows 11, version 21H1**  <br>\(10.1.22000\) | ✅ | ✅ | ✅ |
| **ADK for Windows Server 2022**  <br>\(10.1.20348\) | ✅ | ✅ | ✅ |
| **ADK for Windows 10, version 2004**  <br>\(10.1.19041\) **EOS** | ❌ | ❌ | ❌ |

| Key |
| --- |
| ✅ = **Supported**  <br>This table only shows Windows ADK supportability in relation to the version of Configuration Manager. Microsoft recommends using the Windows ADK that matches the version of Windows you're deploying. Use the latest Windows ADK version when deploying the latest Windows version. The latest Windows ADK version might support deployment of older OS versions, such as Windows 10. For more information on Windows ADK component supportability, see [DISM supported platforms](https://learn.microsoft.com/en-us/windows-hardware/manufacture/desktop/dism-supported-platforms), [USMT requirements](https://learn.microsoft.com/en-us/windows/deployment/usmt/usmt-requirements#bkmk-1), and [Choose the right ADK for your scenario](https://learn.microsoft.com/en-us/windows-hardware/get-started/adk-install#choose-the-right-adk-for-your-scenario). |
| ![Backwards compatible](https://learn.microsoft.com/en-us/intune/configmgr/core/plan-design/configs/media/blue-compat.png) = **Backward compatible**  <br>This combination isn't tested but should work. We'll document any known issues or caveats. |
| ❌ = **Not supported** |

## Support notes

- **ADK 10.1.25398.1 \(updated September 2023\)** Windows PE boot images aren't supported for use with Configuration Manager due to known issues:

  - VBScript doesn't work in WinPE.
  - The **Pre-provision BitLocker** task doesn't work in WinPE.
  - Devices with UFS storage, such as the Surface Go 4, don't work in WinPE.

    Instead use the **ADK 10.1.26100.X \(May 2024, Dec 2024\)** \(10.1.26100.X\) or newer where these issues are resolved.

- For information on applying the [BlackLotus UEFI bootkit vulnerability](https://support.microsoft.com/topic/kb5025885-how-to-manage-the-windows-boot-manager-revocations-for-secure-boot-changes-associated-with-cve-2023-24932-41a975df-beb2-40c1-99a3-b3ff139f832d) security updates to boot images from the ADKs before the **ADK 10.1.26100.1 \(May 2024, Dec 2024\)** \(10.1.26100.1\), see [Customize Windows PE boot images](https://learn.microsoft.com/en-us/windows/deployment/customize-boot-image). Boot images from the **ADK 10.1.26100.1 \(May 2024, Dec 2024\)** \(10.1.26100.1\) and newer already have the BlackLotus UEFI bootkit vulnerability security update applied to them. For this reason, it's recommended to use boot images from the **ADK 10.1.26100.1 \(May 2024, Dec 2024\)** \(10.1.26100.X\) or newer.
- Windows Server builds have the same Windows ADK requirement as the associated Windows client version. For example, Windows Server 2016 is the same build version as Windows 10 LTSB 2016.

- The last supported version of 32-bit WinPE is available in the **WinPE add-on for Windows 10, version 2004** \(10.1.19041\). Versions of the WinPE add-on for the ADK after the **ADK for Windows 10, version 2004** \(10.1.19041\) no longer support 32-bit versions of Windows PE \(WinPE\). For more information, see [Download and install the Windows ADK](https://learn.microsoft.com/en-us/windows-hardware/get-started/adk-install).

  Configuration Manager supports the use of older versions of Windows PE as boot images, but you can't customize them in the Configuration Manager console. For more information, see [Customize boot images with Configuration Manager](https://learn.microsoft.com/en-us/intune/configmgr/osd/get-started/customize-boot-images).

## Known issues

### Pre-provisioning BitLocker during task sequence doesn't own TPM

Applies to: *Windows ADK for Windows 11 \(version 10.1.22000\)*

When you use a Windows 11-based boot image with an OS deployment task sequence that includes the [Pre-provision BitLocker](https://learn.microsoft.com/en-us/intune/configmgr/osd/understand/task-sequence-steps#BKMK_PreProvisionBitLocker) step, the step might fail. You'll see errors similar to the following strings in the smsts.log:

```log
'TakeOwnership' failed (2147942402)
pTpm->TakeOwnership(sOwnerAuth), HRESULT=80070002
Failed to take ownership of TPM. Ensure that Active Directory permissions are properly configured
The system cannot find the file specified. (Error: 80070002; Source: Windows)
Process completed with exit code 2147942402
Failed to run the action: Pre-provision BitLocker. Error -2147024894
```

To work around this issue, add a **Run Command Line** step to the task sequence before the **Pre-provision BitLocker** step. Run the following command:

`reg.exe add HKLM\SOFTWARE\Policies\Microsoft\TPM /v OSManagedAuthLevel /t REG_DWORD /d 2 /f`

For more information on this registry key, see [Change the TPM owner password](https://learn.microsoft.com/en-us/windows/security/information-protection/tpm/change-the-tpm-owner-password). This work around is only needed for ADK releases 10.1.22000. Later versions aren't affected.

## Next steps

[Support for Windows 11](https://learn.microsoft.com/en-us/intune/configmgr/core/plan-design/configs/support-for-windows-11)

[Support for Windows 10](https://learn.microsoft.com/en-us/intune/configmgr/core/plan-design/configs/support-for-windows-10)

[Supported OS versions for clients](https://learn.microsoft.com/en-us/intune/configmgr/core/plan-design/configs/supported-operating-systems-for-clients-and-devices)
