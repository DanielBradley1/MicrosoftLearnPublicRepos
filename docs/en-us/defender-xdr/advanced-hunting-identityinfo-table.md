<!-- Source: https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-identityinfo-table -->
<!-- Sitemap-Last-Modified: 2025-12-22 -->

# IdentityInfo

The `IdentityInfo` table in the [advanced hunting](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-overview) schema contains information about user accounts obtained from various services, including Microsoft Entra ID. Use this reference to construct queries that return information from this table.

This table was renamed from `AccountInfo`. During renames, all queries saved in the portal are automatically updated. Check queries you saved elsewhere.

Microsoft Sentinel uses a slightly expanded version of this table in Log Analytics. For more information, see [Microsoft Sentinel UEBA reference](https://learn.microsoft.com/en-us/azure/sentinel/ueba-reference#identityinfo-table).

For information on other tables in the advanced hunting schema, [see the advanced hunting reference](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-schema-tables).

The following schema is the unified `IdentityInfo` schema that streamlines a similar table in Microsoft Sentinel's log analytics and in Microsoft Defender advanced hunting. The complete set of columns is available for Defender portal users who onboarded Microsoft Sentinel and turned on the User and Entity Behavior Analytics \(UEBA\) service.

Defender portal users who don't onboard a Microsoft Sentinel workspace that has the UEBA service turned on can't view UEBA-specific columns. Read [UEBA-specific columns](#ueba-specific-columns).

This advanced hunting table is populated by records from Microsoft Defender for Identity or Microsoft Sentinel and Microsoft Entra ID. If your organization doesn't deploy the service in Microsoft Defender, queries that use the table don't work or return any results. For more information about how to deploy Defender for Identity in the Defender portal, read [Deploy supported services](https://learn.microsoft.com/en-us/defender-xdr/deploy-supported-services).

| Column name | Data type | Description |
| --- | --- | --- |
| `Timestamp` [\*](#mdi-only) | `datetime` | The date and time that the line was written to the database.  <br>  <br>This is used when there are multiple lines for each identity, such as when a change is detected, or if 24 hours have passed since the last database line was added. |
| `ReportId` [\*](#mdi-only) | `string` | Unique identifier for the event |
| `AccountObjectId` | `string` | Unique identifier for the account in Microsoft Entra ID |
| `AccountUpn` | `string` | User principal name \(UPN\) of the account |
| `OnPremSid` | `string` | On-premises security identifier \(SID\) of the account |
| `AccountDisplayName` | `string` | Name of the account user displayed in the address book. Typically a combination of a given or first name, a middle initial, and a last name or surname. |
| `AccountName` | `string` | User name of the account |
| `AccountDomain` [\*](#mdi-only) | `string` | Domain of the account |
| `CriticalityLevel` | `int` | The criticality score of the account |
| `Type` [\*](#mdi-only) | `string` | Type of identity; possible values: User, ServiceAccount |
| `DistinguishedName` [\*](#mdi-only) | string | The user's [distinguished name](https://learn.microsoft.com/en-us/previous-versions/windows/desktop/ldap/distinguished-names) |
| `CloudSid` | `string` | Cloud security identifier of the account |
| `GivenName` | `string` | Given name or first name of the account user |
| `Surname` | `string` | Surname, family name, or last name of the account user |
| `Department` | `string` | Name of the department that the account user belongs to |
| `JobTitle` | `string` | Job title of the account user |
| `EmailAddress` | `string` | SMTP address of the account |
| `SipProxyAddress` | `string` | Voice over IP \(VOIP\) session initiation protocol \(SIP\) address of the account |
| `Address` | `string` | Address of the account user |
| `City` | `string` | City where the account user is located |
| `Country` | `string` | Country/Region where the account user is located |
| `IsAccountEnabled` | `boolean` | Indicates whether the account is enabled or not |
| `Manager` [\*](#mdi-only) | `string` | The listed manager of the account user |
| `Phone` [\*](#mdi-only) | `string` | The listed phone number of the account user |
| `CreatedDateTime` [\*](#mdi-only) | `datetime` | Date and time when the account user was created |
| `ChangeSource` [\*](#mdi-only) | `string` | Identifies which identity provider or process triggered the addition of the new row. For example, the `System-UserPersistence` value is used for any rows added by an automated process. |
| `BlastRadius` [\*\*](#sentinel) | `string` | A calculation based on the position of the user in the org tree and the user's Microsoft Entra roles and permissions; possible values: Low, Medium, High |
| `CompanyName` [\*\*](#sentinel) | `string` | Name of the company for which the user works |
| `DeletedDateTime` [\*\*](#sentinel) | `datetime` | Date and time when the user account was deleted |
| `EmployeeId` [\*\*](#sentinel) | `string` | Employee identifier assigned to the user by the organization |
| `OtherMailAddresses` [\*\*](#sentinel) | `dynamic` | Additional email addresses of the user account |
| `RiskLevel` | `string` | Microsoft Entra ID risk level of the user account; possible values: Low, Medium, High |
| `RiskLevelDetails` | `string` | Details regarding the Microsoft Entra ID risk level |
| `State` [\*\*](#sentinel) | `string` | State where the sign-in occurred, if available |
| `Tags` [\*](#mdi-only) | `dynamic` | Tags assigned to the account user by Defender for Identity |
| `AssignedRoles` [\*](#mdi-only) | `dynamic` | For identities from Microsoft Entra-only, the roles assigned to the account user |
| `PrivilegedEntraPimRoles` \(Preview\) [\*\*\*](#mdi) | `dynamic` | A snapshot of privileged role assignment schedules and eligibility schedules for the account as maintained by Microsoft Entra Privileged Identity Management \(excluding activated assignments\) |
| `TenantId` | `string` | Unique identifier representing your organization's instance of Microsoft Entra ID |
| `SourceSystem` [\*](#mdi-only) | `string` | The source system for the record |
| `OnPremObjectId` | `string` | Active Directory object ID of the user |
| `TenantMembershipType` | `string` | User type in Microsoft Entra ID; possible values: Guest, Member |
| `RiskStatus` [\*\*](#sentinel) | `string` | Status of the user's risk; possible values: None, ConfirmedSafe, Remediated, Dismissed, AtRisk, ConfirmedCompromised, UnknownFutureValue |
| `UserAccountControl` | `string` | Security attributes of the user account in the Active Directory domain |
| `IdentityEnvironment` | `string` | Environment where the identity is used; possible values: CloudOnly, Hybrid, On-premises |
| `SourceProviders` | `dynamic` | Source providers of the accounts for the identity; possible values: ActiveDirectory, EntraID, Okta |
| `GroupMembership` [\*\*](#sentinel) | `dynamic` | Microsoft Entra ID groups where the user account is a member |

\* Available only for tenants with Microsoft Defender for Identity, Microsoft Defender for Cloud Apps, or Microsoft Defender for Endpoint P2 licensing.  
\*\* Available only for tenants with Microsoft Sentinel. For more information about the freshness and limitations of these columns, see [Microsoft Sentinel UEBA reference](https://learn.microsoft.com/en-us/azure/sentinel/ueba-reference#identityinfo-table)  
\*\*\* Available only for tenants with Microsoft Defender for Identity.

## UEBA-specific columns

If you use the Microsoft Defender portal but don't onboard a Microsoft Sentinel workspace with the UEBA service turned on, the following columns aren't available in your `IdentityInfo` table:

- `BlastRadius`
- `CompanyName`
- `DeletedDateTime`
- `EmployeeId`
- `OtherMailAddresses`
- `Tags`
- `State`
- `GroupMembership`
- `RiskStatus`

For more information about UEBA, see [Advanced threat detection with User and Entity Behavior Analytics \(UEBA\) in Microsoft Sentinel](https://learn.microsoft.com/en-us/azure/sentinel/identify-threats-with-entity-behavior-analytics). For more information about the different data sources in UEBA, see [Microsoft Sentinel UEBA reference](https://learn.microsoft.com/en-us/azure/sentinel/ueba-reference).

## Related articles

- [Advanced hunting overview](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-overview)
- [Learn the query language](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-query-language)
- [Use shared queries](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-shared-queries)
- [Hunt across devices, emails, apps, and identities](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-query-emails-devices)
- [Understand the schema](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-schema-tables)
- [Apply query best practices](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-best-practices)

Tip

Do you want to learn more? Engage with the Microsoft Security community in our Tech Community: [Microsoft Defender XDR Tech Community](https://techcommunity.microsoft.com/t5/microsoft-365-defender/bd-p/MicrosoftThreatProtection).
