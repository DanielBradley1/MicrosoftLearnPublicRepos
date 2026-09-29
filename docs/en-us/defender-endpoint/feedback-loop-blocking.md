<!-- Source: https://learn.microsoft.com/en-us/defender-endpoint/feedback-loop-blocking -->
<!-- Sitemap-Last-Modified: 2026-01-14 -->

# Feedback-loop blocking

## Overview

Feedback-loop blocking, also referred to as rapid protection, is a component of [behavioral blocking and containment capabilities](https://learn.microsoft.com/en-us/defender-endpoint/behavioral-blocking-containment) in [Microsoft Defender for Endpoint](https://learn.microsoft.com/en-us/defender-endpoint/microsoft-defender-endpoint). With feedback-loop blocking, devices across your organization are better protected from attacks.

## Prerequisites

### Supported operating systems

- Windows

## How feedback-loop blocking works

When a suspicious behavior or file is detected, such as by [Microsoft Defender Antivirus in Windows](https://learn.microsoft.com/en-us/defender-endpoint/microsoft-defender-antivirus-windows), information about that artifact is sent to multiple classifiers. The rapid protection loop engine inspects and correlates the information with other signals to arrive at a decision as to whether to block a file. Checking and classifying artifacts happens quickly. It results in rapid blocking of confirmed malware, and drives protection across the entire ecosystem.

With rapid protection in place, an attack can be stopped on a device, other devices in the organization, and devices in other organizations, as an attack attempts to broaden its foothold.

## Configuring feedback-loop blocking

If your organization is using Defender for Endpoint, feedback-loop blocking is enabled by default. However, rapid protection occurs through a combination of Defender for Endpoint capabilities, machine learning protection features, and signal-sharing across Microsoft security services. Make sure the following features and capabilities of Defender for Endpoint are enabled and configured:

- [Microsoft Defender for Endpoint baselines](https://learn.microsoft.com/en-us/defender-endpoint/configure-machines-security-baseline)
- [Devices onboarded to Microsoft Defender for Endpoint](https://learn.microsoft.com/en-us/defender-endpoint/onboard-configure)
- [EDR in block mode](https://learn.microsoft.com/en-us/defender-endpoint/edr-in-block-mode)
- [Attack surface reduction](https://learn.microsoft.com/en-us/defender-endpoint/attack-surface-reduction-rules-overview)
- [Next-generation protection](https://learn.microsoft.com/en-us/defender-endpoint/configure-microsoft-defender-antivirus-features) \(antivirus\)

Tip

If you're looking for Antivirus related information for other platforms, see:

- [Set preferences for Microsoft Defender for Endpoint on macOS](https://learn.microsoft.com/en-us/defender-endpoint/mac-preferences)
- [Microsoft Defender for Endpoint on Mac](https://learn.microsoft.com/en-us/defender-endpoint/microsoft-defender-endpoint-mac)
- [macOS Antivirus policy settings for Microsoft Defender Antivirus for Intune](https://learn.microsoft.com/en-us/intune/intune-service/protect/antivirus-microsoft-defender-settings-macos)
- [Set preferences for Microsoft Defender for Endpoint on Linux](https://learn.microsoft.com/en-us/defender-endpoint/linux-preferences)
- [Microsoft Defender for Endpoint on Linux](https://learn.microsoft.com/en-us/defender-endpoint/microsoft-defender-endpoint-linux)
- [Configure Defender for Endpoint on Android features](https://learn.microsoft.com/en-us/defender-endpoint/android-configure)
- [Configure Microsoft Defender for Endpoint on iOS features](https://learn.microsoft.com/en-us/defender-endpoint/ios-configure-features)

## Related articles

- [Behavioral blocking and containment](https://learn.microsoft.com/en-us/defender-endpoint/behavioral-blocking-containment)
- [\(Blog\) Behavioral blocking and containment: Transforming optics into protection](https://www.microsoft.com/security/blog/2020/03/09/behavioral-blocking-and-containment-transforming-optics-into-protection/)
