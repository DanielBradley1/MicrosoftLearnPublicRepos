<!-- Source: https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-disruptionandresponseevents-table -->
<!-- Sitemap-Last-Modified: 2026-01-04 -->

# DisruptionAndResponseEvents

The `DisruptionAndResponseEvents` table in the [advanced hunting](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-overview) contains information about [automatic attack disruption](https://learn.microsoft.com/en-us/defender-xdr/automatic-attack-disruption) and [predictive shielding](https://learn.microsoft.com/en-us/defender-xdr/shield-predict-threats) events in Microsoft Defender. These events include both block and policy application events related to triggered attack disruption policies, and automatic actions that were taken across related workloads.

Users can use this table to increase their visibility and awareness of active, complex attacks disrupted by automatic attack disruption. Understanding the scope of even complex attacks, their context, impact, and why disruption actions were taken, can help users make better and faster decisions and allocate resources more efficiently.

## DisruptionAndResponseEvents table considerations

The `DisruptionAndResponseEvents` table:

- Is populated by records from various Microsoft security services. If your organization hasn't deployed the service in Microsoft Defender, queries that use the table aren't going to work or return complete results. For more information about how to deploy supported services in the Defender portal, read [Deploy supported services](https://learn.microsoft.com/en-us/defender-xdr/deploy-supported-services).
- Doesn't contain the execution of actions like contain user or disable user. The table only reflects the outcomes of these actions, such as blocked logon attempts or policy applications. For the full context of these actions, the [Action Center](https://learn.microsoft.com/en-us/defender-xdr/m365d-action-center) logs all events.
- Exposes only Defender for Endpoint-based controls.

## Schema reference

Use this reference to construct queries that return information from this table.

Tip

For detailed information about the events types \(`ActionType` values\) supported by this table, see [ActionType values](#actiontype-values).

For information on other tables in the advanced hunting schema, [see the advanced hunting reference](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-schema-tables).

| Column name | Data type | Description |
| --- | --- | --- |
| `Timestamp` | `datetime` | Date and time when the event was recorded |
| `ActionType` | `string` | Type of disruption action taken  <br>**Tip**: For more information, see [ActionType values](#actiontype-values). |
| `DeviceId` | `string` | Unique identifier for the device that reported the event; the reporting device can be the one that blocked the access, the compromised device itself, or even a different device that is aware of the attack |
| `SourceDeviceId` | `string` | Unique identifier for the device that the attack originated from |
| `TargetDeviceId` | `string` | Unique identifier for the device that was targeted or attacked |
| `TargetDeviceName ` | `string` | Name of the device that was targeted or attacked |
| `TargetDomainName ` | `string` | Domain name of the device that was targeted or attacked |
| `DeviceName` | `string` | Name of the device that reported the event; the reporting device can be the one that blocked the access, the compromised device itself, or even a different device that is aware of the attack |
| `DomainName` | `string` | Domain name that the device that reported the event is joined to; the reporting device can be the one that blocked the access, the compromised device itself, or even a different device that is aware of the attack |
| `InitiatingProcessId` | `integer` | Process ID \(PID\) of the process that triggered that block action, based on the perspective of the reporting device |
| `InitiatingProcessFileName` | `string` | Name of the process that triggered the block action, based on the perspective of the reporting device |
| `SourceUserSid` | `string` | The security identifier of the account conducting the malicious activity |
| `SourceUserName` | `string` | The user name of the account conducting the malicious activity |
| `SourceUserDomainName` | `string` | The domain name of the account conducting the malicious activity |
| `SourceIpAddress` | `string` | IP address where the attacker communication originated from and was blocked by automatic attack disruption |
| `SourcePort` | `integer` | Port where the attacker communication originated from |
| `IpAddress` | `string` | IP address that the attacker attempted to access |
| `Port` | `string` | Port that the attacker attempted to access |
| `SourceDeviceName` | `string` | Host name of the device where the attack originated from |
| `SourceDomainName` | `string` | Domain name of the device where the attack originated from |
| `AuthenticationProtocol` | `string` | Authentication protocol that the compromised user used to sign in; possible values: Undefined, NTLM, Kerberos |
| `Service` | `string` | Name of the service the attacker attempted to use, if the attacker signed in using Kerberos or NTLM; for example: SMB, HTTP, cifs, SMB, host, ldap, SMB, krbtgt |
| `InterfaceUuid` | `string` | Unique identifier \(UUID\) for the Remote Procedure Call \(RPC\) interface that the attacker attempted to access |
| `InterfaceFriendlyName` | `string` | Friendly name of the interface represented by the interface UUID |
| `FileName` | `string` | Name of the file that the attacker attempted to access |
| `ShareName` | `string` | Name of the share location that the attacker attempted to access |
| `LogonType` | `string` | Type of logon session the user attempted; possible values: interactive, remote interactive \(RDP\), network, batch job, service |
| `LogonId ` | `long` | Identifier for a logon session; this is unique on the same device only between restarts |
| `SessionId ` | `long` | Unique number assigned to a user by a website's server for the duration of the visit or session |
| `CompromisedAccountCount` | `integer` | Number of compromised accounts that are part of the policy |
| `PolicyId` | `string` | Unique identifier for the policy |
| `PolicyName` | `string` | Name of the policy |
| `PolicyVersion` | `string` | Version of the policy |
| `PolicyHash` | `string` | Unique hash of the policy |
| `DataSources` | `string` | Products or services that provided information for the event; for example: Microsoft Defender for Endpoint |
| `IsPolicyOn` | `boolean` | Indicates the current state of the policy on the device at the time of the disruption event; possible values: true \(the policy is on, therefore it was applied or enforced\), false \(the policy was turned off or revoked from the device\) |
| `ReportType` | `string` | The nature and impact level of the reported event; possible values: Prevented \(the action, such as a connection or authentication attempt, was fully blocked before execution\), Blocked \(an active connection or session was forcibly terminated, with partial impact on the device\), PolicyUpdated \(the client received and possibly applied a new policy\) |

### ActionType values

| Action | Description | Defense strategy |
| --- | --- | --- |
| `ContainedRestrictedUserSmbFileOpenBlocked` | Logs an event when a user who is a member of a restricted user group attempts to open a specific Server Message Block \(SMB\) shared file and the action is blocked. | Automatic attack disruption |
| `ContainedUserLogonBlocked` | Logs an event when a contained user's logon attempt is blocked. | Automatic attack disruption |
| `ContainedUserLogonBlockedByDomainController` | Logs an event when a user's logon attempt to a device in the domain is blocked by the Domain Controller due to containment policies. | Automatic attack disruption |
| `ContainedUserRemoteDesktopSessionDisconnected` | Logs an event when a contained user's remote desktop session is forcibly disconnected using `WTSDisconnectSession`. | Automatic attack disruption |
| `ContainedUserRemoteDesktopSessionStopped` | Logs an event when a contained user's remote desktop session is stopped using `WTSLogoffSession`. | Automatic attack disruption |
| `ContainedUserRpcAccessBlocked` | Logs an event when a contained user's attempt to access a resource via RPC is blocked. | Automatic attack disruption |
| `ContainedUserSmbFileOpenBlocked` | Logs an event when a contained user attempts to open an SMB shared file and the attempt is blocked. | Automatic attack disruption |
| `ContainedUserSmbFileOpenBlockedAggregation` | Same as `ContainedUserSmbFileOpenBlocked`, but aggregated for cases where the same contained user accesses more than 10 files within a one-minute window. | Automatic attack disruption |
| `ContainedUserSmbSessionStopped` | Logs an event when an SMB session initiated by a contained user is forcibly ended. | Automatic attack disruption |
| `GroupPolicyAccessBlocked` | Blocks access to the **SYSVOL** directory, preventing the device from pulling group policy updates. | Predictive shielding |
| `SafeBootBlocked` | Prevents the device from being rebooted into safe mode. | Predictive shielding |
| `SafeBootGuardPolicyApplied` | Applies the Safe Boot Guard policy to the device. | Predictive shielding |
| `SafeBootGuardPolicyRemoved` | Removes the Safe Boot Guard policy from the device. | Predictive shielding |
| `GroupPolicyHardeningPolicyApplied` | Applies the Group Policy Hardening policy to the device. | Predictive shielding |
| `GroupPolicyHardeningPolicyRemoved` | Removes the Group Policy Hardening policy from the device. | Predictive shielding |

## Related topics

- [Advanced hunting overview](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-overview)
- [Learn the query language](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-query-language)
- [Use shared queries](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-shared-queries)
- [Hunt across devices, emails, apps, and identities](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-query-emails-devices)
- [Understand the schema](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-schema-tables)
- [Apply query best practices](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-best-practices)
