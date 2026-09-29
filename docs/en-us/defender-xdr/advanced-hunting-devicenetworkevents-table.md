<!-- Source: https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-devicenetworkevents-table -->
<!-- Sitemap-Last-Modified: 2026-06-22 -->

# DeviceNetworkEvents

The `DeviceNetworkEvents` table in the [advanced hunting](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-overview) schema contains information about network connections and related events. Use this reference to construct queries that return information from this table.

Tip

For detailed information about the events types \(`ActionType` values\) supported by a table, use the built-in schema reference available in the Defender portal.

This advanced hunting table is populated by records from Microsoft Defender for Endpoint. If your organization hasn't deployed the service in Microsoft Defender, queries that use the table aren't going to work or return any results. For more information about how to deploy Defender for Endpoint in the Defender portal, read [Deploy supported services](https://learn.microsoft.com/en-us/defender-xdr/deploy-supported-services).

For information on other tables in the advanced hunting schema, [see the advanced hunting reference](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-schema-tables).

| Column name | Data type | Description |
| --- | --- | --- |
| `Timestamp` | `datetime` | Date and time when the event was recorded |
| `DeviceId` | `string` | Unique identifier for the device in the service |
| `DeviceName` | `string` | Fully qualified domain name \(FQDN\) of the device |
| `ActionType` | `string` | Type of activity that triggered the event. See the [in-portal schema reference](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-schema-tables?#get-schema-information-in-the-security-center) for details. |
| `RemoteIP` | `string` | IP address that was being connected to |
| `RemotePort` | `int` | TCP port on the remote device that was being connected to |
| `RemoteUrl` | `string` | URL or fully qualified domain name \(FQDN\) that was being connected to |
| `LocalIP` | `string` | Source IP, or the IP address where the communication came from |
| `LocalPort` | `int` | TCP port on the local device used during communication |
| `Protocol` | `string` | Protocol used during the communication |
| `LocalIPType` | `string` | Type of IP address, for example Public, Private, Reserved, Loopback, Teredo, FourToSixMapping, and Broadcast |
| `RemoteIPType` | `string` | Type of IP address, for example Public, Private, Reserved, Loopback, Teredo, FourToSixMapping, and Broadcast |
| `InitiatingProcessSHA1` | `string` | SHA-1 of the process \(image file\) that initiated the event |
| `InitiatingProcessSHA256` | `string` | SHA-256 of the process \(image file\) that initiated the event. This field is usually not populated — use the SHA1 column when available. |
| `InitiatingProcessMD5` | `string` | MD5 hash of the process \(image file\) that initiated the event |
| `InitiatingProcessFileName` | `string` | Name of the process file that initiated the event; if unavailable, the name of the process that initiated the event might be shown instead |
| `InitiatingProcessFileSize` | `long` | Size of the file that ran the process responsible for the event |
| `InitiatingProcessVersionInfoCompanyName` | `string` | Company name from the version information of the process \(image file\) responsible for the event |
| `InitiatingProcessVersionInfoProductName` | `string` | Product name from the version information of the process \(image file\) responsible for the event |
| `InitiatingProcessVersionInfoProductVersion` | `string` | Product version from the version information of the process \(image file\) responsible for the event |
| `InitiatingProcessVersionInfoInternalFileName` | `string` | Internal file name from the version information of the process \(image file\) responsible for the event |
| `InitiatingProcessVersionInfoOriginalFileName` | `string` | Original file name from the version information of the process \(image file\) responsible for the event |
| `InitiatingProcessVersionInfoFileDescription` | `string` | Description from the version information of the process \(image file\) responsible for the event |
| `InitiatingProcessId` | `long` | Process ID \(PID\) of the process that initiated the event |
| `InitiatingProcessCommandLine` | `string` | Command line used to run the process that initiated the event |
| `InitiatingProcessCreationTime` | `datetime` | Date and time when the process that initiated the event was started |
| `InitiatingProcessFolderPath` | `string` | Folder containing the process \(image file\) that initiated the event |
| `InitiatingProcessParentFileName` | `string` | Name of the parent process that spawned the process responsible for the event |
| `InitiatingProcessParentId` | `long` | Process ID \(PID\) of the parent process that spawned the process responsible for the event |
| `InitiatingProcessParentCreationTime` | `datetime` | Date and time when the parent of the process responsible for the event was started |
| `InitiatingProcessAccountDomain` | `string` | Domain of the account that ran the process responsible for the event |
| `InitiatingProcessAccountName` | `string` | User name of the account that ran the process responsible for the event; if the device is registered in Microsoft Entra ID, the Entra ID user name of the account that ran the process responsible for the event might be shown instead |
| `InitiatingProcessAccountSid` | `string` | Security Identifier \(SID\) of the account that ran the process responsible for the event |
| `InitiatingProcessAccountUpn` | `string` | User principal name \(UPN\) of the account that ran the process responsible for the event; if the device is registered in Microsoft Entra ID, the Entra ID UPN of the account that ran the process responsible for the event might be shown instead |
| `InitiatingProcessAccountObjectId` | `string` | Microsoft Entra object ID of the user account that ran the process responsible for the event |
| `InitiatingProcessIntegrityLevel` | `string` | Integrity level of the process that initiated the event. Windows assigns integrity levels to processes based on certain characteristics, such as if they were launched from an internet download. These integrity levels influence permissions to resources. |
| `InitiatingProcessTokenElevation` | `string` | Token type indicating the presence or absence of User Access Control \(UAC\) privilege elevation applied to the process that initiated the event |
| `ReportId` | `long` | Event identifier based on a repeating counter. To identify unique events, this column must be used in conjunction with the DeviceName and Timestamp columns. |
| `AppGuardContainerId` | `string` | Identifier for the virtualized container used by Application Guard to isolate browser activity |
| `AdditionalFields` | `string` | Additional information about the event in JSON array format |
| `InitiatingProcessSessionId` | `long` | Windows session ID of the initiating process |
| `IsInitiatingProcessRemoteSession` | `bool` | Indicates whether the initiating process was run under a remote desktop protocol \(RDP\) session \(true\) or locally \(false\) |
| `InitiatingProcessRemoteSessionDeviceName` | `string` | Device name of the remote device from which the initiating process's RDP session was initiated |
| `InitiatingProcessRemoteSessionIP` | `string` | IP address of the remote device from which the initiating process's RDP session was initiated |
| `InitiatingProcessUniqueId` | `string` | Unique identifier of the initiating process; this is equal to the Process Start Key in Windows devices |
| `LogonID` | `long` | A unique identifier for the user initiating the event, enabling attribution of network activity to the originating interactive user across privilege escalation and session transitions. This field is located inside AdditionalFields/InitiatingProcessPosixEffectiveUser |

## Related topics

- [Advanced hunting overview](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-overview)
- [Learn the query language](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-query-language)
- [Use shared queries](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-shared-queries)
- [Hunt across devices, emails, apps, and identities](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-query-emails-devices)
- [Understand the schema](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-schema-tables)
- [Apply query best practices](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-best-practices)

Tip

Do you want to learn more? Engage with the Microsoft Security community in our Tech Community: [Microsoft Defender XDR Tech Community](https://techcommunity.microsoft.com/t5/microsoft-365-defender/bd-p/MicrosoftThreatProtection).
