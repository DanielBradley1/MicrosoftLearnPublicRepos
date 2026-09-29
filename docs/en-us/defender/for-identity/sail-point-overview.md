<!-- Source: https://learn.microsoft.com/en-us/defender-for-identity/sail-point-overview -->
<!-- Sitemap-Last-Modified: 2026-03-26 -->

# How Microsoft Defender for Identity protects your SailPoint Identity Security Cloud accounts \(Preview\)

Microsoft Defender for Identity helps protect your on-premises Active Directory and Microsoft Entra ID environments from advanced threats. Connecting SailPoint Identity Security Cloud with Microsoft Defender for Identity \(MDI\) gives you the ability to detect, investigate, and respond to identity-based threats across both cloud and on-premises infrastructures.

## What you can do after connecting SailPoint Identity Security Cloud to Microsoft Defender for Identity

After you connect SailPoint Identity Security Cloud, Microsoft Defender for Identity provides the following capabilities:

| Capability | Description |
| --- | --- |
| View SailPoint accounts in the identity inventory | - Adds SailPoint Identity Security Cloud accounts into the identity inventory and correlates them with identities from on-premises, Active Directory and Microsoft Entra ID. |
| Improve SailPoint security posture | Evaluates SailPoint Identity Security Cloud accounts for security risks such as stale privileged accounts and excessive privileged role assignments, and generates posture recommendations. Example recommendations include:  <br>- Change password for SailPoint Identity Security Cloud privileged user accounts  <br>- Remove stale SailPoint Identity Security Cloud privileged accounts  <br>- Limit the number of SailPoint Identity Security Cloud accounts with system admin role  <br>- High number of SailPoint Identity Security Cloud accounts with a privileged role assigned  <br>- Assign multifactor authentication for SailPoint privileged user accounts |
| Use advanced hunting to investigate SailPoint identities and their related activities | The [IdentityInfo](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-identityinfo-table) and the [IdentityEvents](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-identityevents-table) advanced hunting tables include inventory and event data from SailPoint Identity Security Cloud for investigation. |
| Take remediation actions | If an identity is determined to be at risk, the following remediation actions can be taken from within the Microsoft Defender portal:  <br>- Disable user in SailPoint Identity Security Cloud  <br>- Enable user in SailPoint Identity Security Cloud |

## Next steps

- [Connect SailPoint Identity to Microsoft Defender for Identity \(Preview\)](https://learn.microsoft.com/en-us/defender-for-identity/connect-sail-point).
