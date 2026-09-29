<!-- Source: https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-behaviorentities-table -->
<!-- Sitemap-Last-Modified: 2026-01-12 -->

# BehaviorEntities \(Preview\)

The `BehaviorEntities` table in the [advanced hunting](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-overview) schema contains information about entities \(file, process, device, user, and others\) that are involved in a behavior in [Microsoft Defender for Cloud Apps](https://learn.microsoft.com/en-us/defender-cloud-apps/what-is-defender-for-cloud-apps?toc=%2Fdefender-xdr%2Ftoc.json&bc=%2Fdefender-xdr%2Fbreadcrumb%2Ftoc.json) and [User and Entity Behavior Analytics \(UEBA\)](https://learn.microsoft.com/en-us/azure/sentinel/identify-threats-with-entity-behavior-analytics). Use this reference to construct queries that return information from this table.

Important

The `BehaviorEntities` table is in preview and is not available for GCC. The information here may be substantially modified before it's commercially released. Microsoft makes no warranties, express or implied, with respect to the information provided here. Have feedback to share? Fill out our [feedback form](https://forms.office.com/r/x0mX5hBkGu).

**Behaviors** are a type of data in Microsoft Defender XDR based on one or more raw events. Behaviors provide contextual insight into events and can, but not necessarily, indicate malicious activity. For more information, see the following articles:

- [Investigate behaviors with advanced hunting](https://learn.microsoft.com/en-us/defender-cloud-apps/behaviors)
- [Translate raw security logs to behavioral insights using UEBA behaviors in Microsoft Sentinel](https://learn.microsoft.com/en-us/azure/sentinel/entity-behaviors-layer)

This advanced hunting table is populated by records from both Defender for Cloud Apps and UEBA. If your organization doesn't deploy these services in Microsoft Defender, queries that use the table won't work or return any results. For more information about how to deploy services in Defender, see [Deploy supported services](https://learn.microsoft.com/en-us/defender-xdr/deploy-supported-services).

To make sure Defender for Cloud Apps and UEBA data populate the `BehaviorEntities` table, follow the instructions in the following articles:

- [Connect Microsoft 365 to Microsoft Defender for Cloud Apps](https://learn.microsoft.com/en-us/defender-cloud-apps/protect-office-365#prerequisites)
- [Enable the UEBA behaviors layer](https://learn.microsoft.com/en-us/azure/sentinel/entity-behaviors-layer#enable-the-ueba-behaviors-layer)

For information on other tables in the advanced hunting schema, [see the advanced hunting reference](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-schema-tables).

| Column name | Data type | Description |
| --- | --- | --- |
| `Timestamp` | `datetime` | Date and time when the record was generated |
| `BehaviorId` | `string` | Unique identifier for the behavior |
| `Categories` | `string` | Type of threat indicator or breach activity identified by the behavior, as defined by the MITRE ATT&CK framework |
| `ServiceSource` | `string` | Product or service that identified the behavior |
| `DetectionSource` | `string` | Detection technology or sensor that identified the notable component or activity |
| `DataSources` | `string` | Products or services that provided information for the behavior |
| `EntityType` | `string` | Type of object, such as a file, a process, a device, or a user |
| `EntityRole` | `string` | Indicates whether the entity is impacted or merely related |
| `DetailedEntityRole` | `string` | The roles of the entity in the behavior |
| `FileName` | `string` | Name of the file that the behavior applies to |
| `FolderPath` | `string` | Folder containing the file that the behavior applies to |
| `SHA1` | `string` | SHA-1 of the file that the behavior applies to |
| `SHA256` | `string` | SHA-256 of the file that the behavior applies to |
| `FileSize` | `long` | Size, in bytes, of the file that the behavior applies to |
| `ThreatFamily` | `string` | Malware family that the suspicious or malicious file or process has been classified under |
| `RemoteIP` | `string` | IP address that was being connected to |
| `RemoteUrl` | `string` | URL or fully qualified domain name \(FQDN\) that was being connected to |
| `AccountName` | `string` | User name of the account |
| `AccountDomain` | `string` | Domain of the account |
| `AccountSid` | `string` | Security Identifier \(SID\) of the account |
| `AccountObjectId` | `string` | Unique identifier for the account in Microsoft Entra ID |
| `CloudPlatform ` | `string` | The cloud platform that the resource belongs to, can be Azure, Amazon Web Services, or Google Cloud Platform |
| `CloudResourceType ` | `string` | Type of cloud resource |
| `CloudResourceId` | `string` | Unique identifier of the cloud resource accessed |
| `CloudSubscriptionId ` | `string` | Unique identifier of the cloud service subscription |
| `AccountUpn` | `string` | User principal name \(UPN\) of the account |
| `DeviceId` | `string` | Unique identifier for the device in the service |
| `DeviceName` | `string` | Fully qualified domain name \(FQDN\) of the device |
| `LocalIP` | `string` | IP address assigned to the local device used during communication |
| `NetworkMessageId` | `string` | Unique identifier for the email, generated by Microsoft 365 |
| `EmailSubject` | `string` | Subject of the email |
| `EmailClusterId` | `string` | Identifier for the group of similar emails clustered based on heuristic analysis of their contents |
| `Application` | `string` | Application that performed the recorded action |
| `ApplicationId` | `int` | Unique identifier for the application |
| `OAuthApplicationId` | `string` | Unique identifier of the third-party OAuth application |
| `ProcessCommandLine` | `string` | Command line used to create the new process |
| `RegistryKey` | `string` | Registry key that the recorded action was applied to |
| `RegistryValueName` | `string` | Name of the registry value that the recorded action was applied to |
| `RegistryValueData` | `string` | Data of the registry value that the recorded action was applied to |
| `AdditionalFields` | `string` | Additional information about the behavior |
| `ActionType` | `string` | Type of behavior |

## Related topics

- [Advanced hunting overview](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-overview)
- [Learn the query language](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-query-language)
- [Use shared queries](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-shared-queries)
- [Hunt across devices, emails, apps, and identities](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-query-emails-devices)
- [Understand the schema](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-schema-tables)
- [Apply query best practices](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-best-practices)

Tip

Do you want to learn more? Engage with the Microsoft Security community in our Tech Community: [Microsoft Defender XDR Tech Community](https://techcommunity.microsoft.com/t5/microsoft-365-defender/bd-p/MicrosoftThreatProtection).
