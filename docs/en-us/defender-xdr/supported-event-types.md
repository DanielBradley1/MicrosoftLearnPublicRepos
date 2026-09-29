<!-- Source: https://learn.microsoft.com/en-us/defender-xdr/supported-event-types -->
<!-- Sitemap-Last-Modified: 2024-11-05 -->

# Supported Microsoft Defender XDR streaming event types in event streaming API

**Applies to:**

- [Microsoft Defender XDR](https://learn.microsoft.com/en-us/defender-xdr/microsoft-365-defender)

Note

**Try our new APIs using MS Graph security API**. Find out more at: [Use the Microsoft Graph security API - Microsoft Graph \| Microsoft Learn](https://learn.microsoft.com/en-us/graph/api/resources/security-api-overview).

Important

Some information in this article relates to a prereleased product which may be substantially modified before it's commercially released. Microsoft makes no warranties, expressed or implied, with respect to the information provided here.

The Event Streaming API is constantly being expanded to support more event types. Learn which hunting tables are generally available, currently in public preview, or not yet supported.

## Hunting tables support status in Event Streaming API

The following table includes that status of support for tables in the streaming API, and is not inclusive of all AH schema. For a full list of the API see, [Learn the schema tables](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-schema-tables#learn-the-schema-tables).

Note

Streaming data is only available for columns or fields that are in general availability in Microsoft Defender.

| Table name | Status  <br>\(Commercial\) | GCC | GCC High | DoD |
| --- | --- | --- | --- | --- |
| **[AlertEvidence](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-alertevidence-table)** | GA | GA | GA | GA |
| **[AlertInfo](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-alertinfo-table)** | GA | GA | GA | GA |
| **[BehaviorEntities](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-behaviorentities-table)** | Not available | Not available | Not available | Not available |
| **[BehaviorInfo](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-behaviorinfo-table)** | Not available | Not available | Not available | Not available |
| **[CloudAppEvents](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-cloudappevents-table)** | GA | GA | GA | GA |
| **[DeviceEvents](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-deviceevents-table)** | GA | GA | GA | GA |
| **[DeviceFileCertificateInfo](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-devicefilecertificateinfo-table)** | GA | GA | GA | GA |
| **[DeviceFileEvents](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-devicefileevents-table)** | GA | GA | GA | GA |
| **[DeviceImageLoadEvents](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-deviceimageloadevents-table)** | GA | GA | GA | GA |
| **[DeviceInfo](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-deviceinfo-table)** | GA | GA | GA | GA |
| **[DeviceLogonEvents](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-devicelogonevents-table)** | GA | GA | GA | GA |
| **[DeviceNetworkEvents](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-devicenetworkevents-table)** | GA | GA | GA | GA |
| **[DeviceNetworkInfo](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-devicenetworkinfo-table)** | GA | GA | GA | GA |
| **[DeviceProcessEvents](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-deviceprocessevents-table)** | GA | GA | GA | GA |
| **[DeviceRegistryEvents](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-deviceregistryevents-table)** | GA | GA | GA | GA |
| **[EmailAttachmentInfo](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-emailattachmentinfo-table)** | GA | GA | GA | GA |
| **[EmailEvents](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-emailevents-table)** | GA | GA | GA | GA |
| **[EmailPostDeliveryEvents](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-emailpostdeliveryevents-table)** | GA | GA | GA | GA |
| **[EmailUrlInfo](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-emailurlinfo-table)** | GA | GA | GA | GA |
| **[IdentityLogonEvents](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-identitylogonevents-table)** | GA | GA | GA | GA |
| **[IdentityQueryEvents](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-identityqueryevents-table)** | GA | GA | GA | GA |
| **[IdentityDirectoryEvents](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-identitydirectoryevents-table)** | GA | GA | GA | GA |
| **[UrlClickEvents](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-urlclickevents-table)** | GA | GA | GA | GA |

## Related topics

[Use the Microsoft Graph security API - Microsoft Graph \| Microsoft Learn](https://learn.microsoft.com/en-us/graph/api/resources/security-api-overview)

Tip

Do you want to learn more? Engage with the Microsoft Security community in our Tech Community: [Microsoft Defender XDR Tech Community](https://techcommunity.microsoft.com/t5/microsoft-365-defender/bd-p/MicrosoftThreatProtection).
