<!-- Source: https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-synthetic-media-detection-events -->
<!-- Sitemap-Last-Modified: 2026-11-13 -->

# SyntheticMediaDetectionEvents

The `SyntheticMediaDetectionEvents` table in the [advanced hunting](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-overview) schema contains details about synthetic media \(deepfake\) detection events in Microsoft Teams in your organization.

This advanced hunting table is populated by records from Microsoft Defender for Office 365. If your organization hasn't deployed the service in Microsoft Defender, queries that use the table don't work or return any results. For more information about how to deploy Defender for Office 365 in the Defender portal, read [Deploy supported services](https://learn.microsoft.com/en-us/defender-xdr/deploy-supported-services).

Note

This table contains data only if you're using an approved detection engine: Microsoft or a third-party engine \(GetReal, Pindrop, Reality Defender, or Resemble AI\).

## Schema

For information on other tables in the advanced hunting schema, [see the advanced hunting reference](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-schema-tables).

| Column name | Data type | Description |
| --- | --- | --- |
| `DetectionId` | `string` | Unique identifier for this detection event |
| `Timestamp` | `datetime` | Date and time when the activity was recorded |
| `Severity` | `string` | Severity of the detection; possible values: High, Medium, or Low |
| `ConfidenceScore` | `real` | Indicates whether the synthetic media was likely used with harmful intent \(for example, impersonation, fraud, or social engineering\), rather than benign use \(AI-generated avatars or accessibility tools\) |
| `IsMalicious` | `boolean` | Indicates whether the synthetic media was likely used with harmful intent \(for example, impersonation, fraud, or social engineering\), rather than benign use \(AI-generated avatars or accessibility tools\) |
| `SourceType` | `string` | The Microsoft 365 application where the detection event occurred |
| `SourceId` | `string` | Unique identifier of the source \(for example, call ID for meetings or calls, network message ID for emails, and file ID for files\) |
| `SourceContextUrl` | `string` | URL of the source \(for example, the meeting URL or file URL\) |
| `SourceContextName` | `string` | Name of the source \(for example, the meeting, file, or email name\) |
| `SourceContextType` | `string` | Context of the source \(for example, scheduled meeting, ad hoc meeting, or recurring meeting\) |
| `DetectedUserIdType` | `string` | Type of identifier to interpret DetectedUserId; possible values: PSTN \(for phone number\), Enterprise, Consumer, or Bot |
| `DetectedUserDisplayName` | `string` | Display name of the user flagged as using synthetic media |
| `DetectionProviderName` | `string` | Name of the detection bot or application that identified the synthetic media |
| `Modality` | `string` | Type of content analyzed; possible values: Audio, Video, Multimodal, or Image |
| `IsRealTime` | `boolean` | Indicates whether the detection happened live during the session \(`true`\) or after as a post-session analysis \(`false`\) |
| `ContentDurationSec` | `real` | Duration of the suspicious content segment in seconds |
| `Detections` | `dynamic` | Detailed results from each detection model; each entry includes model name, content type analyzed, detection tasks, time segment, and confidence score |
| `PrimaryModelTasks` | `string` | The primary types of synthetic media detected |

## Correlate detections with call activities

Join the `SourceId` column in `SyntheticMediaDetectionEvents` with the `CallId` column in the [CallActivityEvents](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-callactivityevents-table) table to view activities recorded for the same Microsoft Teams call or meeting.

The following query returns up to 500 matching detection and activity records, starting with the most recent call activities. The `inner` join returns only records with matching call IDs and preserves multiple detections and activities for the same call.

```kusto
CallActivityEvents
| join kind=inner (
    SyntheticMediaDetectionEvents
    | where isnotempty(SourceId)
) on $left.CallId == $right.SourceId
| project DetectionTimestamp = Timestamp, DetectionId, Severity,
    DetectedUserDisplayName, CallId, ActivityTimestamp, ActivityType,
    ActivityInitiatorDisplayName
| order by ActivityTimestamp desc
| take 500
```

## Related topics

- [Advanced hunting overview](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-overview)
- [Learn the query language](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-query-language)
- [Understand the schema](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-schema-tables)
- [Apply query best practices](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-best-practices)

Tip

Do you want to learn more? Engage with the Microsoft Security community in our Tech Community: [Microsoft Defender XDR Tech Community](https://techcommunity.microsoft.com/t5/microsoft-365-defender/bd-p/MicrosoftThreatProtection).
