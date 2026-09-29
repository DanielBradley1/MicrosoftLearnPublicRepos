<!-- Source: https://learn.microsoft.com/en-us/defender-endpoint/tamper-protection-linux-audit-mode -->
<!-- Sitemap-Last-Modified: 2026-09-09 -->

# Use tamper protection in audit mode for Microsoft Defender for Endpoint on Linux

Important

Some information in this article relates to a prereleased product which may be substantially modified before it's commercially released. Microsoft makes no warranties, expressed or implied, with respect to the information provided here.

Tamper protection in audit mode for Microsoft Defender for Endpoint on Linux detects unauthorized modifications to Defender for Endpoint assets, including configuration files, directories, processes, and services. It detects changes made by any user, including the root user, and generates alerts without blocking the activity.

Use this article to review prerequisites, verify audit mode, investigate alerts, and test tamper detection. For an explanation of tamper protection and how its modes differ by operating system, see [Tamper protection overview](https://learn.microsoft.com/en-us/defender-endpoint/tamper-protection-overview).

On Linux devices, **Audit** mode detects and alerts on the following tampering activities:

- Modification of Defender for Endpoint configuration files.
- Deletion of Defender for Endpoint configuration files, state files, and binaries.
- Renaming or moving Defender for Endpoint configuration files, state files, and binaries.
- Termination of Defender for Endpoint processes, including restarting Defender for Endpoint services.

Audit mode provides visibility into tampering attempts through alerts and advanced hunting in the Microsoft Defender portal.

## Prerequisites

Before you use tamper protection in audit mode, make sure your device meets the following requirements:

- Defender for Endpoint version `101.26072.0004` \(September 2026\) or later from the Insiders-Slow ring.
- Allow access to `https://config.edge.skype.com/config/v1`. For more information, see [Microsoft Defender for Endpoint streamlined connectivity URLs - commercial](https://learn.microsoft.com/en-us/defender-endpoint/streamlined-device-connectivity-urls-commercial#urls-used-for-core-functionality).
- Tamper protection requires a Linux kernel that supports extended Berkeley Packet Filter \(eBPF\) with BPF Type Format \(BTF\). BTF provides the file and process context that Defender for Endpoint uses to detect tampering attempts. The following Linux distributions and kernel versions are supported:
  | Distribution | Supported version | Minimum kernel version |
  | --- | --- | --- |
  | Alma Linux 10 | 10.x | 6.12.0-55 |
  | Alma Linux 9 | 9.2+ | 5.14.0-284 |
  | Alma Linux 8 | 8.8+ | 4.18.0-477 |
  | Amazon Linux | 2023 | 6.1.132-147.221.amzn2023 |
  | Azure Linux 3 | 3 | 6.6.78.1-3.azl3 |
  | CentOS Stream | 10 | 6.12.0 |
  | CentOS Stream | 9 | 5.14.0 |
  | CentOS Stream | 8 | 4.18.0-553 |
  | Debian | 13 | 6.12 |
  | Debian | 12 | 6.1.0-9 |
  | Fedora | arm64: 40-43 | 6.8.5 |
  | Fedora | x86\_64: 33-43 | 5.8.15 |
  | Mariner 2 | 2 | 5.15 |
  | Oracle Linux 10 | 10.x \(UEK8\) | 6.12.0 |
  | Oracle Linux 10 | 10.x \(RHCK\) | 6.12.0-55 |
  | Oracle Linux 9 | 9.x \(UEK8\) | 6.12.0 |
  | Oracle Linux 9 | 9.x \(UEK7\) | 5.15.0 |
  | Oracle Linux 9 | 9.x \(RHCK\) | 5.14.0-70 |
  | Oracle Linux 8 | 8.10 \(UEK7\) | 5.15.0 |
  | Oracle Linux 8 | 8.10 \(RHCK\) | 4.18.0-553 |
  | RHEL 10 | 10.x | 6.12.0-55 |
  | RHEL 9 | 9.x | 5.14.0-70 |
  | RHEL 8 | 8.4+ | 4.18.0-305 |
  | Rocky Linux 10 | 10.x | 6.12.0-55 |
  | Rocky Linux 9 | 9.3+ | 5.14.0-362 |
  | Rocky Linux 8 | 8.9+ | 4.18.0-513 |
  | SLES 16 | 16 | 6.12.0-160000 |
  | SLES 15 | 15.5+ | 5.14.21-150500 |
  | Ubuntu LTS | 24.04 | 6.8.0 |
  | Ubuntu LTS | 22.04 | 5.15.0<sup>\*</sup> |
  | Ubuntu LTS | 20.04 | 5.15.0<sup>\*</sup> |
  | Ubuntu Pro | 24.04 | 6.8.0 |
  | Ubuntu Pro | 22.04 | 5.15.0<sup>\*</sup> |


  Important


  <sup>\*</sup> For Ubuntu 20.04 and Ubuntu 22.04, the following generic kernel versions aren't supported: `5.15.0-144`, `5.15.0-150`, `5.15.0-151`, and `5.15.0-152`.

## Enable tamper protection in audit mode

During Preview, tamper protection in audit mode is enabled by default. No configuration is required.

The feature rolls out gradually over two weeks to eligible devices in the Insiders-Slow ring that meet the prerequisites.

## Verify audit mode enablement

Run the following command to check the tamper protection status and errors:

```bash
mdatp health --details tamper_protection
```

The following output shows that tamper protection is enabled in audit mode without errors:

```console
tamper_protection_enforcement_level : "audit"
tamper_protection_errors            : []
```

If tamper protection can't be enabled, `tamper_protection_enforcement_level` shows `disabled`. For error descriptions and resolution steps, see [Troubleshoot problems with tamper protection](https://learn.microsoft.com/en-us/defender-endpoint/tamper-protection-troubleshoot).

## View tampering alerts in the Microsoft Defender portal

On the **Device inventory** page in the Microsoft Defender portal at [https://security.microsoft.com/machines](https://security.microsoft.com/machines), select the affected Linux device. Then, review **Timeline** and **Incidents and alerts** for tampering activity and alerts.

Open a tampering alert to review the affected assets, process tree, alert timeline, and related activity. For more information, see [Investigate alerts in Microsoft Defender for Endpoint](https://learn.microsoft.com/en-us/defender-endpoint/investigate-alerts).

## Query tampering attempts with advanced hunting

To get the device ID directly from a Linux device, run the following command:

```bash
mdatp health --field edr_device_id
```

Use the device ID to filter the cross-platform queries in [Query tampering attempts with advanced hunting](https://learn.microsoft.com/en-us/defender-endpoint/tamper-protection-overview#query-tampering-attempts-with-advanced-hunting).

## Test a tampering scenario

To generate a test tampering attempt, open the Defender for Endpoint configuration file in `vim`:

```bash
sudo vim /etc/opt/microsoft/mdatp/managed/mdatp_managed.json
```

Modify and save the file. The attempt generates a tampering alert in the Microsoft Defender portal. The alert includes information about the initiating process and target file.

To reduce alert noise from known and approved activity, see [Tune alerts for legitimate tampering activity](https://learn.microsoft.com/en-us/defender-endpoint/tamper-protection-overview#tune-alerts-for-legitimate-tampering-activity).

## Related content

- [Tamper protection overview](https://learn.microsoft.com/en-us/defender-endpoint/tamper-protection-overview)
- [Troubleshoot problems with tamper protection](https://learn.microsoft.com/en-us/defender-endpoint/tamper-protection-troubleshoot)
- [Microsoft Defender for Endpoint on Linux](https://learn.microsoft.com/en-us/defender-endpoint/microsoft-defender-endpoint-linux)
- [Configure security policies and settings for Microsoft Defender for Endpoint on Linux](https://learn.microsoft.com/en-us/defender-endpoint/linux-preferences)
- [Configure eBPF-based sensor for Microsoft Defender for Endpoint on Linux](https://learn.microsoft.com/en-us/defender-endpoint/linux-support-ebpf)
- [Investigate alerts in Microsoft Defender XDR](https://learn.microsoft.com/en-us/defender-xdr/investigate-alerts)
