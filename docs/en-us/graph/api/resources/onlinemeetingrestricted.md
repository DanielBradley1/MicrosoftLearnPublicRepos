<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/onlinemeetingrestricted?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-12-03 -->

# onlineMeetingRestricted resource type

Namespace: microsoft.graph

Indicates the reason or reasons media content from a participant is restricted.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| contentSharingDisabled | [onlineMeetingContentSharingDisabledReason](#onlinemeetingcontentsharingdisabledreason-values) | Specifies the reason shared content from this participant is disabled. The possible values are: `watermarkProtection`, `unknownFutureValue`. |
| videoDisabled | [onlineMeetingVideoDisabledReason](#onlinemeetingvideodisabledreason-values) | Specifies the reason video from this participant is disabled. The possible values are: `watermarkProtection`, `unknownFutureValue`. |

### onlineMeetingContentSharingDisabledReason values

| Value | Description |
| :--- | :--- |
| watermarkProtection | The meeting content is marked *watermarked* but the user joined from an unsupported client. |
| unknownFutureValue | Evolvable enumeration sentinel value. Do not use. |

### onlineMeetingVideoDisabledReason values

| Value | Description |
| :--- | :--- |
| watermarkProtection | The meeting content is marked *watermarked* but the user joined from an unsupported client. |
| unknownFutureValue | Evolvable enumeration sentinel value. Do not use. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "contentSharingDisabled": {"@odata.type": "microsoft.graph.onlineMeetingContentSharingDisabledReason"},
  "videoDisabled": {"@odata.type": "microsoft.graph.onlineMeetingVideoDisabledReason"}
}
```
