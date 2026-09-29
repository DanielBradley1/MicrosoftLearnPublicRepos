<!-- Source: https://learn.microsoft.com/en-us/defender-endpoint/microsoft-defender-endpoint -->
<!-- Sitemap-Last-Modified: 2026-07-28 -->

# Microsoft Defender for Endpoint overview

Microsoft Defender for Endpoint is an enterprise endpoint security platform designed to help organizations prevent, detect, investigate, and respond to advanced threats on their endpoints. These endpoints include laptops, phones, tablets, PCs, access points, routers, and firewalls.

As the endpoint security pillar of [Microsoft Defender](https://learn.microsoft.com/en-us/defender-xdr/), Defender for Endpoint feeds endpoint signals into the unified Defender portal. The portal correlates these signals with alerts from identity, email, and cloud workloads to form complete incident views. Your security team can trace an attack from a phishing email to a compromised endpoint to lateral movement - all in one place.

Defender for Endpoint also integrates with the broader Microsoft security ecosystem, including:

- [Intune](https://learn.microsoft.com/en-us/intune/intune-service/)
- [Microsoft Defender for Cloud](https://learn.microsoft.com/en-us/azure/defender-for-cloud/)
- [Microsoft Defender for Cloud Apps](https://learn.microsoft.com/en-us/defender-cloud-apps/)
- [Microsoft Defender for Identity](https://learn.microsoft.com/en-us/defender-for-identity/)
- [Microsoft Defender for Office 365](https://learn.microsoft.com/en-us/defender-office-365/)
- [Microsoft Defender Vulnerability Management](https://learn.microsoft.com/en-us/defender-vulnerability-management/defender-vulnerability-management)
- [Microsoft Sentinel](https://learn.microsoft.com/en-us/azure/sentinel/)
- [Microsoft threat intelligence](https://learn.microsoft.com/en-us/defender-endpoint/threat-protection-integration)

## Operating systems

Microsoft Defender for Endpoint supports the following operating systems: Windows, macOS, Linux, Android, and iOS. For detailed information about capabilities on each platform, see the following articles.

- [Microsoft Defender for Endpoint on Windows](https://learn.microsoft.com/en-us/defender-endpoint/microsoft-defender-endpoint-windows)
- [Microsoft Defender for Endpoint on Linux](https://learn.microsoft.com/en-us/defender-endpoint/microsoft-defender-endpoint-linux)
- [Microsoft Defender for Endpoint on macOS](https://learn.microsoft.com/en-us/defender-endpoint/microsoft-defender-endpoint-mac)
- [Microsoft Defender for Endpoint on Android and iOS](https://learn.microsoft.com/en-us/defender-endpoint/mtd)

For detailed system requirements and supported versions, see [Minimum requirements for Microsoft Defender for Endpoint](https://learn.microsoft.com/en-us/defender-endpoint/minimum-requirements).

## Licensing

Defender for Endpoint is available with several licensing options, including Defender for Endpoint Plan 1, Plan 2, and Microsoft Defender for Business. Microsoft 365 E5 and Microsoft 365 E5 Security include Defender for Endpoint Plan 2. For licensing requirements, see [Minimum requirements for Microsoft Defender for Endpoint](https://learn.microsoft.com/en-us/defender-endpoint/minimum-requirements#licensing-requirements). For full plan comparison and pricing, see [Microsoft Defender for Endpoint plans and pricing](https://www.microsoft.com/security/business/endpoint-security/microsoft-defender-endpoint#Licensing).

Tip

The more Microsoft Defender workloads you deploy \(identity, email, cloud apps, and endpoints\), the stronger your overall protection becomes. Each workload contributes signals that enrich detection, correlation, and automated response in the unified Defender portal.

### Server licensing and Defender for Servers

If you're using Defender for Endpoint on servers, you might be eligible for a discount if you're also using [Microsoft Defender for Servers](https://learn.microsoft.com/en-us/azure/defender-for-cloud/defender-for-servers-overview). Learn about [licensing discounts available when you have both Defender for Endpoint and Defender for Servers](https://learn.microsoft.com/en-us/azure/defender-for-cloud/faq-defender-for-servers#can-i-get-a-discount-if-i-already-have-a-microsoft-defender-for-endpoint-license-).

## Defender for Endpoint capabilities

Defender for Endpoint provides a comprehensive set of capabilities, including [endpoint detection and response](https://learn.microsoft.com/en-us/defender-endpoint/overview-endpoint-detection-response), [autonomous protection](https://learn.microsoft.com/en-us/defender-xdr/automatic-attack-disruption) with [automatic attack disruption](https://learn.microsoft.com/en-us/defender-xdr/automatic-attack-disruption) and [predictive shielding](https://learn.microsoft.com/en-us/defender-xdr/shield-predict-threats), [next-generation protection](https://learn.microsoft.com/en-us/defender-endpoint/next-generation-protection) with ransomware prevention, [attack surface reduction](https://learn.microsoft.com/en-us/defender-endpoint/overview-attack-surface-reduction), [vulnerability management](https://learn.microsoft.com/en-us/defender-vulnerability-management/defender-vulnerability-management), [Endpoint Attack Notifications](https://learn.microsoft.com/en-us/defender-endpoint/endpoint-attack-notifications), and [APIs](https://learn.microsoft.com/en-us/defender-endpoint/api/management-apis) for integration with your existing workflows.

For guidance on planning and rolling out Defender for Endpoint in your environment, see [Plan your Defender for Endpoint deployment](https://learn.microsoft.com/en-us/defender-endpoint/mde-planning-guide). Before you begin, review [Minimum requirements](https://learn.microsoft.com/en-us/defender-endpoint/minimum-requirements) to confirm your environment is ready. To learn about new and upcoming capabilities, see [What's new in Microsoft Defender for Endpoint](https://learn.microsoft.com/en-us/defender-endpoint/whats-new-in-microsoft-defender-endpoint). To turn on preview features in your environment, see [Preview features in Microsoft Defender XDR](https://learn.microsoft.com/en-us/defender-xdr/preview).

For a step-by-step workflow for piloting and deploying Defender for Endpoint in a production environment, including onboarding endpoints and verifying pilot groups, see [Pilot and deploy Defender for Endpoint](https://learn.microsoft.com/en-us/defender-xdr/pilot-deploy-defender-endpoint).

For platform-specific capabilities, see the [Windows](https://learn.microsoft.com/en-us/defender-endpoint/microsoft-defender-endpoint-windows), [Linux](https://learn.microsoft.com/en-us/defender-endpoint/microsoft-defender-endpoint-linux), [macOS](https://learn.microsoft.com/en-us/defender-endpoint/microsoft-defender-endpoint-mac), and [Android and iOS mobile threat defense](https://learn.microsoft.com/en-us/defender-endpoint/mtd) documentation.

### APIs and integrations

Use these capabilities to integrate Microsoft Defender for Endpoint with your existing security tools and workflows, and automate tasks by using APIs. [Management and automation APIs](https://learn.microsoft.com/en-us/defender-endpoint/api/management-apis) enable you to automate workflows and integrate Defender for Endpoint into your existing processes. You can also use [partner integrations](https://learn.microsoft.com/en-us/defender-endpoint/partner-integration) to connect with Microsoft and non-Microsoft security solutions.

## Privacy and compliance

Defender for Endpoint is built with privacy, data protection, and regulatory compliance as core principles. For details on how Defender for Endpoint collects, stores, and protects your data, see [Data storage and privacy](https://learn.microsoft.com/en-us/defender-endpoint/data-storage-privacy).

Defender for Endpoint supports a [Zero Trust](https://learn.microsoft.com/en-us/defender-endpoint/zero-trust-with-microsoft-defender-endpoint) security model, helping you verify identities and device health before granting access. To learn more about Microsoft's data handling practices and privacy commitments, visit the [Microsoft Trust Center](https://www.microsoft.com/trust-center/privacy) and [Privacy at Microsoft](https://privacy.microsoft.com/). For an overview of how Microsoft manages data privacy and protection in compliance with global standards, see [Privacy and data management](https://learn.microsoft.com/en-us/compliance/assurance/assurance-privacy).

## Related content

- [Pilot and deploy Defender for Endpoint](https://learn.microsoft.com/en-us/defender-xdr/pilot-deploy-defender-endpoint)
- [Plan your Defender for Endpoint deployment](https://learn.microsoft.com/en-us/defender-endpoint/mde-planning-guide)
- [What's new in Microsoft Defender for Endpoint](https://learn.microsoft.com/en-us/defender-endpoint/whats-new-in-microsoft-defender-endpoint)
