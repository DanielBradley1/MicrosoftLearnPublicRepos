<!-- Source: https://learn.microsoft.com/en-us/defender-office-365/zero-trust-with-microsoft-365-defender-office-365 -->
<!-- Sitemap-Last-Modified: 2026-07-17 -->

# Zero Trust with Microsoft Defender for Office 365

## How Microsoft Defender for Office 365 supports Zero Trust

Microsoft Defender for Office 365 is a cloud-based email filtering service that helps protect your organization against advanced threats to email and collaboration tools \(for example, phishing, business email compromise, and malware attacks\). Defender for Office 365 also provides investigation, Threat Hunting, and remediation capabilities to help security teams efficiently identify, prioritize, investigate, and respond to threats.

[Zero Trust](https://learn.microsoft.com/en-us/security/zero-trust/zero-trust-overview) is a security strategy for designing and implementing the following set of security principles:

| Verify explicitly | Use least privilege access | Assume breach |
| --- | --- | --- |
| Always authenticate and authorize based on all available data points. | Limit user access with Just-In-Time and Just-Enough-Access \(JIT/JEA\), risk-based adaptive policies, and data protection. | Minimize blast radius and segment access. Verify end-to-end encryption and use analytics to get visibility, drive threat detection, and improve defenses. |

Defender for Office 365 is the primary component of the **Assume breach** principle and an important element of your extended detection and response \(XDR\) deployment with Microsoft Defender XDR. Defender for Office 365 consists of three levels of protection based on your subscription level:

| Protection level | Description |
| --- | --- |
| The built-in security features for all cloud mailboxes | Prevent broad, volume-based, known attacks. |
| Defender for Office 365 P1 | Protects email and collaboration from zero-day malware, phish, and business email compromise. |
| Defender for Office 365 P2 | Adds post-breach investigation, hunting, and response, as well as automation, and simulation \(for training\). |

## Threat protection capabilities that support Zero Trust

The Defender for Office 365 protection or filtering stack can be broken out into four phases:

1. **Edge protection**: Edge blocks are designed to be automatic. For false positives, senders are notified and told how to address their issue. Mail flow connectors that route messages from trusted partners with limited reputation can ensure deliverability, or temporary overrides can be put in place, when onboarding new endpoints.
2. **Sender intelligence**: Critical for catching spam, bulk, impersonation, and unauthorized spoof messages, and also factor into phish detection.
3. **Content filtering**: The filtering stack begins to handle the specific contents of the mail, including its hyperlinks and attachments.
4. **Post-delivery protection**: After mail or file delivery, acting on mail that is in various mailboxes and files and links that appear in clients like Microsoft Teams.

The Defender for Office 365 is also secure by default by quarantining email with suspected malware and using anti-spam policies to handle email with a high suspicion of phishing.

## Next steps

Learn how to set up your SecOps team with the [Microsoft Defender for Office 365 Security Operations Guide](https://learn.microsoft.com/en-us/defender-office-365/mdo-sec-ops-guide).

Learn more about Zero Trust and how to build an enterprise-scale strategy and architecture with the [Zero Trust Guidance Center](https://learn.microsoft.com/en-us/security/zero-trust).

Learn about other Microsoft 365 capabilities that contribute to a strong Zero Trust strategy and architecture with [Zero Trust deployment plan with Microsoft 365](https://learn.microsoft.com/en-us/defender-xdr/zero-trust-with-microsoft-365-defender).

For an overview of Zero Trust for Microsoft Defender XDR services, see [Zero Trust with Microsoft Defender XDR](https://learn.microsoft.com/en-us/defender-xdr/zero-trust-with-microsoft-365-defender).
