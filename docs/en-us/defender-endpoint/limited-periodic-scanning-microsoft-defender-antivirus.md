<!-- Source: https://learn.microsoft.com/en-us/defender-endpoint/limited-periodic-scanning-microsoft-defender-antivirus -->
<!-- Sitemap-Last-Modified: 2026-07-15 -->

# Use limited periodic scanning in Microsoft Defender Antivirus

## Overview

Note

**Microsoft does not support this feature in enterprise settings.** This feature uses only a small part of Microsoft Defender Antivirus to find threats. It can't detect most malware or unwanted software. You can't manage this feature or control it through policies. Reporting is also limited. Microsoft recommends that enterprises pick one antivirus product and use it alone.

Limited periodic scanning is a threat detection mode that works when another antivirus product is installed on a Windows 10 or Windows 11 device. You can turn it on only in certain cases. This article covers the prerequisites and steps to enable limited periodic scanning on your device. For more information, see [Microsoft Defender Antivirus compatibility](https://learn.microsoft.com/en-us/defender-endpoint/microsoft-defender-antivirus-compatibility).

## Prerequisites

Before you enable limited periodic scanning, make sure your device meets the following requirements.

### Supported operating systems

Limited periodic scanning is supported on the following operating systems:

- Windows

## How to enable limited periodic scanning

By default, Microsoft Defender Antivirus turns on when no other antivirus product is installed on a Windows 10 or Windows 11 device. It also turns on if the other product is out-of-date, expired, or not working. When Microsoft Defender Antivirus is on, you can configure it as usual on that device:

[![The Windows Security app showing Microsoft Defender Antivirus options, including scan options, settings, and update options](https://learn.microsoft.com/en-us/defender-endpoint/media/vtp-wdav.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/vtp-wdav.png#lightbox)

If another antivirus product is installed and working, Microsoft Defender Antivirus turns itself off. The Windows Security app then shows the status of the other antivirus product in the **Virus & threat protection** section. It also provides a link to that product's settings.

Below the non-Microsoft antivirus product name, select **Microsoft Defender Antivirus options**. Turn on the toggle to enable limited periodic scanning. When you slide the switch to **On**, the standard Microsoft Defender Antivirus options appear below the other product. The limited periodic scanning option is at the bottom of the page.

## Related articles

For more information about configuring and using Microsoft Defender Antivirus, see the following articles:

- [Configure behavioral, heuristic, and real-time protection](https://learn.microsoft.com/en-us/defender-endpoint/configure-protection-features-microsoft-defender-antivirus)
- [Microsoft Defender Antivirus in Windows 10](https://learn.microsoft.com/en-us/defender-endpoint/microsoft-defender-antivirus-windows)

Tip

If you're looking for Antivirus related information for other platforms, see:

- [Set preferences for Microsoft Defender for Endpoint on macOS](https://learn.microsoft.com/en-us/defender-endpoint/mac-preferences)
- [Microsoft Defender for Endpoint on Mac](https://learn.microsoft.com/en-us/defender-endpoint/microsoft-defender-endpoint-mac)
- [macOS Antivirus policy settings for Microsoft Defender Antivirus for Intune](https://learn.microsoft.com/en-us/intune/intune-service/protect/antivirus-microsoft-defender-settings-macos)
- [Set preferences for Microsoft Defender for Endpoint on Linux](https://learn.microsoft.com/en-us/defender-endpoint/linux-preferences)
- [Microsoft Defender for Endpoint on Linux](https://learn.microsoft.com/en-us/defender-endpoint/microsoft-defender-endpoint-linux)
- [Configure Defender for Endpoint on Android features](https://learn.microsoft.com/en-us/defender-endpoint/android-configure)
- [Configure Microsoft Defender for Endpoint on iOS features](https://learn.microsoft.com/en-us/defender-endpoint/ios-configure-features)
