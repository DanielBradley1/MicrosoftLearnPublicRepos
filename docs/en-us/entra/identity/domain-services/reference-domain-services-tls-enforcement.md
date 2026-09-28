<!-- Source: https://learn.microsoft.com/en-us/entra/identity/domain-services/reference-domain-services-tls-enforcement -->
<!-- Sitemap-Last-Modified: 2025-09-03 -->

# How to migrate to Transport Layer Security \(TLS\) 1.2 enforcement for Microsoft Entra Domain Services

Microsoft is enhancing security by disabling TLS versions 1.0 and 1.1 as communicated on November 10, 2023. While the Microsoft implementation of TLS 1.0 and TLS 1.1 versions isn't known to have vulnerabilities, TLS 1.2 or later versions provide improved security features, including perfect forward secrecy and stronger cipher suites. This change helps protect customer data and ensures compliance with industry standards.

Microsoft Entra Domain Services supports TLS versions 1.0 and 1.1, but they're disabled by default. Domain Services has removed the ability to disable **TLS 1.2 Only Mode**. Customers who disable **TLS 1.2 Only Mode** can enable it.

You can use the Azure portal or PowerShell to enable **TLS 1.2 Only Mode**.

## Prerequisites

You need the [Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#application-administrator) and [Groups Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#groups-administrator) roles in Microsoft Entra ID to change security settings such as **TLS 1.2 Only Mode**.

## Identify applications that use deprecated TLS versions

Before you enable **TLS 1.2 Only Mode**, it's important to identify applications that still use TLS 1.0 or 1.1, and update them or replace them with alternatives that support TLS 1.2. For more information about apps that are expected to be impacted, see [TLS 1.0 and TLS 1.1 deprecation in Windows](https://learn.microsoft.com/en-us/windows/win32/secauthn/tls-10-11-deprecation-in-windows).

- [**Azure portal**](#tabpanel_1_portal)
- [**PowerShell**](#tabpanel_1_powershell)

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as an [Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#application-administrator) and a [Groups Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#groups-administrator).
2. Search for **Domain Services**, and select your Domain Services instance.
3. Select **Security Settings**.
4. If **TLS 1.2 Only Mode** is set to **Disable**, the instance enables TLS versions 1.0 and 1.1. Set **TLS 1.2 Only Mode** to **Enable**, and then click **Save**.

   This change may take about 10 minutes to complete as domain security updates are enforced.

   ![Screenshot that shows how to enable TLS 1.2 Only Mode for Domain Services.](https://learn.microsoft.com/en-us/entra/identity/domain-services/media/reference-domain-services-tls-enforcement/enable.png)

Note

Until June 30, 2026, you can select **Disable** to temporarily allow legacy TLS traffic while you update or replace apps that might fail. Select **Enable** again to remain compliant.

1. Install the Az.ADDomainServices module:

   ```powershell
   Install-Module -Name Az.ADDomainServices
   ```

2. Connect to the Azure subscription:

   ```powershell
   Connect-AzAccount -Subscription aaaa0a0a-bb1b-cc2c-dd3d-eeeeee4e4e4e
   ```

3. Update the value of **TLS 1.2 Only Mode** by executing these two commands:

   ```powershell
   $domainService = Get-AzADDomainService
   ```


   ```powershell
   Update-AzADDomainService -Name $domainService.Name -ResourceGroupName $domainService.ResourceGroupName -DomainSecuritySettingTlsV1 Disabled
   ```


   This command may take about 10 minutes to complete as domain security updates are enforced.

## Troubleshooting

- Some apps provide logs or error messages when TLS handshakes fail. Use application-level diagnostics to look for errors related to unsupported protocols.
- Until June 30, 2026, you can modify the following PowerShell example to temporarily allow legacy TLS traffic while you update or replace apps:

  ```powershell
  Update-AzADDomainService -Name $domainService.Name -ResourceGroupName $domainService.ResourceGroupName -DomainSecuritySettingTlsV1 Enabled
  ```

- For more troubleshooting help, you can [create an Azure support request](https://learn.microsoft.com/en-us/entra/fundamentals/how-to-get-support).

## Related content

- [Enable support for TLS 1.2 in your environment for Microsoft Entra TLS 1.1 and 1.0 deprecation](https://learn.microsoft.com/en-us/troubleshoot/entra/entra-id/ad-dmn-services/enable-support-tls-environment)
- [TLS 1.2 enforcement for Microsoft Entra Connect](https://learn.microsoft.com/en-us/entra/identity/hybrid/connect/reference-connect-tls-enforcement)
