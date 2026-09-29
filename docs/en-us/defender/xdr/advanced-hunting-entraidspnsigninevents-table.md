<!-- Source: https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-entraidspnsigninevents-table -->
<!-- Sitemap-Last-Modified: 2026-08-03 -->

# EntraIdSpnSignInEvents

Important

On October 19, 2026, the `EntraIdSpnSignInEvents` table will replace [`AADSpnSignInEventsBeta`](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-aadspnsignineventsbeta-table). This change removes the latter's preview status and aligns it with the existing product branding. Both tables will coexist until `AADSpnSignInEventsBeta` is deprecated on that date.

All queries that use the `AADSpnSignInEventsBeta` table will be migrated automatically to `EntraIdSpnSignInEvents` on October 19, 2026. Your custom detections won't require any changes.

Important

Customers need to have a Microsoft Entra ID P2 license to collect and view activities for this table.

The `EntraIdSpnSignInEvents` table in the advanced hunting schema contains information about Microsoft Entra service principal and managed identity sign-ins. You can learn more about the different kinds of sign-ins in [Microsoft Entra sign-in activity reports - preview](https://learn.microsoft.com/en-us/azure/active-directory/reports-monitoring/concept-all-sign-ins).

Use this reference to construct queries that return information from the table.

For information on other tables in the advanced hunting schema, see [the advanced hunting reference](https://learn.microsoft.com/en-us/windows/security/threat-protection/microsoft-defender-atp/advanced-hunting-reference).

| Column name | Data type | Description |
| --- | --- | --- |
| `Timestamp` | `datetime` | Date and time when the record was generated |
| `Application` | `string` | Application that performed the recorded action |
| `ApplicationId` | `string` | Unique identifier for the application |
| `IsManagedIdentity` | `boolean` | Indicates whether the sign-in was initiated by a managed identity |
| `ErrorCode` | `int` | Contains the error code if a sign-in error occurs. To find a description of a specific error code, visit [https://aka.ms/AADsigninsErrorCodes](https://aka.ms/AADsigninsErrorCodes). |
| `CorrelationId` | `string` | Unique identifier of the sign-in event |
| `ServicePrincipalName` | `string` | Name of the service principal that initiated the sign-in |
| `ServicePrincipalId` | `string` | Unique identifier of the service principal that initiated the sign-in |
| `ResourceDisplayName` | `string` | Display name of the resource accessed. The display name can contain any character. |
| `ResourceId` | `string` | Unique identifier of the resource accessed |
| `ResourceTenantId` | `string` | Unique identifier of the tenant of the resource accessed |
| `IPAddress` | `string` | IP address assigned to the endpoint and used during related network communications |
| `Country` | `string` | Two-letter code indicating the country/region where the client IP address is geolocated |
| `State` | `string` | State where the sign-in occurred, if available |
| `City` | `string` | City where the account user is located |
| `Latitude` | `string` | The north to south coordinates of the sign-in location |
| `Longitude` | `string` | The east to west coordinates of the sign-in location |
| `RequestId` | `string` | Unique identifier of the request |
| `ReportId` | `string` | Unique identifier for the event |
| `IsConfidentialClient` | `boolean` | Indicates whether the sign-in was performed by a confidential client application |
| `GatewayJA4` | `string` | JA4 fingerprint derived from the TLS Client Hello request that identifies the client's TLS configuration |
| `SessionId` | `string` | Unique number assigned to a user by a website's server for the duration of the visit or session |
| `UserAgent` | `string` | User agent information from the web browser or other client application |
| `TenantId` | `string` | Unique identifier representing the organization's instance of Microsoft Entra ID |
| `Type` | `string` | Name of the table |
| `SourceSystem` | `string` | Source system for the record |
| `TimeGenerated` | `datetime` | Date and time when the record was generated |
| `UniqueTokenId` | `string` | Unique identifier for the token passed during sign-in, used to correlate the sign-in with the token request |

## Related articles

- [EntraIdSignInEvents](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-entraidsigninevents-table)
- [Advanced hunting overview](https://learn.microsoft.com/en-us/windows/security/threat-protection/microsoft-defender-atp/advanced-hunting-overview)
- [Learn the query language](https://learn.microsoft.com/en-us/windows/security/threat-protection/microsoft-defender-atp/advanced-hunting-query-language)
- [Understand the schema](https://learn.microsoft.com/en-us/windows/security/threat-protection/microsoft-defender-atp/advanced-hunting-schema-reference)

Tip

Do you want to learn more? Engage with the Microsoft Security community in our Tech Community: [Microsoft Defender XDR Tech Community](https://techcommunity.microsoft.com/t5/microsoft-365-defender/bd-p/MicrosoftThreatProtection).
