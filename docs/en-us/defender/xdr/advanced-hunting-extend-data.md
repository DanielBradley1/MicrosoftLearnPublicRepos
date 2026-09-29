<!-- Source: https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-extend-data -->
<!-- Sitemap-Last-Modified: 2026-08-11 -->

# Extend advanced hunting coverage with the right settings

## Configure data sources for advanced hunting

[Advanced hunting](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-overview) relies on data from various sources. These sources include your devices, your Office 365 workspaces, Microsoft Entra ID, and Microsoft Defender for Identity. To get the most complete data, make sure you have the correct settings in each data source.

## Enable advanced security auditing on Windows devices

Turn on these advanced auditing settings to ensure you get data about activities on your devices, including local account management, local security group management, and service creation.

| Data | Description | Schema table | How to configure |
| --- | --- | --- | --- |
| Account management | Events captured as various `ActionType` values indicating local account creation, deletion, and other account-related activities | [DeviceEvents](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-deviceevents-table) | - Deploy an advanced security audit policy: [Audit User Account Management](https://learn.microsoft.com/en-us/windows/security/threat-protection/auditing/audit-user-account-management)  <br>- [Learn about advanced security audit policies](https://learn.microsoft.com/en-us/windows/security/threat-protection/auditing/advanced-security-auditing) |
| Security group management | Events captured as various `ActionType` values indicating local security group creation and other local group management activities | [DeviceEvents](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-deviceevents-table) | - Deploy an advanced security audit policy: [Audit Security Group Management](https://learn.microsoft.com/en-us/windows/security/threat-protection/auditing/audit-security-group-management)  <br>- [Learn about advanced security audit policies](https://learn.microsoft.com/en-us/windows/security/threat-protection/auditing/advanced-security-auditing) |
| Service installation | Events captured with the `ActionType` value `ServiceInstalled`, indicating that a service has been created | [DeviceEvents](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-deviceevents-table) | - Deploy an advanced security audit policy: [Audit Security System Extension](https://learn.microsoft.com/en-us/windows/security/threat-protection/auditing/audit-security-system-extension)  <br>- [Learn about advanced security audit policies](https://learn.microsoft.com/en-us/windows/security/threat-protection/auditing/advanced-security-auditing) |

## Install the Microsoft Defender for Identity sensor on the domain controller

If you're running Active Directory on premises, you need to install the Microsoft Defender for Identity sensor on the domain controller to get data for Microsoft Defender for Identity. When installed and properly configured, data from on-premises Active Directory also feeds into advanced hunting through Microsoft Defender for Identity and provides a more holistic picture of identity information and events in your network. Data collected by the Defender for Identity sensor also enhances the ability of Microsoft Defender for Identity to generate relevant alerts that are also covered by advanced hunting.

| Data | Description | Schema table | How to configure |
| --- | --- | --- | --- |
| Domain controller | Data from on-premises Active Directory sent to Microsoft Defender for Identity, enriching identity-related information, such as account details, logon activity, and Active Directory queries | Multiple tables, including [IdentityInfo](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-identityinfo-table), [IdentityLogonEvents](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-identitylogonevents-table), and [IdentityQueryEvents](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-identityqueryevents-table) | - [Install the Microsoft Defender for Identity sensor](https://learn.microsoft.com/en-us/azure-advanced-threat-protection/install-atp-step4)  <br>- [Turn on relevant Windows Events](https://learn.microsoft.com/en-us/azure-advanced-threat-protection/configure-event-collection) |

Note

Some tables in this article might not be available in Microsoft Defender for Endpoint. [Turn on Microsoft Defender XDR](https://learn.microsoft.com/en-us/defender-xdr/m365d-enable) to hunt for threats using more data sources. You can move your advanced hunting workflows from Microsoft Defender for Endpoint to Microsoft Defender XDR by following the steps in [Migrate advanced hunting queries from Microsoft Defender for Endpoint](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-migrate-from-mde).

## Related content

- [Advanced hunting overview](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-overview)
- [Understand the schema](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-schema-tables)

Tip

Do you want to learn more? Engage with the Microsoft Security community in our Tech Community: [Microsoft Defender XDR Tech Community](https://techcommunity.microsoft.com/t5/microsoft-365-defender/bd-p/MicrosoftThreatProtection).
