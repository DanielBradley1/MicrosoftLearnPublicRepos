<!-- Source: https://learn.microsoft.com/en-us/defender-endpoint/indicator-certificates -->
<!-- Sitemap-Last-Modified: 2026-07-03 -->

# Create indicators for certificates in Microsoft Defender for Endpoint

This article shows you how to create certificate-based indicators in Microsoft Defender for Endpoint to allow or block signed applications. Some common use cases include:

- Scenarios when you need to deploy blocking technologies, such as [attack surface reduction rules](https://learn.microsoft.com/en-us/defender-endpoint/attack-surface-reduction-rules-overview) but need to allow behaviors from signed applications by adding the certificate in the allowlist.
- Blocking the use of a specific signed application across your organization. By creating an indicator to block the certificate of the application, Microsoft Defender Antivirus prevents file executions \(block and remediate\), and automated investigation and remediation behaves the same.

## Before you begin

It's important to understand the following requirements before creating indicators for certificates:

- This feature is available if your organization uses Microsoft Defender Antivirus \(in active mode\) and cloud-based protection is enabled. For more information, see [Manage cloud-based protection](https://learn.microsoft.com/en-us/defender-endpoint/deploy-manage-report-microsoft-defender-antivirus).
- The anti-malware client version must be `4.18.1901.x` or later.
- Supported on machines on Windows 10, version 1703 or later, Windows Server 2012 R2 and later, or Azure Stack HCI OS, version 23H2 and later.

  Note

  Windows Server 2016 and Windows Server 2012 R2 must be onboarded using the instructions in [Onboard Windows Server 2012 R2 and Windows Server 2016 to Microsoft Defender for Endpoint](https://learn.microsoft.com/en-us/defender-endpoint/onboard-server) for certificate-based indicators to work.
- The virus and threat protection definitions must be up to date.
- This feature supports entering .CER or .PEM file extensions.

Important

- A valid leaf certificate is a signing certificate that has a valid certification path and must be chained to the Root Certificate Authority \(CA\) trusted by Microsoft. Alternatively, a custom \(self-signed\) certificate can be used as long as it's trusted by the client \(Root CA certificate is installed under the Local Machine 'Trusted Root Certification Authorities'\).
- The children or parent of the allow/block certificate IOCs aren't included in the allow/block IoC functionality, only leaf certificates are supported.
- Microsoft signed certificates can't be blocked.

Note

In situations where a certificate-based indicator is configured to **Block**, but a file hash indicator for one of its signed files is configured to **Allow**, this configuration is **not supported by design**. Certificate-based indicators have higher precedence in the Microsoft Defender for Endpoint evaluation pipeline and will always override file hash allow indicators. A configuration that simultaneously:

- blocks a certificate, and
- attempts to allow one of its signed files via file hash

is **not supported**. Certificate-based indicators take precedence, and therefore the file will continue to be blocked.

## Create an indicator for certificates from the settings page

Use the following steps to create a certificate indicator from the Settings page.

Important

Creating or removing a certificate indicator of compromise \(IoC\) can take up to 3 hours.

1. In the navigation pane, select **Settings** > **Endpoints** > **Indicators** \(under **Rules**\).
2. Select **Add indicator**.
3. Specify the following details:

   - **Indicator**: Specify the entity details and define the expiration of the indicator.
   - **Action**: Specify the action to be taken and provide a description.
   - **Scope**: Define the scope of the machine group.

4. Review the details on the **Summary** tab, and then select **Save**.

## Related articles

- [Create indicators](https://learn.microsoft.com/en-us/defender-endpoint/indicators-overview)
- [Create indicators for files](https://learn.microsoft.com/en-us/defender-endpoint/indicator-file)
- [Create indicators for IPs and URLs/domains](https://learn.microsoft.com/en-us/defender-endpoint/indicator-ip-domain)
- [Manage indicators](https://learn.microsoft.com/en-us/defender-endpoint/indicator-manage)
- [Exclusions for Microsoft Defender for Endpoint and Microsoft Defender Antivirus](https://learn.microsoft.com/en-us/defender-endpoint/defender-endpoint-exclusions-overview)
