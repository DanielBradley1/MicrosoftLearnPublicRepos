<!-- Source: https://learn.microsoft.com/en-us/intune/solutions/windows-virtual-machines -->
<!-- Sitemap-Last-Modified: 2026-04-16 -->

# Using Windows virtual machines with Intune

Intune supports managing virtual machines running Windows Enterprise with certain limitations. Intune management doesn't depend on, or interfere with Azure Virtual Desktop management of the same virtual machine.

## Enrollment

- We recommend that you don't use Intune to manage on-demand, session-host virtual machines, also known as non-persistent virtual desktop infrastructure \(VDI\). Each VM must be enrolled when it's created. Also, regularly deleting VMs creates orphaned device records in Intune until they're [cleaned up](https://learn.microsoft.com/en-us/intune/governance/configure-cleanup-rules).
- Windows Autopilot Self-deploying and pre-provisioning deployment types aren't supported because they require a physical Trusted Platform Module \(TPM\).
- Out of Box Experience \(OOBE\) enrollment isn't supported on non-persistent VMs that can only be accessed by using RDP \(such as VMs that are hosted on Azure\). This restriction means:
- Windows Autopilot and Commercial OOBE aren't supported.

  - Enrollment Status Page isn't supported.

## Configuration

Intune doesn't support any configuration that utilizes a Trusted Platform Module or hardware management, including:

- [BitLocker settings](https://learn.microsoft.com/en-us/intune/device-configuration/overview#endpoint-protection)
- [Device Firmware Configuration Interface settings](https://learn.microsoft.com/en-us/intune/device-configuration/overview#bios-configuration-and-dfci)

## Reporting

Intune automatically detects virtual machines and reports them as "Virtual Machine" in **Devices** > **All devices** > choose a device > **Overview** > **Model** field.

Deallocated virtual machines may contribute to noncompliant device reports because they're unable to [check in with the Intune service](https://learn.microsoft.com/en-us/intune/device-configuration/troubleshoot-device-profiles#policy-refresh-intervals).

## Retirement

If you only have RDP access, don't use the [Wipe action](https://learn.microsoft.com/en-us/intune/device-management/actions/wipe). The Wipe action deletes the virtual machine's RDP settings and prevents you from ever connecting again.

## Limitations

Intune does not support using a cloned image of a computer that is already enrolled. This includes both physical and virtual devices such as Azure Virtual Desktop \(AVD\). When device enrollment or identity tokens are replicated between devices, Intune device enrollment or synchronization failures will occur.

- For more information, see [Mobile device enrollment - Windows Client Management](https://learn.microsoft.com/en-us/windows/client-management/mobile-device-enrollment) and [Certificate authentication device enrollment - Windows Client Management](https://learn.microsoft.com/en-us/windows/client-management/certificate-authentication-device-enrollment).
- For information on disabling token roaming in AVD, see [Using Azure Virtual Desktop multi-session with Microsoft Intune](https://learn.microsoft.com/en-us/intune/solutions/azure-virtual-desktop-multi-session#prerequisites).
- For information on troubleshooting issues related to image cloning, see [Error hr 0x8007064c: The machine is already enrolled](https://learn.microsoft.com/en-us/troubleshoot/mem/intune/troubleshoot-windows-enrollment-errors#error-hr-0x8007064c-the-machine-is-already-enrolled).

## Next steps

[Learn about using Azure Virtual Desktop with Intune](https://learn.microsoft.com/en-us/intune/solutions/azure-virtual-desktop)
