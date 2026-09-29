<!-- Source: https://learn.microsoft.com/en-us/defender-endpoint/client-behavioral-blocking -->
<!-- Sitemap-Last-Modified: 2025-09-29 -->

# Client behavioral blocking

**Platform**

- Windows

## Overview

Client behavioral blocking is a component of [behavioral blocking and containment capabilities](https://learn.microsoft.com/en-us/defender-endpoint/behavioral-blocking-containment) in Defender for Endpoint. As suspicious behaviors are detected on devices \(also referred to as clients or endpoints\), artifacts \(such as files or applications\) are blocked, checked, and remediated automatically.

[![Cloud and client protection](https://learn.microsoft.com/en-us/defender-endpoint/media/pre-execution-and-post-execution-detection-engines.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/pre-execution-and-post-execution-detection-engines.png#lightbox)

Antivirus protection works best when paired with cloud protection.

## How client behavioral blocking works

[Microsoft Defender Antivirus](https://learn.microsoft.com/en-us/defender-endpoint/microsoft-defender-antivirus-windows) can detect suspicious behavior, malicious code, fileless and in-memory attacks, and more on a device. When suspicious behaviors are detected, Microsoft Defender Antivirus monitors and sends those suspicious behaviors and their process trees to the cloud protection service. Machine learning differentiates between malicious applications and good behaviors within milliseconds, and classifies each artifact. In almost real time, as soon as an artifact is found to be malicious, it's blocked on the device.

Whenever a suspicious behavior is detected, an [alert](https://learn.microsoft.com/en-us/defender-endpoint/alerts-queue) is generated and is visible while the attack was detected and stopped; alerts, such as an "initial access alert," are triggered and appear in the [Microsoft Defender portal](https://learn.microsoft.com/en-us/defender-xdr/microsoft-365-defender).

Client behavioral blocking is effective because it not only helps prevent an attack from starting, it can help stop an attack that has begun executing. And, with [feedback-loop blocking](https://learn.microsoft.com/en-us/defender-endpoint/feedback-loop-blocking) \(another capability of behavioral blocking and containment\), attacks are prevented on other devices in your organization.

## Behavior-based detections

Behavior-based detections are named according to the [MITRE ATT&CK Matrix for Enterprise](https://attack.mitre.org/matrices/enterprise). The naming convention helps identify the attack stage where the malicious behavior was observed:

| Tactic | Detection threat name |
| --- | --- |
| Initial Access | `Behavior:Win32/InitialAccess.*!ml` |
| Execution | `Behavior:Win32/Execution.*!ml` |
| Persistence | `Behavior:Win32/Persistence.*!ml` |
| Privilege Escalation | `Behavior:Win32/PrivilegeEscalation.*!ml` |
| Defense Evasion | `Behavior:Win32/DefenseEvasion.*!ml` |
| Credential Access | `Behavior:Win32/CredentialAccess.*!ml` |
| Discovery | `Behavior:Win32/Discovery.*!ml` |
| Lateral Movement | `Behavior:Win32/LateralMovement.*!ml` |
| Collection | `Behavior:Win32/Collection.*!ml` |
| Command and Control | `Behavior:Win32/CommandAndControl.*!ml` |
| Exfiltration | `Behavior:Win32/Exfiltration.*!ml` |
| Impact | `Behavior:Win32/Impact.*!ml` |
| Uncategorized | `Behavior:Win32/Generic.*!ml` |

Tip

To learn more about specific threats, see **[recent global threat activity](https://www.microsoft.com/wdsi/threats)**.

## Configuring client behavioral blocking

If your organization is using Defender for Endpoint, client behavioral blocking is enabled by default. However, to benefit from all Defender for Endpoint capabilities, including [behavioral blocking and containment](https://learn.microsoft.com/en-us/defender-endpoint/behavioral-blocking-containment), make sure the following features and capabilities of Defender for Endpoint are enabled and configured:

- [Defender for Endpoint baselines](https://learn.microsoft.com/en-us/defender-endpoint/configure-machines-security-baseline)
- [Devices onboarded to Defender for Endpoint](https://learn.microsoft.com/en-us/defender-endpoint/onboard-configure)
- [EDR in block mode](https://learn.microsoft.com/en-us/defender-endpoint/edr-in-block-mode)
- [Attack surface reduction](https://learn.microsoft.com/en-us/defender-endpoint/attack-surface-reduction-rules-overview)
- [Next-generation protection](https://learn.microsoft.com/en-us/defender-endpoint/configure-microsoft-defender-antivirus-features) \(antivirus, antimalware, and other threat protection capabilities\)

Tip

If you're looking for Antivirus related information for other platforms, see:

- [Set preferences for Microsoft Defender for Endpoint on macOS](https://learn.microsoft.com/en-us/defender-endpoint/mac-preferences)
- [Microsoft Defender for Endpoint on Mac](https://learn.microsoft.com/en-us/defender-endpoint/microsoft-defender-endpoint-mac)
- [macOS Antivirus policy settings for Microsoft Defender Antivirus for Intune](https://learn.microsoft.com/en-us/intune/intune-service/protect/antivirus-microsoft-defender-settings-macos)
- [Set preferences for Microsoft Defender for Endpoint on Linux](https://learn.microsoft.com/en-us/defender-endpoint/linux-preferences)
- [Microsoft Defender for Endpoint on Linux](https://learn.microsoft.com/en-us/defender-endpoint/microsoft-defender-endpoint-linux)
- [Configure Defender for Endpoint on Android features](https://learn.microsoft.com/en-us/defender-endpoint/android-configure)
- [Configure Microsoft Defender for Endpoint on iOS features](https://learn.microsoft.com/en-us/defender-endpoint/ios-configure-features)
