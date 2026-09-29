<!-- Source: https://learn.microsoft.com/en-us/defender-endpoint/built-in-protection -->
<!-- Sitemap-Last-Modified: 2026-09-17 -->

# Built-in protection helps guard against ransomware

Built-in protection in [Microsoft Defender for Endpoint](https://learn.microsoft.com/en-us/defender-endpoint/microsoft-defender-endpoint) applies default security settings that help protect Windows and macOS devices from ransomware and other threats. Built-in protection complements [next-generation protection](https://learn.microsoft.com/en-us/defender-endpoint/next-generation-protection) and [attack surface reduction](https://learn.microsoft.com/en-us/defender-endpoint/attack-surface-reduction-overview) capabilities that help prevent, detect, investigate, and respond to advanced threats.

Use this article to understand how built-in protection works and find the appropriate method to manage tamper protection settings.

Tip

To strengthen protection for your organization's devices, configure these capabilities:

- [Enable cloud protection](https://learn.microsoft.com/en-us/defender-endpoint/cloud-protection-configure)
- [Turn tamper protection on](https://learn.microsoft.com/en-us/defender-endpoint/tamper-protection-overview)
- [Enable standard protection attack surface reduction \(ASR\) rules in Block mode](https://learn.microsoft.com/en-us/defender-endpoint/attack-surface-reduction-rules-overview#asr-rules)
- [Enable network protection in block mode](https://learn.microsoft.com/en-us/defender-endpoint/enable-network-protection)

## What is built-in protection, and how does it work?

Built-in protection applies default settings automatically as devices are onboarded to Defender for Endpoint. These settings help protect devices from ransomware and other threats. Built-in protection initially enabled [tamper protection](https://learn.microsoft.com/en-us/defender-endpoint/tamper-protection-overview) for your organization and later expanded to other default settings. For more information, see the Tech Community blog post, [Tamper protection will be turned on for all enterprise customers](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/tamper-protection-will-be-turned-on-for-all-enterprise-customers/ba-p/3616478).

Your security team can [change the built-in protection settings](#can-i-change-built-in-protection-settings) to meet your organization's needs.

Note

Built-in protection sets default values for Windows and macOS devices. Endpoint security settings configured through baselines or policies in [Microsoft Intune](https://learn.microsoft.com/en-us/intune/endpoint-manager-overview) override the built-in protection settings.

## Can I opt out?

You can opt out of built-in protection by configuring your own security settings. Settings that you configure through a supported management method override the built-in protection defaults. For available configuration methods, see the next section.

## Can I change built-in protection settings?

Built-in protection is a set of default settings. Your security team isn't required to keep these default settings in place. To meet your organization's business needs, your security team can change the following security features:

- **Cloud protection**: [Configure cloud protection in Microsoft Defender Antivirus](https://learn.microsoft.com/en-us/defender-endpoint/cloud-protection-configure)
- **Tamper protection**

  - [Configure tamper protection for Microsoft Defender Antivirus on Windows](https://learn.microsoft.com/en-us/defender-endpoint/tamper-protection-windows-configure)
  - [Configure tamper protection for Microsoft Defender for Endpoint on macOS](https://learn.microsoft.com/en-us/defender-endpoint/tamper-protection-macos-configure)
  - [Temporarily disable tamper protection by using troubleshooting mode](https://learn.microsoft.com/en-us/defender-endpoint/troubleshooting-mode-enable#temporarily-disable-tamper-protection)

- **Attack surface reduction \(ASR\) rules**: [Configure attack surface reduction rules and exclusions](https://learn.microsoft.com/en-us/defender-endpoint/attack-surface-reduction-rules-configure)
- **Network protection**: [Configure network protection in Microsoft Defender Antivirus](https://learn.microsoft.com/en-us/defender-endpoint/enable-network-protection)
