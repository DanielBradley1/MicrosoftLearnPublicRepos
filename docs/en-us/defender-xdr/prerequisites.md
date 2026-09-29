<!-- Source: https://learn.microsoft.com/en-us/defender-xdr/prerequisites -->
<!-- Sitemap-Last-Modified: 2026-08-07 -->

# Microsoft Defender XDR prerequisites

Learn about licensing and other requirements for provisioning and using [Microsoft Defender](https://learn.microsoft.com/en-us/defender-xdr/microsoft-365-defender).

## Licensing requirements

Microsoft Defender natively correlates Microsoft security products' signals, providing security operations teams a single pane of glass to detect, investigate, respond, and protect your assets. These signals are dependent on the license that you have and the access provisioned to you.

Any of these licenses give you access to Microsoft Defender features via the Microsoft Defender portal without any additional cost:

- Microsoft 365 E5 or A5
- Microsoft 365 E3 with the Microsoft Defender Suite add-on
- Microsoft 365 E3 with the Enterprise Mobility + Security E5 add-on
- Microsoft 365 A3 with the Microsoft 365 A5 Security add-on
- Windows 10 Enterprise E5 or A5
- Windows 11 Enterprise E5 or A5
- Enterprise Mobility + Security \(EMS\) E5 or A5
- Office 365 E5 or A5
- Microsoft Defender for Endpoint
- [Microsoft Defender for IoT - Enterprise IoT protection](https://learn.microsoft.com/en-us/defender-for-iot/enterprise-iot-licenses#enterprise-iot-licenses) \(includes protection for enterprise IoT devices with the Microsoft 365 E5 \(ME5\) or E5 Security license\)
- Microsoft Defender for Identity
- Microsoft Defender for Cloud Apps or [Cloud App Discovery](https://learn.microsoft.com/en-us/defender-cloud-apps/editions-cloud-app-security-aad)
- Microsoft Defender for Office 365 \(Plan 2\)
- Microsoft 365 Business Premium
- Microsoft Defender for Business

For more information, [view the Microsoft 365 Enterprise service plans](https://www.microsoft.com/licensing/product-licensing/microsoft-365-enterprise).

Note

- Automatic attack disruption requires Microsoft Defender for Endpoint Plan 2. For more information, see [Configure automatic attack disruption capabilities](https://learn.microsoft.com/en-us/defender-xdr/configure-attack-disruption).
- Threat analytics also requires Defender for Endpoint Plan 2. For more information, see [Threat analytics in Microsoft Defender](https://learn.microsoft.com/en-us/defender-xdr/threat-analytics).

> Don't have license yet? [Try or buy a Microsoft 365 subscription](https://learn.microsoft.com/en-us/microsoft-365/commerce/try-or-buy-microsoft-365)

### Check your existing licenses

Go to Microsoft 365 admin center \([admin.microsoft.com](https://admin.microsoft.com/)\) to view your existing licenses. In the admin center, go to **Billing** > **Licenses**.

Note

You need to be assigned either the **Billing admin** or higher [role in Microsoft Entra ID](https://learn.microsoft.com/en-us/azure/active-directory/roles/permissions-reference) to be able to see license information. If you encounter access problems, contact a Global Administrator.

## Required permissions

You must at least be a **security administrator** in Microsoft Entra ID to turn on Microsoft Defender. For the list of roles required to use Microsoft Defender and information on how access to data is regulated, read about [managing access to Microsoft Defender](https://learn.microsoft.com/en-us/defender-xdr/m365d-permissions).

Important

Microsoft recommends that you use roles with the fewest permissions. Using lower permissioned accounts helps improve security for your organization. Global Administrator is a highly privileged role that should be limited to emergency scenarios when you can't use an existing role.

## Browser requirements

Access Microsoft Defender in the Microsoft Defender portal using Microsoft Edge, Internet Explorer 11, or any HTML 5 compliant web browser.

## Availability to US GCC, GCC High, and other US government institutions

For information related to US Government customers, see [Microsoft Defender for US Government customers](https://learn.microsoft.com/en-us/defender-xdr/usgov).

Currently, the Microsoft Defender for Office 365 integration into the unified Microsoft Defender features are not available to customers in the following Office 365 datacenter locations:

- Norway
- South Africa
- United Arab Emirates
- Sweden
- Singapore

## Related articles

- [Microsoft Defender overview](https://learn.microsoft.com/en-us/defender-xdr/microsoft-365-defender)
- [Turn on Microsoft Defender XDR](https://learn.microsoft.com/en-us/defender-xdr/m365d-enable)
- [Manage access and permissions](https://learn.microsoft.com/en-us/defender-xdr/m365d-permissions)

Tip

Do you want to learn more? Engage with the Microsoft Security community in our Tech Community: [Microsoft Defender XDR Tech Community](https://techcommunity.microsoft.com/t5/microsoft-365-defender/bd-p/MicrosoftThreatProtection).
